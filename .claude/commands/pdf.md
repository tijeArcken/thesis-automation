# Academic PDF Extractor (`/pdf`)

Extract structured content from an academic paper PDF and save a reading note.

## Usage
```
/pdf [PDF file path]
```

**Example:**
- `/pdf papers/Author_2022_title.pdf`

---

## Instructions

You are an academic paper extraction assistant. Your job is to read a PDF and produce a structured summary that feeds directly into `/rewrite-literature`, `/fact-check`, and `/write-section`.

**Read CLAUDE.md before proceeding** to determine:
- The thesis topic and research question (section 1)
- Research focus areas (section 4)
- The paper notes directory (section 9 — default: `papers/notes/`)
- The references file path (section 9 — default: `papers/references.md`)

### Step 1 — Read the PDF

Use the Read tool to read the file at the provided path. If it is not found, tell the user and stop.

### Step 2 — Extract structured content

Extract the following sections. If a section is not present in the paper, write "Not reported" rather than guessing.

| Section | What to extract |
|---------|-----------------|
| **Metadata** | Authors, year, journal, DOI |
| **Research question** | The paper's central question or objective (1-2 sentences) |
| **Methods** | Analytical/empirical methods used |
| **Data** | Dataset name(s), frequency, country coverage, time period, key variables |
| **Key findings** | 3-5 bullet points: the most important empirical results |
| **Limitations** | What the authors acknowledge as weaknesses |
| **Quotes worth citing** | 2-3 verbatim quotes useful for the thesis (with page numbers if visible) |
| **Thesis relevance** | How this paper connects to the research question and focus areas from CLAUDE.md |

### Step 3 — Determine output filename

Strip the PDF filename of its extension and use it as the note filename:
- Input: `papers/Author_2022_title.pdf`
- Output: `papers/notes/Author_2022_title.md`

Use the paper notes directory from CLAUDE.md section 9.

### Step 4 — Write the structured note

Save the note using this template:

```markdown
# [Full Paper Title]

> **Authors:** [Names]
> **Year:** [Year]
> **Journal:** [Journal]
> **DOI:** [DOI or "Not reported"]
> **Extracted:** [today's date]

---

## Research Question

[1-2 sentences]

---

## Methods

[List methods used]

---

## Data

- **Dataset:** [name]
- **Frequency:** [annual / quarterly / monthly]
- **Coverage:** [countries/regions]
- **Period:** [years]
- **Key variables:** [list]

---

## Key Findings

- [Finding 1]
- [Finding 2]
- [Finding 3]
- [Finding 4 if applicable]
- [Finding 5 if applicable]

---

## Limitations

[What the authors acknowledge]

---

## Quotes Worth Citing

> "[Quote 1]" (p. X)

> "[Quote 2]" (p. X)

> "[Quote 3]" (p. X)

---

## Thesis Relevance

**Focus area relevance:** [Which focus area(s) from CLAUDE.md section 4 this connects to]

[2-3 sentences on how this paper connects to the thesis research question, methods, or data]

---

## Citation

[Full citation in the style specified in CLAUDE.md section 6]
```

### Step 5 — Auto-register citation

After writing the note, automatically run the `/cite` logic for this paper:
- Extract the citation entry
- Check if the references file exists
- If the paper is not already listed, append it

### Step 6 — Report back

Tell the user:
- Note saved to: `[path]`
- Citation added to: references file (or "already existed")
- Focus area relevance: [which focus areas it connects to]
- Strongest finding: [one sentence]
- Tip: "Use `/fact-check [claim]` to verify any specific assertion from this paper."

---

## Rules

- Never fabricate content. If something is not in the PDF, write "Not reported."
- Quotes must be verbatim. Never paraphrase and present as a quote.
- Thesis relevance must connect specifically to the research question and focus areas from CLAUDE.md.
- Keep key findings factual and precise — no editorializing.
- If the PDF cannot be read (encrypted, image-based), tell the user and suggest they copy-paste the abstract manually.
