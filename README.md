# 🏦 Bank Loan Approval Prediction System

An end-to-end Machine Learning pipeline designed to automate and predict bank loan eligibility based on customer demographic, financial, and credit history details.

---

## 📋 Table of Contents
1. [Project Overview](#-project-overview)
2. [Problem Statement](#-problem-statement)
3. [Data Pipeline & Preprocessing](#-data-pipeline--preprocessing)
4. [Model Architecture & Selection](#-model-architecture--selection)
5. [Results & Evaluation Metrics](#-results--evaluation-metrics)
6. [Tech Stack](#-tech-stack)

---

## 🌟 Project Overview
Financial institutions process thousands of loan applications daily. Manual reviews are time-consuming and prone to human error. This project implements a classification model to predict whether an applicant's loan should be approved or rejected, helping banks streamline decision-making and reduce risk.

---

## 🎯 Problem Statement
To build a robust predictive model that determines loan approval (`Loan_Status`) based on key applicant features including:
*   **Demographics:** Gender, Marital Status, Dependents, Education, Self-Employment status.
*   **Financials:** Applicant Income, Coapplicant Income, Loan Amount, Loan Amount Term.
*   **History & Location:** Credit History, Property Area (Urban, Semiurban, Rural).

---

## 🛠️ Data Pipeline Steps
The data preprocessing and cleaning pipeline handles raw inputs through the following systematic steps:
*   **Missing Value Imputation:** 
    *   Categorical columns filled using the **mode** (most frequent value).
    *   Numerical columns filled using the **median** to prevent skewness from outliers.
*   **Feature Encoding:** 
    *   Binary mapping applied to columns like `Gender`, `Married`, `Education`, `Self_Employed`, and `Loan_Status`.
    *   Ordinal cleaning for the `Dependents` feature (converting `'3+'` to numeric format).
*   **One-Hot Encoding:** Applied to multi-category features such as `Property_Area` to avoid ordinal assumptions.
*   **Feature Dropping:** Unique identifiers like `Loan_ID` removed prior to training.

---

## 🤖 Model Selection
*   **Algorithm:** Random Forest Classifier ($n\_estimators=100$)
*   **Rationale:** Chosen for its superior handling of mixed data types (numerical and categorical), robustness against overfitting via ensemble bagging, and built-in feature importance evaluation.

---

## 📊 Results & Metrics
The model was evaluated on an 80-20 train-test split, yielding strong overall performance:

| Metric | Class 0 (Rejected) | Class 1 (Approved) | Total / Average |
| :--- | :---: | :---: | :---: |
| **Precision** | 0.77 | 0.84 | 0.82 (Weighted) |
| **Recall** | 0.61 | 0.92 | 0.82 (Weighted) |
| **F1-Score** | 0.68 | 0.88 | 0.81 (Weighted) |
| **Accuracy** | — | — | **82.11%** |

### Confusion Matrix Highlights:
*   **True Positives (Approved Correctly):** High recall ($\mathbf{0.92}$) ensures the model reliably captures qualified candidates.
*   **Visualization:** A visual heatmap of the Confusion Matrix is generated within the Google Colab pipeline to track true vs. false predictions.

---

## 💻 Tech Stack
*   **Language:** Python 3.x
*   **Environment:** Google Colab
*   **Libraries:** Pandas, NumPy, Scikit-Learn, Seaborn, Matplotlib
