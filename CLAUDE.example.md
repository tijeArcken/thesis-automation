# Thesis Project Configuration — EXAMPLE

> This is a filled-in example based on a real ML & Real Estate thesis at UvA.
> Copy `CLAUDE.md` (the template) and fill it in, or run `/setup` to generate it interactively.

## 1. Project Context

- **University:** Universiteit van Amsterdam, Faculty of Economics and Business
- **Faculty / Department:** Faculty of Economics and Business
- **Course:** Bachelor Thesis & Thesis Seminar Finance (6013B0455 / 6013B0520), 6 EC, Semester 2 2025–2026
- **Degree level:** Bachelor
- **Topic:** Machine Learning Applications in Real Estate Markets
- **Research question:** Are there benefits in forecasting real estate variables using ML? At what frequencies? Can we build ML models of over/underpricing?
- **Format:** Group of 2 + individual robustness analysis
- **Language:** English

---

## 2. Key Deadlines

| Date | Milestone |
|------|-----------|
| April 20, 2026 | Mini-exam (multiple choice, 1.5 hrs, min 5.0) |
| May 18, 2026 | Intermediate stage product (2 draft chapters OR extensive notes) + Ethics Board registration |
| June 14, 2026 | First complete draft to supervisor |
| June 25, 2026 | FINAL thesis + changelog submitted (graded) |
| July 9, 2026 | Defense (10–15 min joint + 5–10 min individual, min 5.0) |

---

## 3. Grading (optional)

| Component | Weight | Notes |
|-----------|--------|-------|
| Joint thesis | 40% | 80% content, 20% process |
| Individual robustness analysis | 30% | |
| Mini-exam (individual) | 15% | |
| Defense (individual) | 15% | |

- Minimum **5.0** required on each component
- Weighted average **≥ 5.50** to pass overall

---

## 4. Research Design

### Research Focus Areas

1. **Non-linearities in real estate valuation/forecasting** — Can ML models capture nonlinear relationships that traditional linear models miss?
2. **Detecting over/undervaluation using ML** — Can we build models that identify mispriced real estate assets?

### Methods

- **Regularization:** LASSO, Ridge
- **Dimension reduction:** Principal Component Regression (PCR), Partial Least Squares (PLS)
- **Panel methods:** Factor Augmented panels
- **Tree-based:** Random Forests
- **Deep learning:** Neural Networks

### Data Sources

| Source | Description |
|--------|-------------|
| OECD, IMF, BIS | High-frequency aggregate data (quarterly) |
| National statistical agencies | Regional GDP, employment, unemployment, real estate indices |
| Jorda-Schularick-Taylor Macrohistory Database | Annual data, 17 advanced economies, 1870+, 45 variables |

### Methodology Type

- **Type:** quantitative

### Skill Level

- **Methods skill level:** beginner

---

## 5. Starting Literature

- Conway Viriato (2019) — "AI and Machine Learning in Real Estate Investment", *Journal of Portfolio Management*
- Lorenz et al. (2022) — "Interpretable machine learning for real estate market analysis", *Real Estate Economics*
- Perez-Rave et al. (2019) — "A machine learning approach to big data regression analysis of real estate prices", *Journal of Property Research*
- Jorda, Schularick & Taylor (2016) — "The Great Mortgaging", *Economic Policy*
- Knoll, Schularick & Steger (2016) — "No Price Like Home: Global House Prices 1870-2012", *AER*
- Capozza et al. (2002) — "Determinants of Real House Price Dynamics", *NBER Working Paper*
- Girouard et al. (2006) — "Recent House Price Developments: The Role of Fundamentals", *OECD Working Paper No. 475*

---

## 6. How Claude Should Help

- **Language:** Always respond in English
- **Code stack:** Python with sklearn, pandas, numpy
- **Writing style:** Formal academic, third person
- **Explain level:** Explain concepts from the ground up — user is a beginner in ML
- **AI use policy:** AI writing assistance is permitted. Explicit supervisor approval has been granted for all aspects including writing. All AI-assisted writing must be reviewed, understood, and owned by the student.

---

## 7. Chapter Structure

| Chapter | File | Word target |
|---------|------|-------------|
| Introduction | writing/ch1_introduction.md | 1000 |
| Literature Review | writing/ch2_literature.md | 2500 |
| Methodology | writing/ch3_methodology.md | 2500 |
| Results | writing/ch4_results.md | 2000 |
| Conclusion | writing/ch5_conclusion.md | 800 |

**Total word target:** 8800
**Words per page estimate:** 250

---

## 8. Project Folder Structure

```
thesis-project/
├── CLAUDE.md
├── .claude/commands/
├── docs/
├── papers/
│   └── notes/
├── data/
│   ├── raw/
│   └── processed/
├── code/
├── output/
│   ├── figures/
│   └── tables/
├── writing/
└── notes/
```

---

## 9. File Paths (used by skills)

| Purpose | Path |
|---------|------|
| Chapter drafts | writing/ |
| References file | papers/references.md |
| Paper notes | papers/notes/ |
| Session state | notes/ralph-state.md |
| Course documents | docs/ |

---

## 10. Google Docs Integration (optional)

### Document ID Reference

| Doc | Google Doc ID |
|-----|--------------|
| Main Thesis (Full) | `1J_WWyHfpNvX47IMdxLK6Hg9AMwxeV7WZDiMrcWd7LsE` |
| Progress Tracker | `1NlmAdbhz46KnCEEofzJHO9G-4_9G8KnW__CxnLJ7P7Y` |
| Group Thesis | `1oN-MZ1vfgBm7ysN54WnkI2jnGJRAVJxNa-5nzbaK_Os` |

### Overwrite Procedure (3 steps)

(Same as in the template — get, replace, verify)

---

## 11. Skills Reference

(Same table as in template — all 17 skills)
