Search for, annotate, and synthesize academic literature on a given topic relevant to the thesis.

## Usage
`/literature-review [topic]`

Examples:
- `/literature-review [your search topic]`
- `/literature-review [method name] forecasting`
- `/literature-review [dependent variable] prediction methods`

## Context

Read the project context from `CLAUDE.md` at the repository root. The following sections are relevant:
- **Section 4 (Research Question)** — core RQ and focus areas
- **Section 5 (Methods)** — methods of interest
- **Section 6 (Data Sources)** — key datasets
- **Section 7 (Starting Literature)** — papers to cross-reference

All project-specific details (topic, methods, data, key papers) are defined there.

## Process

### Step 1 — Scope the Topic
- Clarify the specific question the literature should answer
- Identify 3–5 search terms to use

### Step 2 — Find & Annotate Papers
For each paper found in `papers/` or identified via web search, produce:

```
**[Author(s) (Year)] — "Title"**
- Method: [what technique/approach they use]
- Data: [sample, countries, time period]
- Key finding: [one clear sentence]
- Evidence tier: [A = top journal / B = good journal / C = working paper / D = policy report]
- Relevance to thesis: [HIGH / MEDIUM / LOW] — [one sentence why]
- Focus area: [which focus area from CLAUDE.md Section 4 this connects to, or "background"]
```

### Step 3 — Synthesize
- Group papers by theme or finding
- Write a 3–5 sentence synthesis: what the body of evidence collectively shows
- Identify the most important gap: what is still unresolved that the thesis could address

### Step 4 — Recommend
- Suggest which papers should definitely be cited in the thesis
- Flag any contradictions in the literature that are worth discussing
- Recommend any additional searches to fill gaps

## Key Papers to Cross-Reference

Refer to the starting literature listed in CLAUDE.md Section 7. These are the canonical papers for this thesis and should be cross-referenced when relevant.
