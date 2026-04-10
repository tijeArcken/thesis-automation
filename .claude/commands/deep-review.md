# Three-Agent Parallel Quality Review (`/deep-review`)

Run three parallel review agents on a thesis chapter — language, citation, and argumentation — and synthesize into a unified report.

## Usage
```
/deep-review [file path or chapter name]
```

**Examples:**
- `/deep-review writing/ch2_literature.md`
- `/deep-review ch3` — resolves to the methodology chapter in `writing/`
- `/deep-review writing/ch1_introduction.md`

---

## Instructions

You are a three-agent quality reviewer for an academic thesis. Read the project context from `CLAUDE.md` (research question, methods, starting literature) before starting. Your job is to simulate three expert reviewers working in parallel, each evaluating the chapter from a different angle, then synthesize their findings into a single actionable report.

### Step 1 — Resolve the file path

If the user provides:
- A full path: use it directly
- A chapter name or abbreviation (e.g., `ch2`, `literature`, `methodology`): map to the corresponding file in `writing/`

Read the target file. If it doesn't exist or is empty (<100 words), stop and tell the user.

Also read `papers/references.md` if it exists — the Citation Agent will use it.

---

### Step 2 — Run three agents IN PARALLEL

Evaluate the text from all three perspectives simultaneously. Do NOT do them sequentially — think through all three dimensions at once, then write up each agent's findings.

---

#### AGENT 1: Language Agent
**Role:** Senior academic editor. Focus: grammar, style, clarity, register.

Evaluate:
- **Grammar & mechanics:** Subject-verb agreement, tense consistency, punctuation, sentence structure
- **Academic register:** Appropriate formality, no contractions, no colloquialisms, precise vocabulary
- **Clarity:** Are sentences too long or convoluted? Is the meaning always clear on first read?
- **Word choice:** Vague terms ("big", "many", "things"), overused hedges ("very", "quite"), redundant phrases
- **Flow:** Does each paragraph have a clear topic sentence? Are transitions between paragraphs smooth?
- **Sentence variety:** Mix of sentence lengths; no paragraph that is one sentence or ten sentences

For each issue, quote the problematic passage and suggest a specific fix.

---

#### AGENT 2: Citation Agent
**Role:** Academic integrity reviewer. Focus: evidence and attribution.

Evaluate:
- **Unsupported claims:** Empirical assertions without a citation
- **Over-citation:** Places where too many citations are stacked without explanation
- **Citation quality:** Are the cited papers actually strong sources for the claim being made?
- **Missing citations:** Key claims in the thesis domain that should cite the canonical literature (refer to CLAUDE.md Section 7 for the starting literature list)
- **Cross-check with `papers/references.md`:** Are all cited papers actually in the bibliography?
- **Quote integrity:** If any quotes are used, are they plausibly verbatim (not paraphrased and presented as quotes)?

For each issue, quote the passage and specify what citation is needed or what the citation problem is.

---

#### AGENT 3: Argumentation Agent
**Role:** Thesis supervisor (skeptical). Focus: logical structure and coherence.

Evaluate:
- **Logical flow:** Do paragraphs build on each other? Is there a clear thread through the section?
- **Topic sentences:** Does each paragraph start with a clear claim? Is the claim then defended?
- **Evidence → Conclusion:** When evidence is cited, does the conclusion actually follow from it?
- **Non-sequiturs:** Are there jumps in logic where the reader would ask "wait, why does that follow?"
- **Contribution clarity:** Is it clear what this section adds to the argument? Does it earn its place?
- **Scope creep:** Are there tangents or off-topic paragraphs that should be cut or moved?
- **Internal consistency:** Do claims in this chapter contradict anything that would appear in other chapters?
- **Strength of thesis:** For the introduction — is the research question stated clearly? For the literature — is there a synthesis, not just a list? For methodology — is the choice of method justified?

For each issue, describe the logical problem and suggest a structural fix.

---

### Step 3 — Score each dimension

Score each agent's assessment on a 1–10 scale:
- **10** — publication-ready; no issues
- **8–9** — minor fixes only
- **6–7** — moderate issues; needs revision
- **4–5** — significant problems; substantial rewrite needed
- **1–3** — major structural or content problems

---

### Step 4 — Synthesize the report

Output a unified review in this format:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  DEEP REVIEW — [Chapter Name]
  [Today's date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

OVERALL SCORES
─────────────────────────────────────────────────────────
  Language / Style        [X/10]
  Citation / Evidence     [X/10]
  Argumentation / Logic   [X/10]
  ─────────────
  Composite Score         [X/10]

SUMMARY
─────────────────────────────────────────────────────────
[2–3 sentence overall assessment: what the chapter does well, and what is the most important thing to fix before submission]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AGENT 1 — LANGUAGE REVIEW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[HIGH] Issues — must fix before submission
──────────────────────────────────────────
[Issue 1]
> "[quoted passage]"
Fix: [specific suggestion]

[MEDIUM] Issues — should fix
──────────────────────────────────────────
[Issue 2]
> "[quoted passage]"
Fix: [suggestion]

[LOW] Polish items
──────────────────────────────────────────
[Issue 3]
Fix: [suggestion]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AGENT 2 — CITATION REVIEW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[HIGH] Issues
──────────────────────────────────────────
[Issue 1 — unsupported claim, wrong source, etc.]
> "[quoted passage]"
Fix: [add citation X / replace citation Y / remove unsupported claim]

[MEDIUM] Issues
──────────────────────────────────────────
[...]

[LOW] Polish items
──────────────────────────────────────────
[...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
AGENT 3 — ARGUMENTATION REVIEW
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[HIGH] Issues
──────────────────────────────────────────
[Issue 1 — logical gap, missing link, non-sequitur]
> "[quoted passage or paragraph reference]"
Fix: [structural suggestion]

[MEDIUM] Issues
──────────────────────────────────────────
[...]

[LOW] Polish items
──────────────────────────────────────────
[...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ACTION PLAN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Priority fixes (do these first):
1. [Most important HIGH issue from any agent]
2. [Second most important]
3. [Third]

After fixing: run `/deep-review [file]` again to re-evaluate.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

HUMANIZE PASS (automatic — runs after action plan)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Apply the full humanizer rewrite as defined in `.claude/commands/humanize.md`
(3 passes: identify → rewrite → audit). Remove all AI-isms while preserving
academic register. If the chapter had HIGH language issues, output the
humanized version of the full chapter. If only MEDIUM/LOW issues, output
humanized versions of only the flagged passages.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Rules

- Issues must be quoted from the actual text — never fabricate example passages.
- If an issue is truly not present (e.g., no citation problems), write "No issues found" for that category — don't invent problems.
- HIGH = would cause a supervisor to reject the draft or request major revision
- MEDIUM = noticeable problem that weakens the work but doesn't block submission
- LOW = polish items: minor style, word choice, or formatting
- Composite score = average of the three agent scores
- If the chapter is very short (<300 words), note this prominently: "Chapter too short to review meaningfully — write more content first."
- The Action Plan must prioritize across all three agents — don't just list every HIGH issue.
