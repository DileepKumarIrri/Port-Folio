# Logistic Regression Example

Let's go through a detailed mathematical example of logistic regression, focusing on how the coefficients are updated using gradient descent. We'll use a simple example with just one input feature.

## Example Problem

Suppose we have a dataset with a single feature \( x \) and a binary outcome \( y \). We want to use logistic regression to predict whether \( y = 1 \) (positive class) or \( y = 0 \) (negative class) based on the value of \( x \).

Here’s the data:

| \( x \)  | \( y \) |
|----------|---------|
| 2.78     | 0       |
| 1.46     | 0       |
| 3.39     | 1       |
| 1.85     | 1       |

## Step 1: Initialize Coefficients

Start with initial guesses for the coefficients:

- \( b_0 = 0.0 \) (intercept)
- \( b_1 = 0.0 \) (coefficient for \( x \))

## Step 2: Logistic Regression Model

The logistic regression model for this example is:

\[
y_{\text{pred}} = \frac{1}{1 + e^{-(b_0 + b_1 \cdot x)}}
\]

## Step 3: Iterative Coefficient Updates

We'll go through one iteration of updating the coefficients using gradient descent. For simplicity, let's assume a learning rate \( \alpha = 0.3 \).

### For the first data point \((x_1 = 2.78, y_1 = 0)\):

1. **Calculate \( z \)**:
   
   \[
   z = b_0 + b_1 \cdot x_1 = 0.0 + 0.0 \cdot 2.78 = 0.0
   \]

2. **Calculate the predicted probability \( y_{\text{pred}} \)**:
   
   \[
   y_{\text{pred}} = \frac{1}{1 + e^{-0}} = 0.5
   \]

3. **Calculate the error**:
   
   \[
   \text{Error} = y_{\text{true}} - y_{\text{pred}} = 0 - 0.5 = -0.5
   \]

4. **Update the coefficients using gradient descent**:
   
   For \( b_0 \):
   
   \[
   b_0 = b_0 + \alpha \cdot \text{Error} \cdot y_{\text{pred}} \cdot (1 - y_{\text{pred}}) \cdot 1
   \]
   \[
   b_0 = 0.0 + 0.3 \cdot (-0.5) \cdot 0.5 \cdot (1 - 0.5) \cdot 1
   \]
   \[
   b_0 = 0.0 - 0.0375 = -0.0375
   \]

   For \( b_1 \):
   
   \[
   b_1 = b_1 + \alpha \cdot \text{Error} \cdot y_{\text{pred}} \cdot (1 - y_{\text{pred}}) \cdot x_1
   \]
   \[
   b_1 = 0.0 + 0.3 \cdot (-0.5) \cdot 0.5 \cdot (1 - 0.5) \cdot 2.78
   \]
   \[
   b_1 = 0.0 - 0.10425 = -0.10425
   \]

After processing the first data point, the updated coefficients are:
- \( b_0 = -0.0375 \)
- \( b_1 = -0.10425 \)

### For the second data point \((x_2 = 1.46, y_2 = 0)\):

1. **Calculate \( z \)**:
   
   \[
   z = b_0 + b_1 \cdot x_2 = -0.0375 + (-0.10425) \cdot 1.46 = -0.189705
   \]

2. **Calculate the predicted probability \( y_{\text{pred}} \)**:
   
   \[
   y_{\text{pred}} = \frac{1}{1 + e^{-(-0.189705)}} \approx \frac{1}{1 + 1.2089} \approx 0.4527
   \]

3. **Calculate the error**:
   
   \[
   \text{Error} = y_{\text{true}} - y_{\text{pred}} = 0 - 0.4527 \approx -0.4527
   \]

4. **Update the coefficients**:

   For \( b_0 \):
   
   \[
   b_0 = -0.0375 + 0.3 \cdot (-0.4527) \cdot 0.4527 \cdot (1 - 0.4527)
   \]
   \[
   b_0 = -0.0375 - 0.04475 = -0.08225
   \]

   For \( b_1 \):
   
   \[
   b_1 = -0.10425 + 0.3 \cdot (-0.4527) \cdot 0.4527 \cdot (1 - 0.4527) \cdot 1.46
   \]
   \[
   b_1 = -0.10425 - 0.09739 = -0.20164
   \]

After processing the second data point, the updated coefficients are:
- \( b_0 = -0.08225 \)
- \( b_1 = -0.20164 \)

## Step 4: Repeat for All Data Points

You would repeat the above process for all data points in the dataset, updating the coefficients after each point. The coefficients will gradually converge to values that minimize the prediction error across all data points.

## Step 5: Final Model

After multiple iterations over the entire dataset, the coefficients will stabilize. These final coefficients can then be used to make predictions on new data points.

## Conclusion

Logistic regression uses the logistic function to convert a linear combination of input features into a probability. By iteratively updating the coefficients through gradient descent, the model learns to predict binary outcomes. The example above demonstrates the core of how logistic regression works in practice, providing a step-by-step guide to the mathematical process behind it.
