Draft or rewrite the literature review section using a multi-agent synthesis process.

## Usage
`/rewrite-literature`

## Context

Read the project context from `CLAUDE.md` at the repository root. The following sections are relevant:
- **Section 4 (Research Question)** — core RQ and focus areas
- **Section 5 (Methods)** — methods in use
- **Section 7 (Starting Literature)** — canonical papers

## Process

### Agent 1 — Paper Inventory
- Scan `papers/` and `papers/notes/` for all papers and reading notes
- Build a structured inventory: author(s), year, method, key finding, relevance to research focus areas
- Flag any obvious gaps (e.g., missing a key benchmark paper from CLAUDE.md Section 7)

### Agent 2 — Theme Mapper
- Group papers into 3–4 coherent themes. Derive themes from the papers available — typical patterns include:
  1. **Classical/traditional approaches** — established methods and foundational work
  2. **Advanced methods in the domain** — newer techniques applied to the research area
  3. **Empirical evidence** — studies that test hypotheses similar to the thesis RQ
  4. **The specific gap** — papers closest to what the thesis addresses
- Output: theme map with papers assigned to each theme

### Agent 3 — Synthesizer (Writer)
- Draft the literature review section theme by theme
- For each paper: 1–2 sentences on contribution + method + finding
- End each theme subsection with a synthesis sentence identifying what the theme collectively shows
- Final paragraph: identify the research gap that the thesis fills

### Agent 4 — Style Reviewer
- Check academic register, transitions between themes, citation format consistency
- Flag: passive voice overuse, vague claims without citations, paragraph length issues
- Return revised version with a short improvement log

### Agent 5 — Humanize (automatic, never skip)
Apply the full humanizer rewrite as defined in `.claude/commands/humanize.md` (3 passes: identify → rewrite → audit). Remove all AI-isms while preserving academic register: passive voice, calibrated hedges, domain vocabulary, and formal transitions are all preserved. Strip significance inflation, filler phrases, vague attributions, em dash clusters, rule-of-three lists, generic conclusions, and overused AI vocabulary. Return the clean final version with a brief change log.

## Output Format
Full draft literature review in academic English, organized by theme, with [CITATION NEEDED] flags for any claims needing a source that could not be found in `papers/`.
