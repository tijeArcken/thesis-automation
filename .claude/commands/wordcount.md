# Thesis Progress Tracker (`/wordcount`)

Count words across all thesis chapter files and report progress toward submission targets.

## Usage
```
/wordcount
```

No arguments needed. Automatically scans the writing directory.

---

## Instructions

You are a thesis progress tracker. Your job is to count words, estimate pages, and flag chapters that need attention before the deadlines.

**Read CLAUDE.md before proceeding** to determine:
- The chapter structure with file paths and word targets (section 7)
- The total word target and words-per-page estimate (section 7)
- The key deadlines (section 2)
- The thesis topic for the report header (section 1)

### Step 1 — Read all chapter files

Read each file listed in the chapter structure table in CLAUDE.md section 7. Skip any file that does not exist.

Also check for any other `.md` files in the writing directory that might contain thesis content.

### Step 2 — Count words per file

For each file:
- Count total words (split on whitespace)
- Subtract words in markdown formatting lines (lines starting with `#`, `|`, `---`, backticks)
- This gives a rough "prose word count"

Report both raw and prose counts if they differ significantly (>10%).

### Step 3 — Calculate page estimates

Use the words-per-page estimate from CLAUDE.md section 7 (default: 250 words per page if not specified).

### Step 4 — Compare against targets

Use the per-chapter word targets from CLAUDE.md section 7. For each chapter, determine status:
- On track: word count >= target
- Needs work: word count > 0 but < target
- Not started: file is empty or does not exist

### Step 5 — Format the report

Output this report:

```
THESIS — WORD COUNT REPORT
[Today's date]

CHAPTER BREAKDOWN
Ch. 1  [Chapter Name]     [N] words   (~[N] pages)   [STATUS]
Ch. 2  [Chapter Name]     [N] words   (~[N] pages)   [STATUS]
Ch. 3  [Chapter Name]     [N] words   (~[N] pages)   [STATUS]
...
TOTAL                      [N] words   (~[N] pages)

PROGRESS TOWARD TARGET ([total target] words)
[progress bar] XX%

UPCOMING DEADLINES
[List deadlines from CLAUDE.md section 2, sorted by date]

CHAPTER STATUS
[List each chapter with status icon]
  On track (>= target)
  Needs work (below target)
  Not started (0 words)

RECOMMENDATIONS
[1-3 concrete recommendations based on word counts and nearest deadline]
```

### Step 6 — Recommendations

Based on the nearest upcoming deadline from CLAUDE.md section 2 (check against today's date):

- Flag any chapter below its target
- Recommend which chapters to prioritize based on deadline proximity
- Suggest concrete actions (e.g., "Write 400 more words in Ch. 2 to reach the target")

If all chapters are on track, say so and give a brief encouragement.

---

## Rules

- Count prose words only — exclude markdown headers, table lines, and code blocks.
- Never fabricate word counts. Read the actual files.
- If a file doesn't exist, count it as 0 and mark as "Not started."
- Keep recommendations concrete and actionable.
- Always show the nearest deadline prominently.
