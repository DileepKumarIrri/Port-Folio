

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

### Step 1: Calculate the Entropy of the Entire Dataset

The formula for entropy \(H(S)\) is:

$\[
H(S) = - \sum_{i=1}^{c} p_i \log_2(p_i)
\]
$
Here, \(p_i\) is the proportion of instances belonging to class \(i\) in the dataset, and \(c\) is the number of classes.

- Number of instances where `PlayTennis` is `Yes` = 9
- Number of instances where `PlayTennis` is `No` = 5

The total number of instances is 14. Therefore, the entropy is:

$\[
H(S) = -\left(\frac{9}{14}\right)\log_2\left(\frac{9}{14}\right) - \left(\frac{5}{14}\right)\log_2\left(\frac{5}{14}\right)
\]

\[
H(S) = -\left(\frac{9}{14}\right)\log_2\left(0.6429\right) - \left(\frac{5}{14}\right)\log_2\left(0.3571\right)
\]

\[
H(S) = -(0.6429 \times -0.6439) - (0.3571 \times -1.4855) = 0.940
\]
$
### Step 2: Calculate the Information Gain for Each Attribute

#### 1. **Information Gain for "Outlook"**

**Splitting based on "Outlook":**

- **Outlook = Sunny**: {D1, D2, D8, D9, D11} → [No, No, No, Yes, Yes]
- **Outlook = Overcast**: {D3, D7, D12, D13} → [Yes, Yes, Yes, Yes]
- **Outlook = Rain**: {D4, D5, D6, D10, D14} → [Yes, Yes, No, Yes, No]

Now, we calculate the entropy for each subset:
$
1. **Sunny**:
   - \(H(Sunny)\) = \(-\left(\frac{3}{5}\right)\log_2\left(\frac{3}{5}\right) - \left(\frac{2}{5}\right)\log_2\left(\frac{2}{5}\right) = 0.971\)
2. **Overcast**:
   - \(H(Overcast)\) = \(-\left(\frac{4}{4}\right)\log_2\left(\frac{4}{4}\right) = 0\) (since all outcomes are the same, entropy is 0)
3. **Rain**:
   - \(H(Rain)\) = \(-\left(\frac{3}{5}\right)\log_2\left(\frac{3}{5}\right) - \left(\frac{2}{5}\right)\log_2\left(\frac{2}{5}\right) = 0.971\)
$
Now, calculate the weighted sum of the entropies (which is the expected entropy after splitting):
$
\[
\text{Weighted Entropy (Outlook)} = \left(\frac{5}{14} \times 0.971\right) + \left(\frac{4}{14} \times 0\right) + \left(\frac{5}{14} \times 0.971\right) = 0.693
\]
$
Finally, the Information Gain for "Outlook" is:
$
\[
\text{IG}(S, \text{Outlook}) = H(S) - \text{Weighted Entropy (Outlook)} = 0.940 - 0.693 = 0.247
\]
$
#### 2. **Information Gain for "Temperature"**

**Splitting based on "Temperature":**

- **Hot**: {D1, D2, D3, D13} → [No, No, Yes, Yes]
- **Mild**: {D4, D8, D10, D11, D12, D14} → [Yes, No, Yes, Yes, Yes, No]
- **Cool**: {D5, D6, D7, D9} → [Yes, No, Yes, Yes]

Calculate the entropy for each subset:
$
1. **Hot**:
   - \(H(Hot)\) = \(-\left(\frac{2}{4}\right)\log_2\left(\frac{2}{4}\right) - \left(\frac{2}{4}\right)\log_2\left(\frac{2}{4}\right) = 1.0\)
2. **Mild**:
   - \(H(Mild)\) = \(-\left(\frac{4}{6}\right)\log_2\left(\frac{4}{6}\right) - \left(\frac{2}{6}\right)\log_2\left(\frac{2}{6}\right) = 0.918\)
3. **Cool**:
   - \(H(Cool)\) = \(-\left(\frac{3}{4}\right)\log_2\left(\frac{3}{4}\right) - \left(\frac{1}{4}\right)\log_2\left(\frac{1}{4}\right) = 0.811\)
$
Now, calculate the weighted sum of the entropies:
$
\[
\text{Weighted Entropy (Temperature)} = \left(\frac{4}{14} \times 1.0\right) + \left(\frac{6}{14} \times 0.918\right) + \left(\frac{4}{14} \times 0.811\right) = 0.911
\]

Finally, the Information Gain for "Temperature" is:

\[
\text{IG}(S, \text{Temperature}) = 0.940 - 0.911 = 0.029
\]
$
#### 3. **Information Gain for "Humidity"**

**Splitting based on "Humidity":**

- **High**: {D1, D2, D3, D4, D8, D12, D14} → [No, No, Yes, Yes, No, Yes, No]
- **Normal**: {D5, D6, D7, D9, D10, D11, D13} → [Yes, No, Yes, Yes, Yes, Yes, Yes]

