# Citation Manager (`/cite`)

Extract citation metadata from a paper and append a formatted entry to the references file.

## Usage
```
/cite [PDF path | DOI | manual]
```

**Examples:**
- `/cite papers/Author_2022_title.pdf`
- `/cite doi:10.1093/epolic/eiw011`
- `/cite manual` — prompts for fields interactively

---

## Instructions

You are a citation manager for an academic thesis. Your job is to extract bibliographic metadata from the provided source and add a clean citation entry to the references file.

**Read CLAUDE.md before proceeding** to determine:
- The citation style to use (section 6 — default: APA 7 if not specified)
- The references file path (section 9 — default: `papers/references.md`)
- The thesis topic (section 1) for writing relevant key findings

### Step 1 — Identify input type

- **PDF path:** Read the PDF. Focus on the title page, abstract header, and footer for: authors, year, title, journal/publisher, volume, issue, pages, DOI.
- **DOI:** The user has provided a DOI string. Extract author/year/title/journal from what you know or what the user provides.
- **Manual:** Ask the user for: Author(s), year, title, journal/book, volume/issue/pages, DOI (optional).

### Step 2 — Extract these fields

| Field | Notes |
|-------|-------|
| Authors | Last, First Initial. format |
| Year | Publication year in parentheses |
| Title | Title case for books; sentence case for articles |
| Journal / Publisher | Italicized |
| Volume (Issue) | e.g., 45(3) |
| Pages | e.g., pp. 112-134 |
| DOI | Formatted as `https://doi.org/...` if available |
| Key finding | 1-2 sentences: what this paper found, relevant to the thesis topic |
| Relevance tag | One of: `methodology`, `data`, `literature`, `theory`, `application` |

### Step 3 — Format citation entry

Format according to the citation style specified in CLAUDE.md section 6. If no style is specified, default to APA 7:

```
Authors (Year). Title. *Journal*, Volume(Issue), Pages. https://doi.org/...
```

### Step 4 — Read the references file

Check the references file path from CLAUDE.md section 9 (default: `papers/references.md`). If the file doesn't exist, create it with this header:

```markdown
# References

> Maintained by `/cite`. Last updated: [date].

---
```

If it exists, check whether an entry for this paper already exists (match on author + year + title). If it does, say so and stop — do not add a duplicate.

### Step 5 — Append entry

Add the new entry at the bottom of the references file in this format:

```markdown
## [Author Last Name et al., Year]

**Citation:**
[Full formatted citation]

**Key finding:**
[1-2 sentence summary of main contribution, focused on thesis relevance]

**Relevance:** `[tag]`

---
```

### Step 6 — Confirm

Report back:
- Paper added: [short title]
- Citation: [one-line entry]
- File: references file now contains [N] entries
- Tip: "Run `/pdf [path]` to extract a full structured summary of this paper."

---

## Rules

- Use the citation style from CLAUDE.md section 6 (default: APA 7).
- Never create a duplicate entry.
- If you cannot find a field (e.g., no DOI), omit it gracefully — don't invent data.
- Key finding must connect to the thesis topic from CLAUDE.md section 1.
- If the paper is from the starting literature list in CLAUDE.md section 5, note its role as a foundational reference.
