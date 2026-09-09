# Mental Health & Burnout Prediction: Beginner Data Science Project

## 1. Objective

You'll work with a synthetic dataset of **50,000 people** and **40 columns**, covering demographics, work, lifestyle habits, and psychological indicators. The task is **classification**: predict `Burnout_Risk` (`Low` / `Moderate` / `High`) for each person.

**Dataset source:** [Mental Health & Burnout Prediction Dataset (Kaggle)](https://www.kaggle.com/datasets/mobeenfatimah/mental-health-and-burnout-prediction-dataset)
**File used in this project:** `mental_health_burnout_prediction_dataset.csv`
**Target column:** `Burnout_Risk`

Your goal is to take this dataset from raw CSV to a working, evaluated model, in **one notebook**, following the steps below in order. Every step should have a markdown cell explaining what you did and why; that explanation is as important as the code.

### ⚠️ Important: watch for leakage

Two other columns in this dataset describe the **same underlying outcome** as `Burnout_Risk`, and must be **dropped from your features `X`**:

| Column | Type | Why it must be dropped |
|---|---|---|
| `Burnout_Score` | Numeric (0–100) | `Burnout_Risk` is built directly from this (Low = 0–39, Moderate = 40–64, High = 65–100). Keeping it in `X` means the model just reads the threshold instead of learning anything. |
| `Mental_Health_Status` | Categorical (`Healthy` / `Needs Attention` / `Critical`) | Also built from `Burnout_Score`, using different thresholds; almost the same information as your target. |

Also drop:
- `AI_Wellness_Recommendation`: looks like a recommendation generated *after* burnout risk is known (a consequence, not a cause), so it would leak information too.
- `Person_ID`: just an identifier, not a predictive feature.

If your model gets suspiciously close to 100% accuracy, it's almost certainly because one of these four columns snuck back into `X`. This is called **data leakage**, and catching it is one of the most important skills in this project.

---

## 2. Data Dictionary

| Column | Type | Notes |
|---|---|---|
| `Person_ID` | int | Identifier, drop before modeling |
| `Age` | float | Has missing values |
| `Gender` | category (3) | Male / Female / Other |
| `Country` | category (25) | |
| `Occupation` | category (20) | |
| `Education_Level` | category (5) | High School → PhD |
| `Employment_Status` | category (4) | Employed / Student / Self-Employed / Unemployed |
| `Monthly_Income_USD` | float | Has missing values |
| `Work_Hours_Per_Week` | int | |
| `Remote_Work` | category (3) | Yes / No / Hybrid |
| `Job_Satisfaction` | float | 1–10 scale, has missing values |
| `Work_Life_Balance` | float | 1–10 scale, has missing values |
| `Sleep_Hours` | float | Has missing values |
| `Sleep_Quality` | category (4) | Poor / Average / Good / Excellent |
| `Stress_Level` | category (3) | Low / Moderate / High |
| `Anxiety_Score` | float | Has missing values |
| `Depression_Score` | float | Has missing values |
| `Mood_Score` | float | Has missing values |
| `Emotional_Stability` | int | |
| `Physical_Activity_Hours` | float | Has missing values |
| `Exercise_Frequency` | category (4) | Never / Rarely / Weekly / Daily |
| `Meditation_Minutes` | float | Has missing values |
| `Screen_Time_Hours` | float | Has missing values |
| `Social_Media_Hours` | float | Has missing values |
| `Gaming_Hours` | float | Has missing values |
| `Coffee_Cups_Per_Day` | int | |
| `Alcohol_Consumption` | category (2) | Yes / No |
| `Smoking` | category (2) | Yes / No |
| `Healthy_Diet` | category (2) | Yes / No |
| `Chronic_Stress` | category (2) | Yes / No |
| `Family_History_Mental_Illness` | category (2) | Yes / No |
| `Therapy_Attendance` | category (2) | Yes / No, has missing values |
| `Support_System` | category (4) | Poor / Average / Good / Excellent |
| `Life_Satisfaction` | float | Has missing values |
| `Productivity_Score` | float | Has missing values |
| `Absenteeism_Days` | int | |
| `Burnout_Score` | int (0–100) | **Drop from features, leaky, see note above** |
| `Mental_Health_Status` | category (3) | **Drop from features, leaky, see note above** |
| `AI_Wellness_Recommendation` | category (7) | **Drop from features, leaky** |
| `Burnout_Risk` | category (3) | **This is the target `y`**: Low / Moderate / High |

**Columns with missing values (16 total):** `Age`, `Monthly_Income_USD`, `Job_Satisfaction`, `Work_Life_Balance`, `Sleep_Hours`, `Anxiety_Score`, `Depression_Score`, `Mood_Score`, `Physical_Activity_Hours`, `Meditation_Minutes`, `Screen_Time_Hours`, `Social_Media_Hours`, `Gaming_Hours`, `Therapy_Attendance`, `Life_Satisfaction`, `Productivity_Score`. All are under 3% of rows missing, small enough to impute safely. No duplicate rows in the file.

---

## 3. Folder Structure

Keep it simple:

```
mental-health-burnout-project/
│
├── README.md                 <- Project instructions AND your final write-up (see Step 9)
├── requirements.txt          <- Packages you used
│
├── data/
│   └── mental_health_burnout_prediction_dataset.csv
│
└── notebooks/
    └── mental_health_burnout_project.ipynb   <- Your one and only notebook
```

No separate `report.md`. Your findings go straight into this `README.md`, at the bottom, under a `## Findings & Final Report` section (see Step 9).

---

## 4. Step-by-Step Workflow (all in one notebook)

Use markdown headers in your notebook to separate these sections clearly; it should read top to bottom like a story.

### Step 1: Load the Data & Look Around
- [ ] Load `mental_health_burnout_prediction_dataset.csv` with pandas
- [ ] Check `.shape` (should be 50,000 × 40), `.head()`, `.info()`, `.describe()`
- [ ] Confirm your understanding of each column against the Data Dictionary above
- [ ] Note in a markdown cell that `Burnout_Risk` is your target, and that `Burnout_Score`, `Mental_Health_Status`, `AI_Wellness_Recommendation`, and `Person_ID` will need to be dropped from the features before modeling

### Step 2: Pre-Cleaning Checks
- [ ] Check for missing values (`df.isnull().sum()`); you should find the 16 columns listed above
- [ ] Check for duplicate rows (`df.duplicated().sum()`); should be 0, but confirm it yourself
- [ ] Check your target's distribution (`value_counts()`): is it balanced? (`Burnout_Risk`: Low ~51%, Moderate ~30%, High ~20%, moderately imbalanced)
- [ ] Check for obviously wrong values (e.g. negative ages, scores outside their stated scale)
- [ ] Note down everything you found before fixing anything

### Step 3: Clean the Data
- [ ] Handle missing values: for numeric columns, median imputation is a safe default; for `Therapy_Attendance` (categorical), consider filling with the mode or an `"Unknown"` category. Explain your choice for each column.
- [ ] Confirm data types look right (e.g. `Work_Hours_Per_Week`, `Coffee_Cups_Per_Day` as integers)
- [ ] Standardize any messy category labels if you spot them
- [ ] Re-check Step 2's issues to confirm they're fixed

### Step 4: Hypothesis Testing
Pick a few features you think matter most and test them properly instead of just guessing from a chart. Good candidates given this dataset: `Sleep_Hours`, `Work_Hours_Per_Week`, `Stress_Level`, `Job_Satisfaction`, `Support_System`, `Chronic_Stress`.

- **Numerical feature vs. target** (e.g. `Sleep_Hours` vs. `Burnout_Risk`): use ANOVA (3 target groups) to check if the average of the feature really differs across target groups. State H₀, H₁, and your conclusion from the p-value.
- **Categorical feature vs. target** (e.g. `Chronic_Stress` vs. `Burnout_Risk`): use a Chi-square test to check if the feature and target are related.

Do this for at least 3–4 numeric and 3–4 categorical features, and summarize your results in a small table.

### Step 5: Exploratory Data Analysis (EDA)
Answer these with a plot or table + 2–3 sentences each:

1. What does the distribution of `Burnout_Risk` look like?
2. What do the distributions of `Sleep_Hours`, `Work_Hours_Per_Week`, `Stress_Level`-related scores look like (histograms)? Any skewed ones?
3. How do `Anxiety_Score`, `Depression_Score`, and `Mood_Score` compare across burnout risk groups (boxplots)?
4. How does burnout risk change across `Employment_Status`, `Remote_Work`, and `Support_System` categories (bar charts)?
5. Does `Work_Hours_Per_Week` combined with `Sleep_Hours` show a clearer pattern with burnout than either alone (scatter plot colored by target)?
6. Is there a correlation heatmap pattern among the numeric wellbeing scores (`Anxiety_Score`, `Depression_Score`, `Mood_Score`, `Life_Satisfaction`, `Productivity_Score`)? Do any move together strongly?
7. Do `Chronic_Stress` and `Family_History_Mental_Illness` show a noticeably higher burnout rate than the rest of the population?
8. Which features seem most associated with burnout overall, and does that match your Step 4 hypothesis test results?

Feel free to add your own questions if you notice something interesting.

### Step 6: Split Features and Target, Then Train/Test Split
- [ ] Drop `Person_ID`, `Burnout_Score`, `Mental_Health_Status`, and `AI_Wellness_Recommendation` from the dataframe before building `X`
- [ ] Encode the remaining categorical columns (one-hot encoding is fine to start)
- [ ] Scale numeric columns if you're using a model that needs it (KNN, SVM, logistic regression, neural net)
- [ ] Split into `X` (all remaining features) and `y = df['Burnout_Risk']`
- [ ] Split into train and test sets (80/20) with `train_test_split(..., stratify=y, random_state=42)`
- [ ] If you train a neural network later, also carve a small validation set out of the training data (e.g. train 70% / val 10% / test 20%)

### Step 7: Train Several Models with Cross-Validation
Start with a simple baseline (always predict the most common class, `Low`, ~51% of rows), then try a handful of models using 5-fold cross-validation on the training set:

- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbors
- Gradient Boosting / XGBoost
- (Optional, if you want to go further) a simple Neural Network

For each, record the average cross-validation accuracy and F1-score (use macro-F1 since the classes are imbalanced), and build one small comparison table so you can see which models are doing best.

### Step 8: Hyperparameter Tuning
- [ ] Pick your top 2 models from Step 7
- [ ] Use `GridSearchCV` or `RandomizedSearchCV` to tune a few key hyperparameters for each (e.g. `n_estimators`, `max_depth`, `learning_rate`)
- [ ] Refit the best version on the full training set and evaluate it once on the test set (only now; don't touch the test set before this point)

### Step 9: Wrap Up in This README
Add a `## Findings & Final Report` section to the bottom of this README (half a page to a page) covering:
- What the data looked like and what you cleaned
- Your hypothesis test findings
- Your key EDA insights
- Which model won and its final test-set performance (accuracy + macro-F1 + confusion matrix)
- One or two things you'd try next with more time

---

## 5. A Few Reminders

- Set `random_state=42` everywhere so your results are reproducible.
- Fit scalers/encoders on the training data only, then apply them to the test data. Never fit on test data.
- The target is imbalanced (`Low` ~51%, `Moderate` ~30%, `High` ~20%). Don't judge your model on accuracy alone; check macro-F1, precision, and recall too.
- Watch out for the leakage columns described in Section 1. If your model gets 99%+ accuracy, that's a red flag that a leaky column snuck back into `X`, not a sign your model is great.
- This is a sensitive topic even on synthetic data. Keep your language and conclusions responsible (correlation isn't causation).

---

## 6. Deliverables

Your GitHub repo should contain, at minimum:
- [ ] The dataset in `data/`
- [ ] One complete, well-commented notebook in `notebooks/` that runs top to bottom without errors
- [ ] `requirements.txt` listing the packages you used
- [ ] This `README.md`, updated with your name at the top and a `## Findings & Final Report` section at the bottom (see Step 9)

---

## 7. Suggested `requirements.txt`

```
pandas
numpy
scipy
scikit-learn
matplotlib
seaborn
xgboost
statsmodels
jupyter
```

Good luck. Work through it one step at a time, and don't worry about getting the "best" model. A clean, well-explained process (and catching the leakage trap!) matters more than a perfect score.

---

## Findings & Final Report

*(Fill this section in as your Step 9 deliverable, once your notebook is complete.)*

**Data summary:** What did the raw data look like, and what did you clean?

**Hypothesis test results:** Summary of which features were statistically significant against `Burnout_Risk`.

**Key EDA insights:** 2-4 bullet points on the most interesting patterns you found.

**Final model:** Which model you chose, its final test-set accuracy, macro-F1, and confusion matrix.

**Next steps:** What you'd try with more time or data.

