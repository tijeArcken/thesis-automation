Review the methodology for validity, soundness, and alignment with the research question.

## Usage
`/check-methodology [focus]`

Focus areas:
- `model-selection` — are the right models/methods chosen for this task?
- `evaluation` — are metrics and validation procedures correct?
- `features` — are the predictors/variables sensible and leakage-free?
- `overfitting` — is regularization and model complexity appropriate?
- `robustness` — are robustness checks planned or implemented?
- `/check-methodology` (no focus) — full review across all dimensions

## Context

**Read CLAUDE.md before proceeding** to determine:
- Research focus areas (section 4)
- Methods (section 4)
- Data sources (section 4)
- Methodology type: quantitative / qualitative / mixed (section 4)
- Skill level (section 4)
- Deadlines for priority recommendations (section 2)

## Review Dimensions

### For Quantitative Methodology

#### Model Selection
- Is each model/method appropriate for the prediction or estimation task?
- Are the methods properly motivated relative to the research question?
- Is there a clear baseline for comparison (e.g., OLS, simple average, random walk)?
- Are the computational constraints of the data size considered?

#### Evaluation
- Is the evaluation strictly out-of-sample? Are results clearly labeled as in-sample vs out-of-sample?
- Is temporal structure respected? (No future data in training window for sequential data)
- Is the validation scheme appropriate for the data type? (Time-series CV for panel/time-series data, k-fold for cross-sectional)
- Are multiple metrics reported?

#### Features / Predictors
- Are feature transformations economically or theoretically motivated?
- Are features standardized when required by the method?
- Is there a risk of multicollinearity, and is it addressed?
- Could any feature inadvertently contain information from the future (leakage)?

#### Overfitting
- Is regularization strength tuned by cross-validation, not chosen arbitrarily?
- For tree-based methods: are key hyperparameters tuned?
- For neural networks: is early stopping or dropout used?
- Is the difference between train and test performance monitored?

#### Robustness
- Are results checked on different subsamples?
- Are results stable across different hyperparameter values?
- Is a rolling-window or expanding-window evaluation used for time-series?
- Is there sensitivity analysis on key modeling assumptions?

### For Qualitative Methodology

#### Research Design
- Is the research design (case study, grounded theory, phenomenology, etc.) appropriate for the RQ?
- Is the sampling strategy clearly justified (purposive, theoretical, snowball)?
- Is the scope appropriate for the degree level?

#### Data Collection
- Are the data collection methods clearly described (interviews, observations, documents)?
- Is the interview protocol or observation guide included?
- Are ethical considerations addressed?

#### Analysis
- Is the coding approach clearly described (deductive, inductive, abductive)?
- Is there a clear audit trail from data to findings?
- How is inter-coder reliability established (if applicable)?

#### Trustworthiness
- Credibility: Are findings plausible? Is there member checking or triangulation?
- Transferability: Is the context described in enough detail?
- Dependability: Could another researcher follow the same process?
- Confirmability: Is the researcher's positionality acknowledged?

### For Mixed Methods

Apply both quantitative and qualitative dimensions as relevant, plus:
- Is the integration strategy clear (how do the two components inform each other)?
- Is the sequencing justified?
- If results conflict across methods, is there a resolution strategy?

## Output Format

For each dimension reviewed:

**[DIMENSION] — [PASS / WARNING / FAIL]**
> Concern: [what the issue is]
> Why it matters: [consequence for validity]
> Fix: [concrete recommended action]

End with a **Priority List** of the top 3 things to fix before the next deadline from CLAUDE.md section 2.
