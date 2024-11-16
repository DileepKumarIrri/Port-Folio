---
title: "Trees Classifiers Overview"
categories:
  - computing
tags:
  - mathjax
  - jekyll
use_math: true
published: true
---

Let's dive deeper into each decision tree algorithm—ID3, C4.5, and CART—focusing on how they work, their strengths and weaknesses, and how they compare to one another.

### Example Dataset Recap

| Day  | Outlook  | Temperature | Humidity | Wind   | PlayTennis |
|------|----------|-------------|----------|--------|------------|
| D1   | Sunny    | Hot         | High     | Weak   | No         |
| D2   | Sunny    | Hot         | High     | Strong | No         |
| D3   | Overcast | Hot         | High     | Weak   | Yes        |
| D4   | Rain     | Mild        | High     | Weak   | Yes        |
| D5   | Rain     | Cool        | Normal   | Weak   | Yes        |
| D6   | Rain     | Cool        | Normal   | Strong | No         |
| D7   | Overcast | Cool        | Normal   | Strong | Yes        |
| D8   | Sunny    | Mild        | High     | Weak   | No         |
| D9   | Sunny    | Cool        | Normal   | Weak   | Yes        |
| D10  | Rain     | Mild        | Normal   | Weak   | Yes        |
| D11  | Sunny    | Mild        | Normal   | Strong | Yes        |
| D12  | Overcast | Mild        | High     | Strong | Yes        |
| D13  | Overcast | Hot         | Normal   | Weak   | Yes        |
| D14  | Rain     | Mild        | High     | Strong | No         |

### 1. **ID3 (Iterative Dichotomiser 3)**

#### How It Works

- **Entropy**: ID3 uses entropy to measure the impurity or uncertainty in the dataset. Entropy \(H(S)\) for a set \(S\) is calculated as:
  $\[
  H(S) = -\sum_{i=1}^{c} p_i \log_2(p_i)
  \]$
  where \(p_i\) is the proportion of instances of class \(i\) in set \(S\), and \(c\) is the number of classes.

- **Information Gain**: ID3 selects the attribute that maximizes the reduction in entropy, known as Information Gain (IG):
  $\[
  \text{IG}(S, A) = H(S) - \sum_{v \in \text{Values}(A)} \frac{|S_v|}{|S|} H(S_v)
  \]$
  Here, \(S_v\) is the subset of \(S\) where attribute \(A\) has value \(v\).

- **Tree Construction**: The attribute with the highest IG is chosen as the root or an internal node, and the process is repeated recursively.

#### Example with "Outlook" Attribute

For "Outlook":

- **Entropy of the dataset**:
  $\[
  H(S) = -\left(\frac{9}{14}\right)\log_2\left(\frac{9}{14}\right) - \left(\frac{5}{14}\right)\log_2\left(\frac{5}{14}\right) \approx 0.94
  \]$

- **Information Gain for "Outlook"**:
  $\[
  \text{IG}(S, \text{Outlook}) = 0.94 - \left(\frac{5}{14} \times 0.971 + \frac{4}{14} \times 0 + \frac{5}{14} \times 0.971\right) \approx 0.246
  \]$
  Since "Outlook" has the highest IG, it's chosen as the root node.

#### Strengths and Weaknesses

- **Strengths**:
  - Simple and easy to understand.
  - Good for datasets with categorical attributes.

- **Weaknesses**:
  - **Bias towards attributes with many values**: ID3 can be biased towards attributes with many possible values because it doesn't account for the number of splits.
  - **Overfitting**: Without pruning, ID3 can create overly complex trees that overfit the training data.
  - **Cannot handle numeric data directly**: ID3 requires discretization of numeric attributes.

### 2. **C4.5**

#### How It Works

C4.5 builds on ID3 by addressing its limitations and introducing several improvements:

- **Handling Numeric Attributes**: C4.5 can handle both categorical and continuous attributes. For continuous attributes, C4.5 calculates a threshold (split point) to divide the data into two subsets.

