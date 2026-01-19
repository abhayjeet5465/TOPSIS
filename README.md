# TOPSIS Implementation in Python (Command Line Program)

## 1. Project Description

This project implements the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** method using Python.  
The program is designed as a **command-line application** that ranks multiple alternatives based on several criteria.

TOPSIS works on the principle that the best alternative should have the **shortest distance from the ideal best solution** and the **farthest distance from the ideal worst solution**.

The implementation supports:
- Any number of decision criteria
- User-defined weights and impacts
- CSV and Excel input files
- Proper input validation and error handling

---

## 2. How to Run the Program

### Command Format
```bash
python topsis.py <InputFile> <Weights> <Impacts> <OutputFile>

## Example
python topsis.py data.csv "1,1,1,2,1" "+,+,-,+,+" output-result.csv

3. Input File Format

The first column contains the names of alternatives (e.g., Fund Name)

Columns from second to last represent criteria values

All criteria columns must be numeric

Minimum of three columns is required

Sample Input Table
Fund	P1	P2	P3	P4	P5
M1	0.67	0.45	6.5	42.6	12.56
M2	0.60	0.36	3.6	53.3	14.47
4. Methodology

The TOPSIS algorithm follows the steps below:

Step 1: Decision Matrix

The criteria values (excluding the first column) form the decision matrix.

Step 2: Normalization

Each criterion is normalized using vector normalization:

r_ij = x_ij / sqrt(sum(x_ij^2))


This ensures all criteria are comparable.

Step 3: Weighted Normalized Matrix

Each normalized value is multiplied by its corresponding weight:

v_ij = r_ij × w_j

Step 4: Ideal Best and Ideal Worst Solutions

For benefit (+) criteria:

Ideal Best → maximum value

Ideal Worst → minimum value

For cost (-) criteria:

Ideal Best → minimum value

Ideal Worst → maximum value

Step 5: Distance Calculation

Euclidean distances from ideal best and ideal worst are calculated:

D+ = sqrt(sum((v_ij − v_j+)²))
D− = sqrt(sum((v_ij − v_j−)²))

Step 6: TOPSIS Score

The relative closeness to the ideal solution is computed as:

TOPSIS Score = D− / (D+ + D−)


A higher score indicates a better alternative.

Step 7: Ranking

Alternatives are ranked in descending order of TOPSIS score.

5. Output Format

The output file contains the original input data along with two additional columns:

Column Name	Description
Topsis Score	Relative closeness to the ideal solution
Rank	Final ranking (Rank 1 = best alternative)
Sample Output
Fund	P1	P2	P3	P4	P5	Topsis Score	Rank
M5	0.76	0.58	4.8	43.0	12.29	0.85	1
M1	0.67	0.45	6.5	42.6	12.56	0.73	2
6. Result Graph (Optional)

A bar graph can be plotted using the TOPSIS scores to visually compare the ranking of alternatives.
Higher bars represent better-performing alternatives.

7. Key Features

Fully command-line based implementation

Supports any number of criteria

Handles invalid inputs gracefully

Compatible with CSV and Excel files

Suitable for academic assignments and practical applications

8. Conclusion

This project demonstrates a complete and flexible implementation of the TOPSIS decision-making technique.
The program efficiently ranks alternatives by considering both the best and worst possible scenarios, making it suitable for real-world multi-criteria decision analysis problems.
