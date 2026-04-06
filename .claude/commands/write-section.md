Draft a thesis section using a structured multi-pass process: outline, draft, style review.

## Usage
`/write-section [section]`

Sections: `introduction`, `literature`, `methodology`, `results`, `discussion`, `conclusion`, `abstract`

## Context

**Read CLAUDE.md before proceeding** to determine:
- Thesis topic, research question, and focus areas (sections 1 and 4)
- Methods and data sources (section 4)
- Starting literature (section 5)
- Writing style and language (section 6)
- Chapter structure and word targets (section 7)
- AI use policy (section 6 — check before writing)

## Process

### Pass 1 — Outline
- Read CLAUDE.md and any relevant files in the papers directory, `writing/`, `notes/`, `output/`
- Produce a structured outline with section headers and bullet-point content plan
- Ask the user to confirm or adjust the outline before proceeding

### Pass 2 — Draft
- Write a full academic draft based on the confirmed outline
- Use hedged academic language ("suggests", "indicates", "may")
- Cite papers from the papers directory where relevant; flag gaps with [CITATION NEEDED]
- Integrate empirical results from `output/` if they exist

### Pass 3 — Style Review
- Check: clarity, transitions, academic register, paragraph flow, argument coherence
- Produce a revised version with inline improvements noted

### Pass 4 — Humanize (automatic, never skip)
Apply the full humanizer rewrite as defined in `.claude/commands/humanize.md` (3 passes: identify, rewrite, audit). Remove all AI-isms while preserving academic register: passive voice, calibrated hedges, domain vocabulary, and formal transitions are all preserved. Strip significance inflation, filler phrases, vague attributions, em dash clusters, rule-of-three lists, generic conclusions, and overused AI vocabulary. Return the clean final version with a brief change log.

## Section-Specific Guidance

### introduction
- Motivate the research question with domain-specific evidence
- State the research gap: what existing methods or approaches miss
- Outline paper structure in the final paragraph

### literature
- Organize by theme, not chronologically — derive themes from the research focus areas in CLAUDE.md section 4
- For each paper: contribution, method, finding, limitation
- End with a synthesis paragraph identifying the research gap that the thesis fills

### methodology
- Describe the data with summary statistics reference
- Explain each method conceptually before giving the specification
- Justify method choices relative to the research question
- Include model evaluation strategy (train/test split, cross-validation, metrics)

### results
- Present performance metrics clearly (tables, figures)
- Compare methods to a benchmark
- Discuss substantive significance, not just statistical significance

### discussion
- Interpret the results in light of the literature
- Address limitations: data coverage, method constraints, potential biases
- Connect findings back to the research focus areas from CLAUDE.md section 4

### conclusion
- Restate research question and main finding
- Policy or practical implications (if any)
- Future research directions

### abstract
- 150-250 words
- Structure: motivation, question, data, methods, key finding, implication
