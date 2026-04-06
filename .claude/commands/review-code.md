Review a script or notebook for correctness, best practices, and defense readiness.

## Usage
`/review-code [file]`

Examples:
- `/review-code code/analysis.ipynb`
- `/review-code code/model_training.py`
- `/review-code` — review the most recently modified file in `code/`

## Context

**Read CLAUDE.md before proceeding** to determine:
- Code stack (section 6 — e.g., Python with sklearn, R with tidyverse, Stata)
- Methodology type (section 4)
- Methods used (section 4)

If the code stack is "N/A" or the methodology is purely qualitative, tell the user: "This skill is designed for quantitative code review. For qualitative analysis scripts, use `/proofread` instead."

## What to Check

### 1. Data Leakage (CRITICAL)
- Is preprocessing (scaling, normalization, encoding) fit on the full dataset before splitting? (Wrong: must fit only on training data)
- Are future values used as features for predicting past outcomes?
- Is cross-validation applied after or before preprocessing? (Must be after, inside CV loop)
- For time-series data: is standard k-fold used instead of time-series CV? (Wrong for sequential data)

### 2. Model Evaluation
- Is the train/test split appropriate for the data type (random vs time-ordered)?
- Are evaluation metrics appropriate for the task?
  - Regression: RMSE, MAE, R-squared — is in-sample vs out-of-sample clearly distinguished?
  - Classification: accuracy, AUC, F1 — is class imbalance considered?
- Is there a benchmark model for comparison?

### 3. Feature Engineering
- Are features scaled when required by the method?
- Are categorical variables encoded correctly?
- Is multicollinearity addressed or discussed?

### 4. Hyperparameter Tuning
- Is the regularization parameter tuned via CV, not eyeballed?
- Is the tuning done inside the train set only (not touching the test set)?
- Is the tuning range reasonable?

### 5. Code Correctness

**For Python (sklearn, pandas, numpy):**
- Are API calls used correctly (`.fit()`, `.predict()`, `.transform()` order)?
- Are random seeds set for reproducibility?
- Are pandas operations correct (no SettingWithCopyWarning, correct `.loc`/`.iloc` usage)?

**For R (tidyverse, caret, tidymodels):**
- Are pipe operations correct?
- Is the formula interface used properly?
- Are factor levels handled correctly?

**For Stata:**
- Are estimation commands appropriate?
- Are post-estimation commands correct?
- Is the do-file structured clearly?

### 6. Defense Readiness
For each major code block, explain:
- **What it does** — plain English
- **Why it works** — the underlying concept
- **What would happen if it were done differently** — so you can answer examiner questions

## Output Format

Return a review organized as:

**CRITICAL ISSUES** (could invalidate results)
- [File:line] Issue + explanation + fix

**IMPORTANT ISSUES** (affect validity/interpretation)
- [File:line] Issue + explanation + fix

**STYLE / EFFICIENCY** (minor)
- [File:line] Issue + suggestion

**DEFENSE PREP NOTES**
- Key questions an examiner is likely to ask about this code
- Plain-English explanations of the most important code blocks
