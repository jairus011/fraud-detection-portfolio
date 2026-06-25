# Fraud Detection Project Findings

## Notebook 1: Data Understanding

### Dataset overview
- The raw dataset contains **284,807 transactions** and **31 columns**.
- The features include `Time`, `Amount`, anonymized variables `V1` to `V28`, and the target variable `Class`.

### Fraud class imbalance in raw data
- Non-fraud transactions: **284,315**
- Fraud transactions: **492**
- Fraud rate: **~0.17%**

This confirms that the fraud detection task is a **severely imbalanced classification problem**.

### Data quality observations from raw data
- Missing values: **0**
- Duplicate rows: **1,081**

### Transaction amount observations
- Average transaction amount overall: **88.35**
- Fraud mean amount: **122.21**
- Non-fraud mean amount: **88.29**

Transaction amounts are highly skewed. Fraudulent transactions show a higher average amount than legitimate transactions, but fraud does not appear to follow a single simple amount pattern.

---

## Notebook 2: Cleaning and Preprocessing

### Duplicate handling
- Duplicate rows removed: **1,081**
- Shape after duplicate removal: **283,726 rows, 31 columns**

### Class distribution after duplicate removal
- Non-fraud transactions: **283,253**
- Fraud transactions: **473**

This shows that duplicate removal affected both legitimate and fraudulent transactions, slightly changing the final class distribution used for modeling.

### Train-test split
The cleaned dataset was split into training and testing sets using an 80/20 split with stratification.

- **X_train:** 226,980 rows × 30 columns
- **X_test:** 56,746 rows × 30 columns
- **y_train:** 226,980 rows
- **y_test:** 56,746 rows

### Class balance after train-test split
Training set:
- Non-fraud: **226,602**
- Fraud: **378**

Testing set:
- Non-fraud: **56,651**
- Fraud: **95**

The fraud proportion was preserved across train and test sets using stratified sampling.

### Scaling
`Time` and `Amount` were scaled using `StandardScaler`, while PCA-based variables `V1` to `V28` were left unchanged.

---

## Notebook 3: Baseline Modeling

### Models trained
- Logistic Regression
- Random Forest Classifier

### Logistic Regression results
Fraud-class performance:
- Precision: **0.85**
- Recall: **0.59**
- F1-score: **0.70**
- ROC-AUC: **0.9563**

Confusion matrix:
- True Negatives: **56,641**
- False Positives: **10**
- False Negatives: **39**
- True Positives: **56**

### Random Forest results
Fraud-class performance:
- Precision: **0.97**
- Recall: **0.73**
- F1-score: **0.83**
- ROC-AUC: **0.9239**

Confusion matrix:
- True Negatives: **56,649**
- False Positives: **2**
- False Negatives: **26**
- True Positives: **69**

### Baseline conclusion
Random Forest performed better than Logistic Regression for fraud detection in this project. It identified more fraud cases, produced fewer false positives, and achieved a stronger fraud-class F1-score. Although Logistic Regression had a higher ROC-AUC, Random Forest produced better classification results at the default prediction threshold and is the stronger baseline model for this project.