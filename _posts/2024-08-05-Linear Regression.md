---
title: "linear Example"
categories:
  - computing
tags:
  - mathjax
  - jekyll
use_math: true
published: true
---



### 1. **Linear Regression Example**

**Scenario:**  
Predicting a student's exam score (\( Y \)) based on the number of hours studied (\( X \)).

#### Steps Involved:

1. **Formulation of the Model:**

   <div>
   $$
   Y = b_0 + b_1X
   $$
   </div>

   Where:
   - \( Y \) = Predicted exam score
   - \( X \) = Hours studied
   - \( b_0 \) = Intercept (the score when \( X = 0 \))
   - \( b_1 \) = Slope (the rate of change in score per hour studied)

2. **Calculating the Slope (\( b_1 \)) and Intercept (\( b_0 \))**

   - **Slope Formula:**

     <div>
     $$
     b_1 = \frac{\sum{(X_i - \bar{X})(Y_i - \bar{Y})}}{\sum{(X_i - \bar{X})^2}}
     $$
     </div>

     Where:
     - \( X_i \) and \( Y_i \) are individual data points.
     - \( \bar{X} \) and \( \bar{Y} \) are the means of \( X \) and \( Y \) respectively.

   - **Intercept Formula:**

     <div>
     $$
     b_0 = \bar{Y} - b_1\bar{X}
     $$
     </div>

     Where:
     - \( \bar{X} \) is the mean of the independent variable (hours studied).
     - \( \bar{Y} \) is the mean of the dependent variable (exam scores).

   - **Calculation Example:**
     - Given data:

       | Hours Studied (X) | Exam Score (Y) |
       |-------------------|----------------|
       | 1                 | 50             |
       | 2                 | 55             |
       | 3                 | 65             |
       | 4                 | 70             |
       | 5                 | 75             |

     - Calculate means:

       <div>
       $$
       \bar{X} = \frac{1+2+3+4+5}{5} = 3, \quad \bar{Y} = \frac{50+55+65+70+75}{5} = 63
       $$
       </div>

     - Calculate \( b_1 \):

       <div>
       $$
       b_1 = \frac{(-2)(-13) + (-1)(-8) + (0)(2) + (1)(7) + (2)(12)}{4 + 1 + 0 + 1 + 4} = \frac{65}{10} = 6.5
       $$
       </div>

     - Calculate \( b_0 \):

       <div>
       $$
       b_0 = 63 - 6.5 \times 3 = 63 - 19.5 = 43.5
       $$
       </div>

     - **Regression Equation:**

       <div>
       $$
       Y = 43.5 + 6.5X
       $$
       </div>

3. **Interpretation:**
   - The slope \( b_1 = 6.5 \) means that each additional hour studied increases the exam score by 6.5 points.
   - The intercept \( b_0 = 43.5 \) means that if a student studies for 0 hours, the predicted score would be 43.5.

4. **Prediction Example:**
   - If a student studies for 4 hours:

     <div>
     $$
     Y = 43.5 + 6.5 \times 4 = 43.5 + 26 = 69.5
     $$
     </div>

   - The model predicts an exam score of 69.5.

---

### 2. **Multiple Linear Regression Example**

**Scenario:**  
Predicting exam scores based on hours studied (\( X_1 \)) and the number of practice tests taken (\( X_2 \)).

#### Steps Involved:

1. **Formulation of the Model:**

   <div>
   $$
    Y = b_0 + b_1X_1 + b_2X_2
    $$
   </div>

   Where:
   - \( Y \) = Predicted exam score
   - \( X_1 \) = Hours studied
   - \( X_2 \) = Number of practice tests
   - \( b_0 \) = Intercept
   - \( b_1 \) and \( b_2 \) = Coefficients for hours studied and practice tests, respectively

2. **Calculating Coefficients:**

   - **Using Normal Equations:**

    <div>
    $$
    \mathbf{b} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{Y}
    $$
     </div>

     Where:
     - \( \mathbf{X} \) is the matrix of input variables (including a column of 1s for \( b_0 \)).
     - \( \mathbf{Y} \) is the vector of outputs (exam scores).
     - \( \mathbf{b} \) is the vector of coefficients \([b_0, b_1, b_2]\).

   - **Calculation Example:**
     - Given data:

       | Hours Studied (X1) | Practice Tests (X2) | Exam Score (Y) |
       |--------------------|---------------------|----------------|
       | 1                  | 1                   | 50             |
       | 2                  | 2                   | 60             |
       | 3                  | 1                   | 65             |
       | 4                  | 3                   | 70             |
       | 5                  | 2                   | 75             |

     - Construct matrices \( \mathbf{X} \) and \( \mathbf{Y} \):

       <div>
       $$
       \mathbf{X} = \begin{pmatrix}
       1 & 1 & 1 \\
       1 & 2 & 2 \\
       1 & 3 & 1 \\
       1 & 4 & 3 \\
       1 & 5 & 2
       \end{pmatrix}, \quad \mathbf{Y} = \begin{pmatrix}
       50 \\
       60 \\
       65 \\
       70 \\
       75
       \end{pmatrix}
       $$
       </div>

     - Calculate \( \mathbf{b} \):

       <div>
       $$
       \mathbf{b} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{Y}
       $$
       </div>

     - Assume after calculations:

       <div>
       $$
       b_0 = 40, \quad b_1 = 5, \quad b_2 = 4
       $$
       </div>

3. **Interpretation:**
   - \( b_1 = 5 \) means that each additional hour studied increases the exam score by 5 points, holding the number of practice tests constant.
   - \( b_2 = 4 \) means that each additional practice test increases the exam score by 4 points, holding hours studied constant.
   - The intercept \( b_0 = 40 \) is the predicted score if a student does no studying and takes no practice tests.

4. **Prediction Example:**
   - If a student studies for 3 hours and takes 2 practice tests:

     <div>
     $$
     Y = 40 + 5 \times 3 + 4 \times 2 = 40 + 15 + 8 = 63
     $$
     </div>

   - The model predicts an exam score of 63.

---

This markdown format is clean, organized, and ensures that all mathematical terms are properly rendered.