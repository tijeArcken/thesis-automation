Full quality review of the thesis — writing, methodology, code, and overall coherence. Returns a unified scored report.

## Usage
`/thesis-review [scope]`

Scope options:
- `all` — complete review across all 5 dimensions
- `writing` — focus on academic writing quality only
- `methodology` — focus on methodology validity only
- `code` — focus on code correctness only
- `pre-submit` — final check before a deadline (all dimensions, prioritized by severity)
- `/thesis-review` (no scope) — defaults to `all`

## Context

**Read CLAUDE.md before proceeding** to determine:
- Thesis topic and research question (section 1)
- Key deadlines (section 2)
- Grading breakdown if available (section 3)
- Research focus areas and methods (section 4)
- Starting literature (section 5)
- Chapter structure (section 7)

## 5 Quality Dimensions

### Dimension 1 — Research Question & Contribution (score /10)
- Is the research question clear, specific, and answerable?
- Does the thesis make a genuine contribution (not just applying methods mechanically)?
- Is the contribution appropriate for the degree level specified in CLAUDE.md section 1?
- Is the connection to the research focus areas from CLAUDE.md section 4 explicit?

### Dimension 2 — Literature & Theory (score /10)
- Are the key papers from CLAUDE.md section 5 cited and discussed?
- Is the literature review organized thematically, not just a list of summaries?
- Is there a clear gap identification that motivates the thesis?
- Are claims supported by citations?

### Dimension 3 — Methodology (score /10)
- Are the methods correctly specified and explained?
- Is the evaluation strategy valid (no leakage, correct validation)?
- Is there an appropriate benchmark for comparison?
- Are robustness checks included?

### Dimension 4 — Empirical Results (score /10)
- Are results clearly presented (tables, figures, in-text interpretation)?
- Are results interpreted substantively, not just statistically?
- Is the difference between in-sample and out-of-sample performance discussed (for quantitative work)?
- Are the results honest (neither cherry-picked nor undersold)?

### Dimension 5 — Academic Writing (score /10)
- Is the writing clear, concise, and at the right academic register?
- Is the structure logical (follows the chapter structure from CLAUDE.md section 7)?
- Are all claims properly hedged and cited?
- Is the grammar correct?

## Output Format

```
## Thesis Quality Review — [Date]

### Dimension 1: Research Question & Contribution — [X/10]
[2-4 sentences of assessment]
Issues: [bulleted list sorted by severity]

### Dimension 2: Literature & Theory — [X/10]
...

### Dimension 3: Methodology — [X/10]
...

### Dimension 4: Empirical Results — [X/10]
...

### Dimension 5: Academic Writing — [X/10]
...

---
## Overall Score: [X/50] -> [Letter grade estimate]

## Top 5 Priority Actions (before next deadline)
1. ...
2. ...
3. ...
4. ...
5. ...
```

Reference the next deadline from CLAUDE.md section 2 in the priority actions. If grading information is available in section 3, note which grade components are most at risk.
