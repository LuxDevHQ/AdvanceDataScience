# Resume Screening & ATS Hiring: Beginner Data Science Project

## 1. Objective

You'll work with a synthetic dataset of **100,000 job candidates** and **44 columns**, covering candidate background, education, skills, test/interview scores, and ATS (Applicant Tracking System) metrics. The task is **classification**: predict `selected` (`Selected` / `Rejected`) for each candidate.

**Dataset source:** [Resume Screening and ATS Hiring Dataset (100k Record) (Kaggle)](https://www.kaggle.com/datasets/mobeenfatimah/resume-screening-and-ats-hiring-dataset100k-record)
**File used in this project:** `ai_resume_screening_dataset.csv`
**Target column:** `selected`

Your goal is to take this dataset from raw CSV to a working, evaluated model, in **one notebook**, following the steps below in order. Every step should have a markdown cell explaining what you did and why; that explanation is as important as the code.

### ⚠️ Important: drop PII and identifier columns

This dataset includes personally identifiable information that should never be used as a model feature, plus a few pure identifier columns. Drop all of these from your features `X` before modeling:

`candidate_id`, `full_name`, `email`, `phone`, `github_profile`, `linkedin_profile`

None of these describe anything about a candidate's qualifications; they only identify who the row belongs to. Including them risks the model "memorizing" individuals instead of learning general patterns, and it's bad practice to build hiring models on names, emails, or phone numbers even in a synthetic dataset.

### ⚠️ Also watch: very high-cardinality columns

A few columns have so many unique values that one-hot encoding them directly would create tens of thousands of new columns and likely hurt your model more than help it:

| Column | Unique values | Suggestion |
|---|---|---|
| `city` | ~37,950 | Drop it; `country` already captures location at a usable level |
| `preferred_location` | ~15,831 | Drop it, or reduce to a simpler "same as country?" flag if you want to keep it |
| `previous_companies` | ~34,104 (free text, comma-separated) | Turn into a simple count feature (e.g. `num_previous_companies`) instead of encoding the raw text |
| `technical_skills` | ~97,372 (free text, comma-separated) | Turn into a count feature (e.g. `num_technical_skills`), or flag the presence of a handful of common skills you're interested in |

### ⚠️ Also watch: comma-separated "list" columns

`technical_skills`, `programming_languages`, `frameworks`, `databases`, `cloud_platform`, and `certifications` are not simple categories; each cell holds a comma-separated list (e.g. `"Pandas, HTML, Git, C++, Java"`), and many rows use the literal text `"Not Applicable"` to mean "none." Don't one-hot encode these as-is. The simplest beginner-friendly approach: for each of these columns, engineer a count feature (how many items are listed, treating `"Not Applicable"` as 0) rather than trying to encode every possible value.

---

## 2. Data Dictionary

| Column | Type | Notes |
|---|---|---|
| `candidate_id` | string | Identifier, drop before modeling |
| `full_name` | string | PII, drop before modeling |
| `email` | string | PII, drop before modeling |
| `phone` | string | PII, drop before modeling |
| `country` | category (243) | |
| `city` | category (~37,950) | Very high cardinality, drop (see note above) |
| `age` | int | Range 21-55 |
| `gender` | category (3) | Male / Female / Other |
| `highest_education` | category (5) | High School → PhD |
| `university` | category (15) | |
| `field_of_study` | category (9) | |
| `cgpa` | float | Range 2.5-4.0 |
| `graduation_year` | int | Range 1989-2026 |
| `experience_years` | int | Range 0-35 |
| `previous_companies` | string, comma-separated list | ~21% are `"Not Applicable"`; turn into a count feature |
| `current_job_title` | category | |
| `internship_experience` | category (2) | Yes / No |
| `leadership_experience` | category (2) | Yes / No |
| `technical_skills` | string, comma-separated list | Turn into a count feature |
| `programming_languages` | string, comma-separated list | ~31% are `"Not Applicable"`; turn into a count feature |
| `frameworks` | string, comma-separated list | Turn into a count feature |
| `databases` | string, comma-separated list | ~31% are `"Not Applicable"`; turn into a count feature |
| `cloud_platform` | string, comma-separated list | ~31% are `"Not Applicable"`; turn into a count feature |
| `projects_completed` | int | |
| `github_profile` | string | PII, drop before modeling |
| `linkedin_profile` | string | PII, drop before modeling |
| `certifications` | string, comma-separated list | Turn into a count feature |
| `publications` | int | Range 0-3 |
| `communication_score` | int | |
| `problem_solving_score` | int | |
| `technical_test_score` | int | |
| `interview_score` | int | |
| `aptitude_score` | int | |
| `job_role` | category (15) | |
| `expected_salary` | int | Range 45,000-401,000 |
| `preferred_location` | category (~15,831) | Very high cardinality, drop or simplify (see note above) |
| `employment_type` | category (4) | Full-Time / Part-Time / Contract / Internship |
| `remote_preference` | category (3) | On-site / Hybrid / Remote |
| `availability` | category (5) | Immediate / 15 / 30 / 60 / 90 Days |
| `resume_quality_score` | int | |
| `resume_length` | int | Range 1-4 (pages) |
| `keyword_match_percentage` | float | |
| `ats_score` | int | Range 40-99 |
| `selected` | category (2) | **This is the target `y`**: Selected / Rejected |

**Missing values:** none. **Duplicate rows:** none. **Target balance:** exactly 50,000 `Selected` / 50,000 `Rejected`, a perfectly balanced target, which makes this a friendlier starting point than the burnout dataset for beginners (accuracy is a reasonable metric here, though it's still worth checking precision/recall).

---

## 3. Folder Structure

Keep it simple:

```
resume-ats-project/
│
├── README.md                 <- Project instructions AND your final write-up (see Step 9)
├── requirements.txt          <- Packages you used
│
├── data/
│   └── ai_resume_screening_dataset.csv
│
└── notebooks/
    └── resume_ats_project.ipynb   <- Your one and only notebook
```

No separate `report.md`. Your findings go straight into this `README.md`, at the bottom, under a `## Findings & Final Report` section (see Step 9).

---

## 4. Step-by-Step Workflow (all in one notebook)

Use markdown headers in your notebook to separate these sections clearly; it should read top to bottom like a story.

### Step 1: Load the Data & Look Around
- [ ] Load `ai_resume_screening_dataset.csv` with pandas
- [ ] Check `.shape` (should be 100,000 x 44), `.head()`, `.info()`, `.describe()`
- [ ] Confirm your understanding of each column against the Data Dictionary above
- [ ] Note in a markdown cell that `selected` is your target, and list the PII/identifier/high-cardinality columns you'll drop before modeling

### Step 2: Pre-Cleaning Checks
- [ ] Check for missing values (`df.isnull().sum()`); this dataset has none, but confirm it yourself
- [ ] Check for duplicate rows (`df.duplicated().sum()`); should be 0
- [ ] Check your target's distribution (`value_counts()`); should be an exact 50/50 split
- [ ] Look at the comma-separated columns (`technical_skills`, `programming_languages`, etc.) and count how often `"Not Applicable"` appears in each
- [ ] Check for obviously wrong values (e.g. `cgpa` outside 0-4, negative `age` or `experience_years`)
- [ ] Note down everything you found before fixing anything

### Step 3: Clean the Data
- [ ] Since there are no missing values or duplicates, "cleaning" here mostly means preparing columns for modeling rather than fixing broken data
- [ ] For each comma-separated column, engineer a count feature (e.g. `num_technical_skills = technical_skills.apply(lambda x: 0 if x == "Not Applicable" else len(x.split(",")))`)
- [ ] Drop the PII columns listed in Section 1
- [ ] Drop or simplify `city` and `preferred_location` as noted in Section 1
- [ ] Standardize any messy category labels if you spot them
- [ ] Re-check Step 2's issues to confirm your changes worked as expected

### Step 4: Hypothesis Testing
Pick a few features you think matter most and test them properly instead of just guessing from a chart. Good candidates given this dataset: `interview_score`, `technical_test_score`, `ats_score`, `experience_years`, `keyword_match_percentage`; `highest_education`, `internship_experience`, `leadership_experience`, `remote_preference`.

- **Numerical feature vs. target** (e.g. `interview_score` vs. `selected`): since `selected` has exactly 2 groups, use an independent t-test to check if the average of the feature really differs between `Selected` and `Rejected`. State H₀, H₁, and your conclusion from the p-value.
- **Categorical feature vs. target** (e.g. `internship_experience` vs. `selected`): use a Chi-square test to check if the feature and target are related.

Do this for at least 3-4 numeric and 3-4 categorical features, and summarize your results in a small table.

### Step 5: Exploratory Data Analysis (EDA)
Answer these with a plot or table plus 2-3 sentences each:

1. What does the distribution of `selected` look like? (You already know it's 50/50, but confirm and state it.)
2. How do `ats_score`, `interview_score`, and `technical_test_score` compare between `Selected` and `Rejected` candidates (boxplots)?
3. Does `experience_years` differ meaningfully between the two groups?
4. How does the selection rate change across `highest_education` levels (bar chart)?
5. How does the selection rate change across `job_role` (bar chart)? Are some roles more competitive than others?
6. Do candidates with `internship_experience` or `leadership_experience` get selected at a noticeably higher rate?
7. Is there a relationship between your new `num_technical_skills` feature and selection?
8. Is there a correlation heatmap pattern among the six score columns (`communication_score`, `problem_solving_score`, `technical_test_score`, `interview_score`, `aptitude_score`, `resume_quality_score`)? Do any move together strongly?
9. Which features seem most associated with being selected overall, and does that match your Step 4 hypothesis test results?

Feel free to add your own questions if you notice something interesting.

### Step 6: Split Features and Target, Then Train/Test Split
- [ ] Drop the PII columns, `candidate_id`, `city`, and `preferred_location` from the dataframe before building `X`
- [ ] Make sure your engineered count features from Step 3 are included
- [ ] Encode the remaining categorical columns (one-hot encoding is fine for the low-cardinality ones like `gender`, `highest_education`, `employment_type`, `remote_preference`, `availability`, `job_role`)
- [ ] Scale numeric columns if you're using a model that needs it (KNN, SVM, logistic regression, neural net)
- [ ] Split into `X` (all remaining features) and `y = df['selected']`
- [ ] Split into train and test sets (80/20) with `train_test_split(..., stratify=y, random_state=42)`

### Step 7: Train Several Models with Cross-Validation
Start with a simple baseline (always predict the most common class; since it's an exact 50/50 split, this baseline gets 50% accuracy), then try a handful of models using 5-fold cross-validation on the training set:

- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbors
- Gradient Boosting / XGBoost
- (Optional, if you want to go further) a simple Neural Network

For each, record the average cross-validation accuracy and F1-score, and build one small comparison table so you can see which models are doing best.

### Step 8: Hyperparameter Tuning
- [ ] Pick your top 2 models from Step 7
- [ ] Use `GridSearchCV` or `RandomizedSearchCV` to tune a few key hyperparameters for each (e.g. `n_estimators`, `max_depth`, `learning_rate`)
- [ ] Refit the best version on the full training set and evaluate it once on the test set (only now; don't touch the test set before this point)

### Step 9: Wrap Up in This README
Add a `## Findings & Final Report` section to the bottom of this README (half a page to a page) covering:
- What the data looked like and how you handled the comma-separated columns
- Your hypothesis test findings
- Your key EDA insights
- Which model won and its final test-set performance (accuracy + F1 + confusion matrix)
- One or two things you'd try next with more time

---

## 5. A Few Reminders

- Set `random_state=42` everywhere so your results are reproducible.
- Fit scalers/encoders on the training data only, then apply them to the test data. Never fit on test data.
- The target is perfectly balanced, so accuracy is a reasonable headline metric here, but still check precision, recall, and F1 to make sure your model isn't just doing well on one class.
- Never train a model on PII (names, emails, phone numbers) even if it seems to "work"; it's bad practice regardless of dataset, and it's a good habit to build now.
- This is a hiring-related dataset even though it's synthetic; keep in mind that real-world resume screening models can encode bias (e.g. by proxying for gender or nationality through university or country), and it's worth a sentence in your final report reflecting on that.

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

Good luck. Work through it one step at a time, and don't worry about getting the "best" model. A clean, well-explained process (and handling those comma-separated columns sensibly!) matters more than a perfect score.

---

## Findings & Final Report

*(Fill this section in as your Step 9 deliverable, once your notebook is complete.)*

**Data summary:** What did the raw data look like, and how did you handle the comma-separated columns and PII?

**Hypothesis test results:** Summary of which features were statistically significant against `selected`.

**Key EDA insights:** 2-4 bullet points on the most interesting patterns you found.

**Final model:** Which model you chose, its final test-set accuracy, F1, and confusion matrix.

**Next steps:** What you'd try with more time or data.
