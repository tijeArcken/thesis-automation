Draft or rewrite the literature review section using a multi-agent synthesis process.

## Usage
`/rewrite-literature`

## Context

**Read CLAUDE.md before proceeding** to determine:
- Thesis topic and research question (section 1)
- Research focus areas (section 4)
- Starting literature (section 5)
- Writing style (section 6)
- AI use policy (section 6)
- Papers directory and references file (section 9)

## Process

### Agent 1 — Paper Inventory
- Scan the papers directory (from CLAUDE.md section 9) for all papers and reading notes
- Build a structured inventory: author(s), year, method, key finding, relevance to the research focus areas from CLAUDE.md section 4
- Flag any obvious gaps (e.g., missing a key paper from the starting literature in CLAUDE.md section 5)

### Agent 2 — Theme Mapper
- Group papers into 3-4 coherent themes
- Derive themes dynamically from the papers found and the research focus areas — do NOT use a hardcoded theme structure
- Output: theme map with papers assigned to each theme

### Agent 3 — Synthesizer (Writer)
- Draft the literature review section theme by theme
- For each paper: 1-2 sentences on contribution + method + finding
- End each theme subsection with a synthesis sentence identifying what the theme collectively shows
- Final paragraph: identify the research gap that the thesis fills (connecting to the RQ from CLAUDE.md section 1)

### Agent 4 — Style Reviewer
- Check academic register, transitions between themes, citation format consistency
- Flag: passive voice overuse, vague claims without citations, paragraph length issues
- Return revised version with a short improvement log

### Agent 5 — Humanize (automatic, never skip)
Apply the full humanizer rewrite as defined in `.claude/commands/humanize.md` (3 passes: identify, rewrite, audit). Remove all AI-isms while preserving academic register: passive voice, calibrated hedges, domain vocabulary, and formal transitions are all preserved. Strip significance inflation, filler phrases, vague attributions, em dash clusters, rule-of-three lists, generic conclusions, and overused AI vocabulary. Return the clean final version with a brief change log.

## Output Format
Full draft literature review in academic prose, organized by theme, with [CITATION NEEDED] flags for any claims needing a source that could not be found in the papers directory.
