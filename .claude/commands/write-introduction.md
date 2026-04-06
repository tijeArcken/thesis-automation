# Specialized Introduction Writer (`/write-introduction`)

Draft or outline the thesis introduction using the Jesse Shapiro / Keith Head academic introduction framework.

## Usage
```
/write-introduction [outline | draft | both]
```

- `outline` — produce a structured outline with bullet points per section (default if no argument)
- `draft` — produce a full prose draft
- `both` — outline first, then expand to draft

---

## Instructions

You are drafting the Introduction chapter for an academic thesis. The introduction follows the Jesse Shapiro / Keith Head framework for academic economics papers: it opens with a hook, states the question clearly, leads with main findings early, situates the paper in the literature, states the contribution, and closes with a roadmap.

> **Note:** If your discipline uses a different introduction framework, describe it in CLAUDE.md section 6 and this skill will adapt. The Shapiro/Head framework is the default and works well for empirical social science theses.

**Read CLAUDE.md before proceeding** to determine:
- Research question (section 1)
- Thesis topic (section 1)
- Research focus areas (section 4)
- Methods and data sources (section 4)
- Starting literature (section 5)
- Introduction word target from the chapter structure (section 7)
- Introduction file path from the chapter structure (section 7)

---

### Step 1 — Read existing chapter files

Read these files before writing:
- The introduction file from CLAUDE.md section 7 — check if a draft already exists
- Any notes files in `writing/` — check for notes on the introduction
- The references file from CLAUDE.md section 9 — check what literature is available to cite

If the introduction file already has substantial content (>300 words), present it first and ask whether to revise it or start fresh.

### Step 2 — Follow the 6-part framework

**Part 1 — Hook (2-3 paragraphs, ~200 words)**
- Open with a striking fact relevant to the thesis domain
- Connect to broader relevance: Why does this topic matter?
- Narrow to the specific gap: What do existing approaches miss?
- Do NOT open with "This paper studies..." — open with context and stakes

**Part 2 — Research Question (1 paragraph, ~80 words)**
- State the RQ explicitly and precisely (from CLAUDE.md section 1)
- Frame it as empirical and specific — reference the data and scope
- Make it clear what the thesis tests or investigates

**Part 3 — Approach & Main Findings (~150 words)**
- Lead with your strongest result (even if the analysis isn't done yet — write this as a placeholder with [RESULT TBD] if needed)
- Briefly describe the data and methods used
- Summarize what the evidence shows
- The Shapiro rule: "Don't bury the punchline." Put the finding here, not in the conclusion.

**Part 4 — Antecedents / Related Literature (2-3 paragraphs, ~200 words)**
- Cite 3-5 key papers from CLAUDE.md section 5 and explain how this work relates to them
- Use comparison patterns: "Unlike [X], who..., this paper..." or "Building on [Y]..."
- Cite only papers available in the references file unless you know the reference well

**Part 5 — Contribution (1 paragraph, ~100 words)**
- State clearly what this thesis adds beyond existing work
- Be honest about scope — frame the contribution appropriately for the degree level in CLAUDE.md section 1
- Frame as: "This paper contributes to the literature by..."

**Part 6 — Roadmap (1 paragraph, ~80 words)**
- Standard structure: "The remainder of this paper is organized as follows. Section 2 reviews the literature... Section 3 describes the data and methodology..."
- Derive the section names from the chapter structure in CLAUDE.md section 7
- Keep it factual. One sentence per chapter.

---

### Step 3 — Produce output

**If `outline` mode:**
Output a bullet-point outline for all 6 parts, with placeholder text showing what will go where. Show the word count target per section.

**If `draft` mode:**
Output a full prose draft. Use academic register: formal but readable, precise language. Aim for the word target from CLAUDE.md section 7.

**If `both` mode:**
Output the outline first, then say "Expanding to draft..." and produce the full prose draft.

---

### Step 4 — Save output

- Save/overwrite the introduction file with the output
- If saving a draft, prepend this header:
```markdown
# [Chapter title from CLAUDE.md section 7]

> **Status:** Draft [v1] — `/write-introduction draft` — [date]
> **Word count:** [N] words
> **Next step:** Run `/proofread [file]` or `/deep-review [file]`

---
```

### Step 5 — Humanize (automatic, never skip)
Before saving or returning any prose output, apply the full humanizer rewrite as defined in `.claude/commands/humanize.md` (3 passes: identify, rewrite, audit). Remove all AI-isms while preserving academic register. Save the humanized version.

### Step 6 — Report back

Tell the user:
- Mode: [outline / draft]
- Saved to: [file path]
- Word count: [N]
- Weakest section: [name the part that has the most [TBD] placeholders or needs the most real content]
- Next step: suggest `/deep-review [file]` to check argumentation, or `/wordcount` to see overall progress

---

## Rules

- Never invent empirical results. If the analysis hasn't been run yet, use `[RESULT TBD]` as a placeholder.
- Always lead with the punchline in Part 3 — the Shapiro rule is non-negotiable.
- The hook must NOT start with "This paper..." or "In recent years..." — these are cliches.
- Cite only real papers. If a citation is needed and isn't in the references file, note it as `[CITATION NEEDED]`.
- Academic register: no contractions, no first-person (unless the thesis explicitly allows it), precise and measured language.
- If the user says `outline`, do NOT write a full draft — give bullet points only.
