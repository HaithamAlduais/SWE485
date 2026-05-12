# SW485-Project-Group#

## Group Members
- Munthir Almukhlif - 444101355
- Haitham Alduais - 444105932
- Mohammad Alfarraj - 443102025

## Group Information

| Student Name | Student ID | Responsibility |
|---|---:|---|
| Munthir Almukhif | 444101355 | Dataset loading and checking |
| Haitham Alduais | 444105932 | Summary and visualization |
| Mohammad Alfarraj | 443102025 | Preprocessing |

---

## Project Motivation

Medical insurance charges are not the same for every person. Age, BMI, smoking status, number of children, sex, and region can affect the final cost.

The idea of this project is to use machine learning to estimate the insurance cost-risk level for a user. Instead of only showing a predicted charge, the system gives a simple label:

- Low Cost Risk
- Medium Cost Risk
- High Cost Risk

This makes the result easier to understand as a simple advice system.

---

## Dataset

- Dataset name: Medical Cost Personal Dataset
- Source: https://www.kaggle.com/datasets/mirichoi0218/insurance?resource=download
- File used: `Dataset/insurance.csv`
- Rows: 1338
- Columns: 7
- Original target: `charges`
- Advice target created in the notebook: `risk_level`

### Columns

| Column | Type | Meaning |
|---|---|---|
| age | Numeric | Age of the beneficiary |
| sex | Categorical | Male or female |
| bmi | Numeric | Body Mass Index |
| children | Numeric | Number of children/dependents |
| smoker | Categorical | Whether the person is a smoker |
| region | Categorical | Residential region |
| charges | Numeric | Medical insurance charges |

---

## Phase 1

File: `Phase1_Data_Exploration.ipynb`

In Phase 1, we loaded the dataset and checked the basic information. We also checked missing values, duplicate rows, data types, and statistical summaries.

We created a new column called `risk_level` from `charges` so the project can work as an advice system.

Preprocessing used in Phase 1:

- Remove duplicate rows.
- Encode `sex` and `smoker` as 0 and 1.
- One-hot encode `region`.
- Standardize `age`, `bmi`, and `children`.
- Keep `charges` as the original numeric target.

Main finding: the dataset has no missing values, and smoking status, age, and BMI are important variables to study.

---

## Phase 2 - Supervised Learning

File: `Supervised_Learning/Phase2_Supervised_Learning.ipynb`

The supervised notebook predicts the `risk_level` advice class.

Models used:

- Logistic Regression
- Random Forest
- SVM

The models are compared using accuracy, precision, recall, F1-score, ROC-AUC, cross-validation, and confusion matrix.

F1 Macro is used to choose the best model because the target has three classes.

---

## Phase 2 - Unsupervised Learning

File: `Unsupervised_Learning/Phase2_Unsupervised_Learning.ipynb`

The unsupervised notebook uses K-Means clustering to group users into similar profiles.

The target label is removed before clustering. The clustering model uses only the user information columns.

Clustering is evaluated using:

- WCSS
- Silhouette Score
- BCubed Precision and Recall
- PCA visualization
- Cluster profile summary

The clusters can help explain different user profiles and support the advice system.

---

## Repository Structure

```text
SW485-Project-Group#/
│
├── README.md
├── requirements.txt
│
├── Dataset/
│   ├── insurance.csv
│   ├── insurance_preprocessed_phase1.csv
│   └── dataset_source.md
│
├── Phase1_Data_Exploration.ipynb
├── All_Phases_Combined.ipynb
│
├── Supervised_Learning/
│   └── Phase2_Supervised_Learning.ipynb
│
└── Unsupervised_Learning/
    └── Phase2_Unsupervised_Learning.ipynb
```

---

## How to Run

1. Open the project folder.
2. Make sure the dataset file is here: `Dataset/insurance.csv`.
3. Run `Phase1_Data_Exploration.ipynb`.
4. Run `Supervised_Learning/Phase2_Supervised_Learning.ipynb`.
5. Run `Unsupervised_Learning/Phase2_Unsupervised_Learning.ipynb`.

There is also `All_Phases_Combined.ipynb`, which contains Phase 1 and Phase 2 in one notebook.