Calculate the entropy for each subset:
$
1. **High**:
   - \(H(High)\) = \(-\left(\frac{3}{7}\right)\log_2\left(\frac{3}{7}\right) - \left(\frac{4}{7}\right)\log_2\left(\frac{4}{7}\right) = 0.985\)
2. **Normal**:
   - \(H(Normal)\) = \(-\left(\frac{6}{7}\right)\log_2\left(\frac{6}{7}\right) - \left(\frac{1}{7}\right)\log_2\left(\frac{1}{7}\right) = 0.592\)
$
Now, calculate the weighted sum of the entropies:
$
\[
\text{Weighted Entropy (Humidity)} = \left(\frac{7}{14} \times 0.985\right) + \left(\frac{7}{14} \times 0.592\right) = 0.789
\]

Finally, the Information Gain for "Humidity" is:

\[
\text{IG}(S, \text{Humidity}) = 0.940 - 0.789 = 0.151
\]
$


#### 4. **Information Gain for "Wind"**

**Splitting based on "Wind":**

- **Weak**: {D1, D3, D4, D5, D8, D9, D10} → [No, Yes, Yes, Yes, No, Yes, Yes]
- **Strong**: {D2, D6, D7, D11, D12, D13, D14} → [No, No, Yes, Yes, Yes, Yes, No]

Calculate the entropy for each subset:
$
1. **Weak**:
   - \(H(Weak)\) = \(-\left(\frac{2}{7}\right)\log_2\left(\frac{2}{7}\right) - \left(\frac{5}{7}\right)\log_2\left(\frac{5}{7}\right) = 0.863\)
2. **Strong**:
   - \(H(Strong)\) = \(-\left(\frac{4}{7}\right)\log_2\left(\frac{4}{7}\right) - \left(\frac{3}{7}\right)\log_2\left(\frac{3}{7}\right) = 0.985\)

Now, calculate the weighted sum of the entropies:

\[
\text{Weighted Entropy (Wind)} = \left(\frac{7}{14} \times 0.863\right) + \left(\frac{7}{14} \times 0.985\right) = 0.924
\]

Finally, the Information Gain for "Wind" is:

\[
\text{IG}(S, \text{Wind}) = 0.940 - 0.924 = 0.016
\]
$
### Step 3: Selecting the Best Attribute

The Information Gains for the attributes are:

- **Outlook**: 0.247
- **Temperature**: 0.029
- **Humidity**: 0.151
- **Wind**: 0.016

The highest Information Gain is for **Outlook**, so **Outlook** will be the root of the decision tree.

### Step 4: Recursively Build the Tree

1. **Root Node**: **Outlook**

   - If **Outlook = Sunny**:
     - Subset: {D1, D2, D8, D9, D11} → [No, No, No, Yes, Yes]
     - Repeat the process on this subset to determine the best attribute for this branch.
   - If **Outlook = Overcast**:
     - Subset: {D3, D7, D12, D13} → [Yes, Yes, Yes, Yes]
     - Since all outcomes are `Yes`, this becomes a leaf node with the classification `Yes`.
   - If **Outlook = Rain**:
     - Subset: {D4, D5, D6, D10, D14} → [Yes, Yes, No, Yes, No]
     - Repeat the process on this subset to determine the best attribute for this branch.

### Building the Subtree for **Outlook = Sunny**

For the subset where **Outlook = Sunny**: {D1, D2, D8, D9, D11} → [No, No, No, Yes, Yes]

#### Step 1: Calculate Entropy for Subset

- Number of `Yes` = 2
- Number of `No` = 3

Entropy:
$
\[
H(S) = -\left(\frac{2}{5}\right)\log_2\left(\frac{2}{5}\right) - \left(\frac{3}{5}\right)\log_2\left(\frac{3}{5}\right) = 0.971
\]$

#### Step 2: Calculate Information Gain for Each Attribute in Subset

- **Temperature**:
  - Subsets: {Hot, Mild, Cool}
  - Calculate entropy and weighted entropy as before.
- **Humidity**:
  - Subsets: {High, Normal}
  - Calculate entropy and weighted entropy as before.
- **Wind**:
  - Subsets: {Weak, Strong}
  - Calculate entropy and weighted entropy as before.

Let's say the best attribute for this subset turns out to be **Humidity** (we won't go through all the calculations again here for brevity). You would then split this node further based on the attribute "Humidity".

### Continue Recursively

You continue this process recursively, selecting the best attribute at each step until you reach subsets that are pure (i.e., all instances belong to a single class). Each time a subset is pure, it becomes a leaf node in the decision tree with the classification `Yes` or `No`.

### Final Decision Tree

Based on the above calculations and hypothetical splits:

```
Outlook
├── Sunny
│   ├── Humidity
│   │   ├── High: No
│   │   └── Normal: Yes
├── Overcast: Yes
└── Rain
    ├── Wind
    │   ├── Weak: Yes
    │   └── Strong: No
```

This tree is a simplified version and is hypothetical after the first few calculations. Each node represents a decision point based on an attribute, and each branch represents the possible values for that attribute.

If you need to see the calculations for the remaining splits or if there's any specific part you'd like to dig deeper into, let me know!