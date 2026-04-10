# Thesis Progress Tracker (`/wordcount`)

Count words across all thesis chapter files and report progress toward submission targets.

## Usage
```
/wordcount
```

No arguments needed. Automatically scans `writing/`.

---

## Instructions

You are a thesis progress tracker. Read the project context from `CLAUDE.md` at the repository root for chapter files, word targets, and deadlines.

### Step 1 — Read chapter files

Read the thesis structure from **CLAUDE.md Section 10** to determine:
- Which chapter files to scan (file paths and chapter names)
- The word count targets (minimum, target, maximum) for each chapter

If CLAUDE.md Section 10 is not filled in, fall back to scanning all `.md` files in `writing/` and use these default targets:

| Chapter | Min | Target | Max |
|---------|-----|--------|-----|
| Introduction | 600 | 1,000 | 1,500 |
| Literature Review | 1,500 | 2,500 | 3,500 |
| Methodology | 1,500 | 2,500 | 3,500 |
| Results | 1,500 | 2,000 | 3,000 |
| Conclusion | 500 | 800 | 1,200 |
| **Total** | **5,600** | **8,800** | **12,700** |

### Step 2 — Count words per file

For each file:
- Count total words (split on whitespace)
- Subtract words in markdown formatting lines (lines starting with `#`, `|`, `---`, `` ` ``)
- This gives a rough "prose word count"

Report both raw and prose counts if they differ significantly (>10%).

### Step 3 — Calculate page estimates

Use standard academic page estimates:
- **~250 words per page** (double-spaced, 12pt, standard margins)

### Step 4 — Format the report

Read deadlines from **CLAUDE.md Section 2**.

Output this report:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  THESIS — WORD COUNT REPORT
  [Today's date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CHAPTER BREAKDOWN
─────────────────────────────────────
Ch. 1  [Name]        [N] words   (~[N] pages)   [STATUS]
Ch. 2  [Name]        [N] words   (~[N] pages)   [STATUS]
Ch. 3  [Name]        [N] words   (~[N] pages)   [STATUS]
Ch. 4  [Name]        [N] words   (~[N] pages)   [STATUS]
Ch. 5  [Name]        [N] words   (~[N] pages)   [STATUS]
─────────────────────────────────────
TOTAL                 [N] words   (~[N] pages)

PROGRESS TOWARD TARGET ([target] words)
[████████░░░░░░░░░░░░] XX%

UPCOMING DEADLINES
─────────────────────────────────────
[Read from CLAUDE.md Section 2 — show the next 2–3 upcoming deadlines]

CHAPTER STATUS
─────────────────────────────────────
[List each chapter with one of:]
  ✓  On track (≥ minimum)
  ⚠  Needs work (below minimum)
  ○  Not started (0 words)

RECOMMENDATIONS
─────────────────────────────────────
[1–3 concrete recommendations based on the word counts and the nearest deadline]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**STATUS codes:**
- `✓ On track` — word count ≥ minimum target
- `⚠ Needs work` — word count > 0 but < minimum target
- `○ Not started` — file is empty or does not exist

### Step 5 — Recommendations

Based on the nearest upcoming deadline (from CLAUDE.md Section 2):

- Flag any chapter below minimum. Recommend writing order.
- If all chapters are on track, say so and give a brief encouragement.
- Keep recommendations concrete and actionable (e.g., "Write 400 more words in Ch. 2 to reach the minimum").

---

## Rules

- Count prose words only — exclude markdown headers, table lines, and code blocks.
- Never fabricate word counts. Read the actual files.
- If a file doesn't exist, count it as 0 and mark as "Not started."
- Always show the nearest deadline prominently.
