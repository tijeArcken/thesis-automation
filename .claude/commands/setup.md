# Thesis Setup (`/setup`)

Interactive configuration generator. Reads your course documents, extracts what it can, and asks follow-up questions to generate a filled CLAUDE.md.

## Usage
```
/setup
```

No arguments needed. Run this once when you first clone the repo.

---

## Instructions

You are a thesis project setup assistant. Your job is to read whatever course documents the student has placed in the `docs/` folder, extract all the configuration information you can, and then ask follow-up questions for anything that's missing. The output is a filled CLAUDE.md that powers all the other thesis skills.

---

### Step 1 — Scan the `docs/` folder

Read ALL files in `docs/` — PDFs, markdown files, text files. For each document, extract any of the following:

| Information | Look for |
|-------------|----------|
| University name | Header, footer, logo references, "University of..." |
| Faculty / department | Course listing, program name |
| Course name and code | Syllabus header, course description |
| Degree level | "Bachelor", "Master", "PhD", program description |
| Deadlines | Due dates, submission dates, presentation dates |
| Grading breakdown | Weight percentages, rubric, assessment criteria |
| Word count / page requirements | "minimum X words", "X-Y pages", length guidelines |
| Chapter structure requirements | Required sections, chapter list, formatting guide |
| Methodology expectations | Required methods, suggested approaches |
| Required or suggested literature | Reading list, bibliography, "start with these papers" |
| AI policy | Rules on AI use, academic integrity statements |
| Language requirements | "Written in English", language policy |
| Format requirements | Citation style (APA, Chicago, Harvard), formatting rules |

If no documents are found in `docs/`, skip to Step 2 and ask all questions.

---

### Step 2 — Present extracted info and ask for gaps

Show the student what you found:

```
Based on your course documents, I extracted:

- University: [X]
- Course: [X]
- Degree level: [X]
- Deadlines: [list]
- Grading: [breakdown]
- Word target: [X]
- AI policy: [X]
...

Please confirm this is correct, or let me know what to change.
```

Then ask ONLY for information that could not be extracted. Always ask these (they are personal, not in course docs):

1. **Research question** — "What is your central research question? (One sentence)"
2. **Thesis topic** — "What is your thesis topic? (May differ from RQ)"
3. **Research focus areas** — "What are 1-3 specific focus areas within your topic?"
4. **Methodology type** — "Is your methodology quantitative, qualitative, or mixed methods?"
5. **Methods** — "What specific methods will you use? (e.g., OLS, LASSO, interviews, case study)"
6. **Data sources** — "What are your main data sources?"
7. **Skill level** — "How experienced are you with your methods? (beginner / intermediate / advanced)"
8. **Code stack** — "What programming language/tools will you use? (Python / R / Stata / N/A)"

Only ask these if NOT found in docs:
- Deadlines
- Grading breakdown
- Word target
- Chapter structure
- Citation style
- AI policy

Always ask:
9. **Google Docs** — "Do you use Google Docs for collaboration? (yes/no)" — if yes, ask for document IDs

---

### Step 3 — Generate the filled CLAUDE.md

Read the existing template CLAUDE.md. Replace all `<!-- FILL IN -->` placeholders with the extracted and provided information. Write the completed CLAUDE.md to the project root.

Key formatting rules:
- Deadlines: use absolute dates, sorted chronologically
- Methods: list all methods mentioned
- Chapter structure: if not specified in docs, use the default 5-chapter structure (Introduction, Literature Review, Methodology, Results, Conclusion) with reasonable word targets based on the total target
- If total word target was not found, estimate based on degree level:
  - Bachelor: 8,000-10,000 words
  - Master: 15,000-25,000 words
  - PhD chapter: 8,000-12,000 words

---

### Step 4 — Create project files

Based on the configuration:

1. **Create chapter files** in `writing/` — one empty markdown file per chapter from the chapter structure, each with a header:
   ```markdown
   # [Chapter Title]

   > **Status:** Not started
   > **Word target:** [N] words
   ```

2. **Create `papers/references.md`** with the header:
   ```markdown
   # References

   > Maintained by `/cite`. Last updated: [date].

   ---
   ```
   If starting literature was provided, add each paper as an entry.

3. **Create `notes/ralph-state.md`** with the initial pipeline state (all stages unchecked).

---

### Step 5 — Report back

Print a summary:

```
Setup complete!

  University:      [X]
  Topic:           [X]
  Degree:          [X]
  Methodology:     [X]
  Chapters:        [N] chapters created in writing/
  Word target:     [N] words
  Deadlines:       [N] deadlines set
  Code stack:      [X]
  AI policy:       [X]
  Google Docs:     [yes/no]

Files created:
  - CLAUDE.md (filled configuration)
  - writing/ch1_introduction.md ... writing/chN_[name].md
  - papers/references.md
  - notes/ralph-state.md

Next steps:
  1. Drop your academic papers (PDFs) into papers/
  2. Run /pdf [paper.pdf] to extract and annotate each one
  3. Run /research-guide to think through your approach
  4. Run /wordcount to see your starting progress
```

---

## Rules

- Never guess information that wasn't in the documents or provided by the user. Ask rather than assume.
- If a document cannot be read (encrypted PDF, image-based scan), tell the user and ask them to provide the info manually.
- The CLAUDE.md must be complete enough for all 16 other skills to work. At minimum, sections 1, 4, 6, 7, and 9 must be filled.
- If the AI policy says AI writing is NOT permitted, set section 6 accordingly and note that writing skills should be used for outlining and review only, not for generating prose.
- Delete optional sections (3: Grading, 10: Google Docs) if not applicable rather than leaving them with placeholders.
