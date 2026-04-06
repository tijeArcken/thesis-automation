Proofread a thesis section or file for grammar, style, clarity, and academic register.

## Usage
`/proofread [section or file path]`

Examples:
- `/proofread introduction` — proofread the introduction draft
- `/proofread writing/ch2_literature.md` — proofread a specific file
- `/proofread` — proofread whatever is in `writing/` (most recent file)

## What to Check

### Grammar & Mechanics
- Subject-verb agreement
- Article usage (a/an/the — common issue for non-native writers)
- Tense consistency (past for empirical findings, present for established facts)
- Comma splices, run-on sentences, sentence fragments

### Academic Style
- Hedged language: "suggests" not "proves", "indicates" not "shows definitively"
- Avoid colloquialisms, contractions, first person singular unless justified
- Passive voice: flag overuse, but also flag excessive nominalization
- Avoid vague quantifiers: "many studies", "some researchers" — replace with citations or specifics

### Clarity & Structure
- Each paragraph should have one clear topic sentence
- Transitions between paragraphs and sections
- Avoid burying the main point at the end of a paragraph
- Long sentences (>40 words): flag for restructuring

### Citation & Formatting
- Every empirical claim must have a citation
- Flag [CITATION NEEDED] where a claim is made without support
- Check in-text citation format consistency (match the style specified in CLAUDE.md section 6)

## Output Format

Return issues in three severity tiers:

**HIGH** (must fix before submission)
- [Line/paragraph reference]: Issue description + suggested fix

**MEDIUM** (should fix, affects grade)
- [Line/paragraph reference]: Issue description + suggested fix

**LOW** (polish, nice to have)
- [Line/paragraph reference]: Issue description + suggested fix

Then provide a clean revised version of the text with all HIGH and MEDIUM issues corrected.

## Humanize Pass (automatic, never skip)

After producing the corrected version, apply the full humanizer rewrite as defined in `.claude/commands/humanize.md` (3 passes: identify, rewrite, audit). Remove all AI-isms while preserving academic register: passive voice, calibrated hedges, domain vocabulary, and formal transitions are all preserved. Strip significance inflation, filler phrases, vague attributions, em dash clusters, rule-of-three lists, generic conclusions, and overused AI vocabulary. The final output returned to the user must be the humanized version.
