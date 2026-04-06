Verify a specific empirical claim or literature statement before including it in the thesis.

## Usage
`/fact-check [claim]`

Examples:
- `/fact-check "LASSO outperforms OLS in house price forecasting when the number of predictors exceeds 20"`
- `/fact-check "Random forests are robust to multicollinearity"`
- `/fact-check "The dataset covers 17 countries from 1870"`

## Process

### Step 1 — Parse the Claim
- Identify: (a) the factual assertion, (b) the implied source or context, (c) whether it's empirical, definitional, or interpretive

### Step 2 — Check Against Available Evidence
- Search the papers directory (see CLAUDE.md section 9 for the path) for relevant papers
- Check `data/` for any datasets that could verify the number
- Cross-reference with the starting literature listed in CLAUDE.md section 5
- If claim references a specific paper, check whether the paper actually supports it

### Step 3 — Web Verification (if needed)
- Search for the claim in academic databases or reputable sources
- Look for contradicting evidence, not just supporting evidence

### Step 4 — Verdict

Return one of:

**SUPPORTED**
> Evidence: [source(s) that confirm the claim]
> Confidence: HIGH / MEDIUM / LOW

**PARTIALLY SUPPORTED**
> What's confirmed: [the part that checks out]
> What's uncertain: [the part that needs qualification]
> Suggested revision: [safer phrasing for the thesis]

**UNSUPPORTED**
> Why: [what the evidence actually shows]
> Risk: [why including this claim could be flagged by a reviewer or examiner]
> Alternative: [what you can say instead, if anything]

## Important Notes
- Be especially careful with comparative claims ("X is better than Y") — these are context-dependent
- Be especially careful with numeric claims — verify the exact figure, not just the direction
- For ML performance claims: always ask "on what data, with what setup?" — results vary widely
