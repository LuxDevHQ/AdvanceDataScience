# Credit Risk Prediction Project

# Overview

This project focuses on building a machine learning system that predicts whether a customer will default on a loan.

The dataset contains customer, loan, lender, and economic indicator information from Kenya. The goal is to use this information to develop a predictive model capable of identifying high-risk borrowers.

Some customers may appear multiple times in the dataset, and a single loan may also appear with different lenders. This means that some loans are funded by multiple lenders.

Additional macroeconomic indicators from the FRED (Federal Reserve Economic Data) portal are also provided to enrich the dataset.

---

# Problem Statement

Financial institutions face significant losses when customers fail to repay loans. Traditional credit scoring methods may not fully capture customer behaviour and economic conditions.

The challenge is to build a machine learning model that can accurately predict loan default risk using historical loan, customer, and economic data.

---

# Objectives

The project objectives are to:

* Understand the structure of the dataset
* Explore relationships between features and loan default behaviour
* Clean and preprocess the data
* Engineer useful features
* Build and evaluate machine learning classification models
* Compare model performance
* Save the best-performing model
* Deploy the model using Flask or FastAPI

---

# Type of Machine Learning Problem

This is a:

## Supervised Machine Learning Problem

More specifically:

## Binary Classification

| Target Value | Meaning                        |
| ------------ | ------------------------------ |
| 0            | Customer repaid the loan       |
| 1            | Customer defaulted on the loan |

---

# Dataset Features

| Feature                       | Description                                          | Example Values         |
| ----------------------------- | ---------------------------------------------------- | ---------------------- |
| `ID`                          | Unique identifier for each dataset row               | `ID_001245`            |
| `customer_id`                 | Unique customer identifier                           | `CUS_1452`             |
| `country_id`                  | Country code or identifier                           | `KEN`                  |
| `tbl_loan_id`                 | Unique loan identifier                               | `LN_98451`             |
| `Total_Amount`                | Total loan amount disbursed                          | `15000`                |
| `Total_Amount_to_Repay`       | Total expected repayment amount                      | `18000`                |
| `loan_type`                   | Type/category of loan                                | `Personal`, `Business` |
| `disbursement_date`           | Date loan was issued                                 | `2024-01-15`           |
| `duration`                    | Loan duration in days                                | `30`, `90`, `180`      |
| `lender_id`                   | Identifier of lender                                 | `LEND_004`             |
| `New_versus_Repeat`           | Indicates whether customer is new or repeat borrower | `New`, `Repeat`        |
| `Amount_Funded_By_Lender`     | Amount funded by lender                              | `5000`                 |
| `Lender_portion_Funded`       | Percentage funded by lender                          | `0.35`                 |
| `due_date`                    | Loan repayment due date                              | `2024-03-15`           |
| `Lender_portion_to_be_repaid` | Amount lender expects to recover                     | `6200`                 |
| `target`                      | Default indicator                                    | `0`, `1`               |

---

# Economic Indicators (FRED)

Additional economic indicators are provided in a separate CSV file.

| Indicator           | Description                    |
| ------------------- | ------------------------------ |
| `FP.CPI.TOTL.ZG`    | Inflation rate                 |
| `PA.NUS.FCRF`       | Exchange rate                  |
| `FR.INR.RINR`       | Real interest rate             |
| `AG.LND.PRCP.MM`    | Average precipitation          |
| `FR.INR.DPST`       | Deposit interest rate          |
| `FP.INR.LEND`       | Lending interest rate          |
| `FR.INR.LNDP`       | Interest rate spread           |
| `EG.USE.COMM.FO.ZS` | Fossil fuel energy consumption |
| `SL.UEM.TOTL.ZS`    | Unemployment rate              |

---

# Expected Folder Structure

