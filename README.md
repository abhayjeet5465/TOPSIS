# TOPSIS Implementation in Python (Command Line Program)

## Project Overview

This project implements the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** method using Python. The application is developed as a **command-line program** that evaluates and ranks multiple alternatives based on multiple decision criteria.

The TOPSIS method is based on the principle that the best alternative should be **closest to the ideal best solution** and **farthest from the ideal worst solution**. This method is widely used in multi-criteria decision-making problems involving conflicting criteria.

The program supports:
- Any number of decision criteria
- User-defined weights and impacts
- Input files in CSV or Excel format
- Robust input validation and error handling

---

## Program Execution

### Command-Line Syntax
```bash
python topsis.py <InputFile> <Weights> <Impacts> <OutputFile>

```

###  Example Execution
```bash
python topsis.py data.csv "1,1,1,2,1" "+,+,-,+,+" output-result.csv
```
## Input File Specification
The first column must contain the names or identifiers of the alternatives.

All remaining columns represent criteria values.

Criteria columns must contain numeric values only.

The input file must contain at least three columns.

### Sample Input Data
| Fund | P1 | P2 | P3 | P4 | P5 |
|------|----|----|----|----|----|
| M1 | 0.67 | 0.45 | 6.5 | 42.6 | 12.56 |
| M2 | 0.60 | 0.36 | 3.6 | 53.3 | 14.47 |

## Methodology
The TOPSIS algorithm is executed through the following steps:

### Step 1: Construction of the Decision Matrix
The criteria values (excluding the first column) form the decision matrix.

### Step 2: Normalization
Each criterion is normalized using vector normalization to eliminate the effect of differing units:


     r_ij = x_ij / sqrt(∑ x_ij²)

### Step 3: Weighted Normalized Decision Matrix
The normalized values are multiplied by their respective weights:


    v_ij = r_ij × w_j
### Step 4: Determination of Ideal Solutions
#### Benefit (+) criteria

Ideal Best: maximum value

Ideal Worst: minimum value

#### Cost (-) criteria

Ideal Best: minimum value

Ideal Worst: maximum value

### Step 5: Distance Measures
The Euclidean distance of each alternative from the ideal best and ideal worst solutions is calculated:

    D+ = sqrt(∑ (v_ij − v_j+)²)
    D− = sqrt(∑ (v_ij − v_j−)²)
### Step 6: TOPSIS Score Calculation
The relative closeness to the ideal solution is computed as:

    TOPSIS Score = D− / (D+ + D−)
A higher score indicates a more preferable alternative.

### Step 7: Ranking of Alternatives
Alternatives are ranked in descending order of their TOPSIS scores.

#### Output Description
The output file contains the original input data along with two additional columns:

Topsis Score(	Relative closeness of the alternative to the ideal solution)
Rank	Final ranking (Rank 1 indicates the best alternative)

| Fund | P1 | P2 | P3 | P4 | P5 | Topsis Score | Rank |
|------|----|----|----|----|----|--------------|------|
| M2 | 0.76 | 0.58 | 4.8 | 43.0 | 12.29 | 0.85 | 1 |
| M1 | 0.67 | 0.45 | 6.5 | 42.6 | 12.56 | 0.73 | 2 |



### Key Features
Fully command-line based implementation

Supports any number of decision criteria

Robust error checking and input validation

Compatible with both CSV and Excel input files

### Conclusion
This project provides a complete and adaptable implementation of the TOPSIS method for multi-criteria decision analysis. By systematically evaluating alternatives against ideal best and ideal worst solutions, the program enables effective and rational ranking for complex decision-making scenarios.


