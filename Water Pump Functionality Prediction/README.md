#  CHO4 & CH05 Internship Project - May 2026

**Water Pump Functionality Prediction**

> A supervised machine learning project to classify the operational condition of waterpoints across Tanzania.

---

## Table of Contents

1. [Problem Statement](#1-problem-statement)
2. [Dataset Overview](#2-dataset-overview)
3. [Type of ML Problem](#3-type-of-ml-problem)
4. [Project Folder Structure](#4-project-folder-structure)
5. [ML Workflow](#5-ml-workflow)
   - [5.1 Setting Up Your Environment](#51-setting-up-your-environment)
   - [5.2 Step 1 — Data Loading & Exploration](#52-step-1--data-loading--exploration)
   - [5.3 Step 2 — Data Cleaning & Feature Engineering](#53-step-2--data-cleaning--feature-engineering)
   - [5.4 Step 3 — EDA & Correlation Analysis](#54-step-3--eda--correlation-analysis)
   - [5.5 Step 4 — Sklearn Pipelines & ML Modelling](#55-step-4--sklearn-pipelines--ml-modelling)
   - [5.6 Step 5 — Model Evaluation & Saving](#56-step-5--model-evaluation--saving)
6. [Model Deployment with Flask](#6-model-deployment-with-flask)
7. [Notes & Hints](#7-notes--hints)
8. [Deliverables Checklist](#8-deliverables-checklist)

---

## 1. Problem Statement

Access to clean and functional water is a critical challenge across many parts of Tanzania. Thousands of waterpoints — wells, boreholes, communal standpipes, and more — have been installed across the country, but a significant number are either non-functional or in need of repair, leaving communities without reliable water access.

### Objective

Build a machine learning model that **predicts the operational condition of a waterpoint** given a set of features describing its location, management, water source, and technical setup. Accurate predictions can help the Tanzanian government and NGOs prioritise maintenance efforts and allocate resources more efficiently.

### Target Variable

The model must classify each waterpoint into one of three categories:

| Label | Description |
|---|---|
| `functional` | The waterpoint is operational and needs no repairs |
| `functional needs repair` | The waterpoint is operational but requires repairs |
| `non functional` | The waterpoint is not operational |

---

## 2. Dataset Overview

>  **Important Note on Dataset Files:** The dataset is split across **two separate files**:
> - **`train.csv`** — Contains all the input features for each waterpoint.
> - **`labels.csv`** — Contains the target column (`status_group`) for each waterpoint.
>
> Both files share a common **`id`** column. You must **merge/join** them on `id` as your very first step before any exploration or modelling.

### Feature Columns

| Column | Description | Example Value |
|---|---|---|
| `amount_tsh` | Total static head — amount of water available to the waterpoint | `300.0` |
| `date_recorded` | Date the row was entered into the system | `2013-02-26` |
| `funder` | Who funded the well | `Germany Republi` |
| `gps_height` | Altitude of the well | `1335` |
| `installer` | Organisation that installed the well | `CES` |
| `longitude` | GPS longitude coordinate | `37.2029845` |
| `latitude` | GPS latitude coordinate | `-3.22870286` |
| `wpt_name` | Name of the waterpoint (if available) | `Kwaa Hassan Ismail` |
| `num_private` | Usage unspecified — explore during EDA | `0` |
| `basin` | Geographic water basin | `Pangani` |
| `subvillage` | Geographic location at sub-village level | `Bwani` |
| `region` | Geographic location at region level | `Kilimanjaro` |
| `region_code` | Region encoded as a numeric code | `3` |
| `district_code` | District encoded as a numeric code | `5` |
| `lga` | Local Government Area | `Hai` |
| `ward` | Administrative ward | `Machame Uroki` |
| `population` | Population around the well | `25` |
| `public_meeting` | Whether a public meeting was held | `True` |
| `recorded_by` | Group that entered the data row | `GeoData Consultants Ltd` |
| `scheme_management` | Who operates the waterpoint | `Water Board` |
| `scheme_name` | Name of the operating scheme | `Uroki-Bomang'ombe water sup` |
| `permit` | Whether the waterpoint is permitted | `True` |
| `construction_year` | Year the waterpoint was constructed | `1995` |
| `extraction_type` | Kind of extraction mechanism used | `gravity` |
| `extraction_type_group` | Grouped extraction type | `gravity` |
| `extraction_type_class` | Extraction type class | `gravity` |
| `management` | How the waterpoint is managed | `water board` |
| `management_group` | Grouped management type | `user-group` |
| `payment` | What the water costs | `other` |
| `payment_type` | Type of payment | `other` |
| `water_quality` | Quality of the water | `soft` |
| `quality_group` | Grouped water quality | `good` |
| `quantity` | Quantity of water available | `enough` |
| `quantity_group` | Grouped quantity | `enough` |
| `source` | Source of the water | `spring` |
| `source_type` | Type of water source | `spring` |
| `source_class` | Class of water source | `groundwater` |
| `waterpoint_type` | Kind of waterpoint | `communal standpipe` |
| `waterpoint_type_group` | Grouped waterpoint type | `communal standpipe` |

### General Structure

- **Rows:** ~59,400 records
- **Columns:** 40 feature columns + 1 target column (after merging)
- **Data types:** Mix of numeric (int/float), categorical (string), boolean, and datetime columns
- **Missing values:** Several columns contain missing or zero values that require treatment

---

## 3. Type of ML Problem

This is a **supervised multiclass classification** problem.

- **Supervised** — labelled training data is provided.
- **Multiclass** — there are three possible output classes, not just binary yes/no.
- **Evaluation metrics** — use **classification accuracy** as your primary metric, but also examine the **confusion matrix** and **weighted F1-score** given the potential class imbalance across the three labels.

---

## 4. Project Folder Structure

```
water-pump-prediction/
│
├── data/
│   ├── raw/                    # Original, unmodified dataset files
│   │   ├── train.csv
│   │   └── labels.csv
│   └── processed/              # Cleaned and feature-engineered dataset
│       └── train_clean.csv
│
├── notebooks/
│   └── water_pump_analysis.ipynb   # Single notebook with markdown sections per step
│
├── app/                        # Flask deployment application
│   ├── templates/
│   │   └── index.html          # Combined input form and prediction result page
│   ├── app.py                  # Flask application entry point
│   └── requirements.txt        # App-specific dependencies
│
├── models/
│   └── best_model.pkl          # Saved trained model (pipeline)
│
├── reports/
│   └── figures/                # Saved EDA plots and charts
│
├── requirements.txt            # Project-wide dependencies
├── .gitignore
└── README.md
```

---

## 5. ML Workflow

You will work in a single or multiple notebooks (`water_pump_analysis.ipynb`). Use **markdown cells** to clearly label and separate each step. The steps below define what each section of your notebook should cover.

---

### 5.1 Setting Up Your Environment

Before opening your notebook, always work inside a **virtual environment** to isolate your project dependencies.

**Windows (Command Prompt / PowerShell)**

- Create: `python -m venv venv`
- Activate: `venv\Scripts\activate`
- Install: `pip install -r requirements.txt`

**Linux / macOS (Terminal)**

- Create: `python3 -m venv venv`
- Activate: `source venv/bin/activate`
- Install: `pip install -r requirements.txt`

**Suggested packages to include in `requirements.txt`:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `joblib`, `flask`, `jupyter`, `notebook`, `ipykernel`


---

### 5.2 Step 1 — Data Loading & Exploration

*Markdown label in notebook: `## Step 1 — Data Loading & Exploration`*

This is your first look at the data. In this section you should:

- Import all required libraries
- Load both CSV files and merge them on the shared `id` column
- Inspect the shape, column names, and data types
- Preview the first and last few rows
- Check the distribution of the target variable (`status_group`)
- Identify missing values across all columns
- Identify columns with suspicious zero values (e.g. coordinates, year, population)
- Check the number of unique values (cardinality) per categorical column

---

### 5.3 Step 2 — Data Cleaning & Feature Engineering

*Markdown label in notebook: `## Step 2 — Data Cleaning & Feature Engineering`*

Clean the raw data and derive new useful features. In this section you should:

- Investigate and handle missing values — consider whether to drop, fill, or flag them based on each column's context
- Investigate zero values in numeric columns and decide whether they represent genuine zeros or missing data
- Identify and handle duplicated or redundant feature groups (see Notes & Hints)
- Investigate high-cardinality columns and decide whether to retain, reduce, or drop them
- Parse the `date_recorded` column into useful numeric components (e.g. year, month)
- Engineer new features where possible — for example, consider deriving the age of a pump from available date information
- Encode the target variable into a numeric format for modelling
- Save the cleaned dataset to `data/processed/train_clean.csv`

---

### 5.4 Step 3 — EDA & Correlation Analysis

*Markdown label in notebook: `## Step 3 — EDA & Correlation Analysis`*

Explore the data visually and understand how features relate to the target. In this section you should:

**Univariate Analysis**
- Visualise the distribution of key numeric features using histograms or box plots
- Visualise the frequency of key categorical features using bar charts

**Bivariate Analysis (Feature vs. Target)**
- For categorical features: plot the proportion of each target class within each category (e.g. stacked or grouped bar charts). This helps surface which categories are strongly associated with functional vs. non-functional waterpoints.
- For numeric features: use box plots or violin plots grouped by the target class to see if distributions differ across classes

**Correlation Analysis**
- For numeric features: compute and visualise a **correlation matrix** (heatmap) to identify linear relationships between numeric columns and check for multicollinearity
- For categorical features vs. the target: use **Cramér's V** to measure the strength of association between each categorical column and `status_group`. This is the appropriate correlation measure for categorical-to-categorical relationships. Rank the features by their Cramér's V score to identify which are most informative.
- Note down which features appear most predictive — this will inform your feature selection in modelling

**Geographic Analysis (Optional)**
- Scatter plot of latitude vs. longitude coloured by target class to check for spatial patterns in functionality

---

### 5.5 Step 4 — Sklearn Pipelines & ML Modelling

*Markdown label in notebook: `## Step 4 — Sklearn Pipelines & ML Modelling`*

Build a reproducible preprocessing pipeline and train multiple classification models. In this section you should:

- Separate your features (`X`) and target (`y`) from the cleaned dataset
- Split the data into a **training set and a test set** (you will use this test set for final evaluation — there is no external test file)
- Define your numeric and categorical feature groups based on insights from EDA
- Build a `ColumnTransformer` preprocessing pipeline that handles imputation, scaling (for numeric features), and encoding (for categorical features) separately
- Wrap the preprocessor and each classifier into a full `Pipeline` object so that all transformations are applied consistently
- Train and evaluate at least the following model types:
  - Logistic Regression (baseline)
  - Decision Tree
  - Random Forest
  - Gradient Boosting or another ensemble method
- Use **cross-validation** on the training set to get a more reliable estimate of each model's performance
- Optionally perform **hyperparameter tuning** on your best-performing model

---

### 5.6 Step 5 — Model Evaluation & Saving

*Markdown label in notebook: `## Step 5 — Model Evaluation & Saving`*

Compare all trained models and save the best one. In this section you should:

- Evaluate all models on the held-out test set using accuracy, weighted F1-score, and the full classification report (precision, recall, F1 per class)
- Plot a **confusion matrix** for each model to understand where errors are concentrated
- Select the best model based on your evaluation metrics and justify your choice
- Save the final trained pipeline to `models/best_model.pkl` using `joblib`
- Save any encoders used on the target variable alongside the model

---

## 6. Model Deployment with Flask

Once you have a saved model, deploy it as a simple web application using Flask.

### How it works

- `app/app.py` loads the saved model, exposes a home route (`GET /`) that renders the form, and a predict route (`POST /predict`) that reads the form inputs, passes them through the model pipeline, and returns the prediction.
- `app/templates/index.html` is a **single HTML page** that contains both the input form and a section to display the prediction result. Use Jinja2 template logic to conditionally show the result section only after a prediction has been made.
- Run the app locally with `python app.py` from inside the `app/` folder, then open `http://127.0.0.1:5000/` in your browser.

>  The input fields in your form should correspond to the features your final model pipeline expects. Keep the form focused on the most impactful features identified during EDA — you don't need to expose all 40 columns.

---

## 7. Notes & Hints

###  Dataset Files Must Be Merged

The features and labels are in two separate files. Always load and join them on the `id` column before doing anything else. Failing to do this is one of the most common early mistakes.

###  Columns with Similar Names Likely Carry Similar Data

You will notice several groups of columns that appear to describe the same thing at different levels of detail — for example, there are three columns each for extraction type, water source, waterpoint type, management, payment, water quality, and quantity. Within each group, the columns likely contain overlapping or near-identical information. **Investigate each group** to understand how the columns relate to one another, and be mindful of the multicollinearity this can introduce. You should avoid keeping all columns from the same group in your final feature set without justification.

###  Zero Values May Not Mean Zero

Some numeric columns may contain `0` as a placeholder for missing data rather than a genuine measurement. Inspect columns like construction year, population, and GPS coordinates carefully before treating zeros as valid values.

###  GPS Coordinates Can Flag Invalid Rows

A latitude and longitude of `0, 0` places a waterpoint in the middle of the ocean. These are clearly erroneous entries. Decide how to handle them during cleaning.

###  Some Categorical Columns Have Very High Cardinality

Columns like `funder`, `installer`, and `subvillage` may contain hundreds or thousands of unique values. Encoding all of them directly can be problematic. Explore the distribution of values and consider strategies to reduce cardinality before encoding.

###  Check for Class Imbalance in the Target

The three target classes may not be equally represented. Check the distribution early and keep it in mind when selecting your evaluation metric. Accuracy alone can be misleading when classes are imbalanced.

###  Cramér's V for Categorical Correlation

Standard Pearson correlation only works for numeric features. For understanding the relationship between categorical features and the target, use **Cramér's V** — a value between 0 (no association) and 1 (perfect association). Libraries like `scipy` or `pingouin` can help you compute it, or you can implement it using a chi-squared contingency table.

---

## 8. Deliverables Checklist
-  Virtual environment created and dependencies installed
-  Raw data files placed in `data/raw/`
-  Step 1: Data loaded, merged, and explored in notebook
-  Step 2: Data cleaned and new features engineered; cleaned file saved
-  Step 3: EDA complete with numeric and categorical correlation analysis; key findings noted
-  Step 4: Sklearn pipelines built and multiple models trained with cross-validation
-  Step 5: Best model selected, evaluated on test set, and saved to `models/`
-  Flask app running locally with a single-page form and prediction output
-  `README.md` present and up to date  
__Push the final project to github__
---

*Good luck!* 💧