```text
credit-risk-project/
│
├── data/
│   ├── raw/
│   ├── processed/
│
├── notebooks/
│   ├── 01_data_loading.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_eda.ipynb
│   ├── 04_feature_engineering.ipynb
│   ├── 05_model_training.ipynb
│   └── 06_model_evaluation.ipynb
│
├── models/
│   ├── best_model.pkl
│   └── pipeline.pkl
│
├── app/
│   ├── main.py
│   ├── templates/
│   └── static/
│
├── src/
│   ├── preprocessing.py
│   ├── training.py
│   ├── prediction.py
│   └── utils.py
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

# Recommended Workflow

---

# 1. Environment Setup

## Create Virtual Environment

### Windows

```bash
python -m venv venv

venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv

source venv/bin/activate
```

---

# 2. Data Loading

Possible tasks:

* Read datasets
* Inspect dataset shape
* Check data types
* Explore missing values
* Understand target distribution

---

# 3. Data Cleaning

Possible areas to investigate:

* Missing values
* Duplicate records
* Incorrect data types
* Date formatting
* Outliers

Hints:

* Consider dropping or imputing missing values where applicable
* Convert date columns into datetime format
* Check for duplicate entries

---

# 4. Exploratory Data Analysis (EDA)

Explore the structure and patterns within the dataset.

Possible analysis areas:

## Univariate Analysis

* Distribution of loan amounts
* Loan duration patterns
* Target imbalance

## Bivariate Analysis

* Loan type vs target
* Repeat customers vs target
* Loan amount vs target

## Multivariate Analysis

* Feature relationships
* Correlation analysis
* Grouped statistics

Possible visualizations:

* Histograms
* Boxplots
* Countplots
* Heatmaps
* Scatterplots

---

# 5. Correlation & Relationship Analysis

Investigate relationships between features and the target variable.

Possible approaches:

## Numerical Features vs Target

* Correlation matrix
* Point-biserial correlation
* Feature importance analysis

## Categorical Features vs Target

Possible methods:

* Chi-square test
* Crosstab analysis
* Grouped target distributions

Examples:

* `loan_type` vs `target`
* `New_versus_Repeat` vs `target`

Also investigate:

* Multicollinearity between numerical features
* Highly correlated variables
* Redundant features

---

# 6. Feature Engineering

Possible feature engineering ideas:

## Date-Based Features

* Loan month
* Loan year
* Loan duration categories

## Financial Features

Examples:

```python
interest_amount = Total_Amount_to_Repay - Total_Amount
```

```python
repayment_ratio = Total_Amount_to_Repay / Total_Amount
```

## Customer-Based Features

* Loan frequency
* Previous borrowing patterns
* Aggregated customer statistics

---

# 7. Data Preprocessing

Possible preprocessing steps:

* Feature encoding
* Scaling numerical features
* Handling categorical variables
* Building preprocessing pipelines

Suggested tools:

* Scikit-learn Pipelines
* ColumnTransformer

---

# 8. Model Training

Possible models to explore:

* Logistic Regression
* Decision Trees
* Random Forest
* XGBoost
* LightGBM
* CatBoost

Possible evaluation metrics:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC

---

# 9. Model Saving

Save the best-performing model and preprocessing pipeline.

Example:

```python
import joblib

joblib.dump(model, "models/best_model.pkl")
```

---

# 10. Model Deployment

The final model can be deployed using:

* Flask
* FastAPI

Possible deployment workflow:

1. Receive user input
2. Apply preprocessing pipeline
3. Generate prediction
4. Return prediction result

---

# Expected Deliverables

Students are expected to submit:

* Clean notebooks
* Trained machine learning model
* Saved preprocessing pipeline
* Deployment application
* Documentation (`README.md`)
* Source code files

---

# Suggested Libraries

```txt
pandas
numpy
matplotlib
seaborn
scikit-learn
xgboost
lightgbm
catboost
flask
fastapi
joblib
jupyter
```

---

# Conclusion

This project provides an end-to-end machine learning workflow for credit risk prediction. Students are expected to explore the dataset, engineer useful features, build classification models, evaluate performance, and deploy a working prediction system.