- **Gain Ratio**: Instead of just using Information Gain, C4.5 uses Gain Ratio to select the best attribute. Gain Ratio is the ratio of Information Gain to the Split Information, which penalizes attributes with many values:
  $\[
  \text{Gain Ratio}(A) = \frac{\text{IG}(S, A)}{\text{SplitInfo}(A)}
  \]$
  where
  $\[
  \text{SplitInfo}(A) = -\sum_{v \in \text{Values}(A)} \frac{|S_v|}{|S|} \log_2\left(\frac{|S_v|}{|S|}\right)
  \]$

- **Handling Missing Values**: C4.5 can handle missing attribute values by using fractional counts.

- **Pruning**: C4.5 includes a post-pruning step to reduce the size of the tree and avoid overfitting.

#### Example with "Outlook" Attribute

For "Outlook":

- **Information Gain**: Same as in ID3.

- **Split Information**:
  $\[
  \text{SplitInfo}(\text{Outlook}) = -\left(\frac{5}{14}\right)\log_2\left(\frac{5}{14}\right) - \left(\frac{4}{14}\right)\log_2\left(\frac{4}{14}\right) - \left(\frac{5}{14}\right)\log_2\left(\frac{5}{14}\right)
  \]$

- **Gain Ratio**:
  $\[
  \text{Gain Ratio}(\text{Outlook}) = \frac{\text{IG}(S, \text{Outlook})}{\text{SplitInfo}(\text{Outlook})}
  \]$
  C4.5 selects the attribute with the highest Gain Ratio, which may differ from the attribute selected by ID3.

#### Strengths and Weaknesses

- **Strengths**:
  - **Handles numeric attributes**: No need to discretize continuous data.
  - **Reduced bias**: Gain Ratio helps reduce the bias towards attributes with many values.
  - **Pruning**: Helps avoid overfitting by reducing tree complexity.

- **Weaknesses**:
  - **Computationally intensive**: Calculating Gain Ratio and handling continuous attributes increases computational complexity.
  - **Still prone to some biases**: Although reduced, biases towards attributes with many values can still occur.

### 3. **CART (Classification and Regression Trees)**

#### How It Works

CART differs from ID3 and C4.5 in several key ways:

- **Binary Splits**: CART produces strictly binary splits, meaning each node is split into exactly two branches, regardless of the number of values the attribute can take.

- **Gini Index (for classification)**: Instead of using Entropy, CART uses the Gini Index as a measure of impurity:
  $\[
  \text{Gini}(S) = 1 - \sum_{i=1}^{c} p_i^2
  \]$
  The Gini Index measures how often a randomly chosen element from the set would be incorrectly labeled.

- **Regression Trees**: For regression tasks, CART uses Least Squares Deviation as the splitting criterion.

- **Pruning**: CART uses cost-complexity pruning to avoid overfitting. This involves growing a large tree and then pruning it back to improve generalization.

#### Example with "Outlook" Attribute

For "Outlook":

- **Gini Index**:
  $\[
  \text{Gini}(S) = 1 - \left(\frac{9}{14}\right)^2 - \left(\frac{5}{14}\right)^2 \approx 0.459
  \]$
  The Gini Index is calculated for each possible split, and CART selects the split that minimizes the Gini Index in the resulting subsets.

- **Binary Split**:
  Unlike ID3 and C4.5, CART would create a binary split, e.g., "Outlook = Sunny" vs. "Outlook ≠ Sunny".

#### Strengths and Weaknesses

- **Strengths**:
  - **Binary Splits**: Simplicity and ease of interpretation due to binary nature.
  - **Versatility**: Can be used for both classification and regression tasks.
  - **Pruning**: Cost-complexity pruning helps control tree size and prevents overfitting.

- **Weaknesses**:
  - **Binary Splits**: Can lead to deeper trees compared to multi-way splits used in ID3 and C4.5.
  - **Gini Index Sensitivity**: Gini Index can sometimes be sensitive to small variations in data.


