# Fraud Detection Project

## Project Overview

This project builds a machine learning pipeline for detecting fraudulent credit card transactions. The goal is to explore a highly imbalanced fraud dataset, prepare it for modeling, and compare baseline machine learning models for fraud detection performance.

The project is designed as a **portfolio-ready fraud analytics case study** demonstrating practical skills in:

* fraud data understanding
* preprocessing and duplicate handling
* train/test preparation
* baseline fraud modeling
* evaluation of imbalanced classification models

---

## Business Problem

Fraudulent financial transactions create direct financial losses for banks, fintechs, SACCOs, and digital lenders. Fraud detection systems must identify suspicious transactions early while minimizing false alarms that disrupt legitimate customers and overload fraud operations teams.

This project simulates a fraud analytics workflow by building a classification model that distinguishes between fraudulent and legitimate transactions.

---

## Dataset

The project uses the **Credit Card Fraud Detection** dataset containing anonymized transaction data.

### Raw dataset characteristics

* **Rows:** 284,807
* **Columns:** 31
* **Target variable:** `Class`

  * `0` = non-fraud
  * `1` = fraud
* Features include:

  * `Time`
  * `Amount`
  * anonymized PCA-based features `V1` to `V28`

### Fraud class imbalance in raw data

* Non-fraud transactions: **284,315**
* Fraud transactions: **492**
* Fraud rate: **~0.17%**

This makes the problem a **severely imbalanced binary classification task**.

---

## Project Objectives

The project aimed to:

1. Understand the structure and quality of the fraud dataset
2. Identify class imbalance and early fraud-related patterns
3. Clean and preprocess the data for machine learning
4. Train baseline fraud detection models
5. Evaluate model performance using fraud-relevant classification metrics
6. Identify a stronger baseline model for future improvement

---

## Project Structure

```text
01.Fraud_Detection_Project/
│
├── data/
│   ├── raw/
│   │   └── creditcard.csv
│   ├── processed/
│   │   ├── X_train.csv
│   │   ├── X_test.csv
│   │   ├── y_train.csv
│   │   └── y_test.csv
│   └── external/
│
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   ├── 02_cleaning_preprocessing.ipynb
│   └── 03_baseline_model.ipynb
│
├── src/
│   ├── data_preprocessing.py
│   ├── features.py
│   └── train_model.py
│
├── reports/
│   ├── figures/
│   └── findings.md
│
├── models/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Workflow Summary

### 1. Data Understanding

The first notebook focused on understanding the structure and quality of the raw dataset.

#### Key findings

* Dataset shape: **284,807 rows × 31 columns**
* Missing values: **0**
* Duplicate rows: **1,081**
* Fraud transactions: **492**
* Non-fraud transactions: **284,315**

#### Transaction amount observations

* Average transaction amount overall: **88.35**
* Fraud mean amount: **122.21**
* Non-fraud mean amount: **88.29**

Transaction amounts were highly skewed, and fraudulent transactions did not follow one simple amount pattern.

---

### 2. Cleaning and Preprocessing

The second notebook prepared the dataset for modeling.

#### Steps performed

* removed duplicate rows
* separated features and target
* created train/test split using stratification
* scaled `Time` and `Amount` using `StandardScaler`

#### Duplicate handling results

* Duplicate rows removed: **1,081**
* Shape after duplicate removal: **283,726 rows × 31 columns**

#### Class distribution after duplicate removal

* Non-fraud transactions: **283,253**
* Fraud transactions: **473**

#### Train-test split

* **X_train:** 226,980 rows × 30 columns
* **X_test:** 56,746 rows × 30 columns
* **y_train:** 226,980 rows
* **y_test:** 56,746 rows

#### Class balance after train-test split

**Training set**

* Non-fraud: **226,602**
* Fraud: **378**

**Testing set**

* Non-fraud: **56,651**
* Fraud: **95**

---

### 3. Baseline Modeling

Two baseline models were trained and compared:

* **Logistic Regression**
* **Random Forest Classifier**

Because the dataset is highly imbalanced, model performance was evaluated using:

* Precision
* Recall
* F1-score
* Confusion Matrix
* ROC-AUC

---

## Model Results

### Logistic Regression

#### Fraud-class performance (`Class = 1`)

* Precision: **0.85**
* Recall: **0.59**
* F1-score: **0.70**
* ROC-AUC: **0.9563**

#### Confusion Matrix

* True Negatives: **56,641**
* False Positives: **10**
* False Negatives: **39**
* True Positives: **56**

#### Interpretation

Logistic Regression performed reasonably well as a baseline model, but it missed a notable number of fraud cases, limiting its recall in a fraud detection setting.

---

### Random Forest

#### Fraud-class performance (`Class = 1`)

* Precision: **0.97**
* Recall: **0.73**
* F1-score: **0.83**
* ROC-AUC: **0.9239**

#### Confusion Matrix

* True Negatives: **56,649**
* False Positives: **2**
* False Negatives: **26**
* True Positives: **69**

#### Interpretation

Random Forest produced the stronger fraud detection baseline. It identified more fraud cases, produced fewer false positives, and achieved a stronger fraud-class F1-score than Logistic Regression.

---

## Final Conclusion

The project successfully built a baseline fraud detection workflow from raw transaction data to evaluated machine learning models.

### Main conclusions

1. The dataset is **severely imbalanced**, so accuracy alone is not a reliable performance measure.
2. Duplicate handling mattered because duplicate removal slightly changed the fraud class distribution.
3. Fraud transaction amounts do not follow one simple rule and require model-based detection rather than manual thresholding.
4. **Random Forest outperformed Logistic Regression** as the stronger baseline fraud model in this project.

---

## Tools and Libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Jupyter Notebook

---

## Future Improvements

Possible next steps for improving this project include:

* testing class-weighted models
* experimenting with threshold tuning
* trying imbalance-handling methods such as resampling
* comparing additional fraud detection algorithms
* adding feature importance analysis and model explainability

---

## How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repo-link>
cd 01.Fraud_Detection_Project
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Open Jupyter Notebook

```bash
jupyter notebook
```

### 4. Run notebooks in order

1. `01_data_understanding.ipynb`
2. `02_cleaning_preprocessing.ipynb`
3. `03_baseline_model.ipynb`

---

## Portfolio Value

This project demonstrates:

* end-to-end fraud analytics workflow
* handling of imbalanced classification problems
* preprocessing decisions backed by data inspection
* baseline machine learning comparison for fraud detection
* communication of fraud modeling results in a business-oriented format

It forms a strong foundation for future projects in:

* fraud analytics
* credit risk modeling
* banking analytics
* risk intelligence systems
