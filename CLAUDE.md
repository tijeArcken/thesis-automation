# Thesis Project Configuration

## 1. Project Context

- **University:** <!-- FILL IN: Your university name -->
- **Faculty / Department:** <!-- FILL IN: e.g., Faculty of Economics and Business -->
- **Course:** <!-- FILL IN: Course name and code, e.g., "Bachelor Thesis Finance (ABC123)" -->
- **Degree level:** <!-- FILL IN: Bachelor / Master / PhD -->
- **Topic:** <!-- FILL IN: Your thesis topic in one sentence -->
- **Research question:** <!-- FILL IN: Your central research question -->
- **Format:** <!-- FILL IN: e.g., Individual / Group of 2 / Group of 3 -->
- **Language:** <!-- FILL IN: English / Dutch / German / etc. -->

---

## 2. Key Deadlines

| Date | Milestone |
|------|-----------|
| <!-- FILL IN --> | <!-- e.g., Proposal due --> |
| <!-- FILL IN --> | <!-- e.g., Intermediate draft --> |
| <!-- FILL IN --> | <!-- e.g., First complete draft to supervisor --> |
| <!-- FILL IN --> | <!-- e.g., Final submission --> |
| <!-- FILL IN --> | <!-- e.g., Defense / presentation --> |

---

## 3. Grading (optional)

<!-- DELETE this entire section if grading info is not relevant to your workflow. -->

| Component | Weight | Notes |
|-----------|--------|-------|
| <!-- FILL IN --> | <!-- % --> | |
| <!-- FILL IN --> | <!-- % --> | |

- <!-- Any grading rules, e.g., "Minimum 5.0 required on each component" -->

---

## 4. Research Design

### Research Focus Areas

<!-- List 1–3 focus areas for your thesis. Skills like /research-guide and /check-methodology use these. -->

1. **<!-- FILL IN: Focus area name -->** — <!-- brief description -->
2. **<!-- FILL IN: Focus area name -->** — <!-- brief description -->

### Methods

<!-- List the analytical/empirical methods you plan to use. -->

- <!-- FILL IN: e.g., OLS regression, LASSO, Random Forests, qualitative coding, interviews, etc. -->

### Data Sources

| Source | Description |
|--------|-------------|
| <!-- FILL IN --> | <!-- FILL IN --> |

### Methodology Type

<!-- quantitative / qualitative / mixed methods -->
- **Type:** <!-- FILL IN -->

### Skill Level

<!-- How experienced are you with your methods? This adjusts how much skills explain. -->
<!-- Options: beginner / intermediate / advanced -->
- **Methods skill level:** <!-- FILL IN -->

---

## 5. Starting Literature

<!-- List key papers that form the foundation of your thesis. Skills like /literature-review and /deep-review cross-reference these. -->

- <!-- Author (Year) — "Title", Journal -->
- <!-- Author (Year) — "Title", Journal -->
- <!-- Author (Year) — "Title", Journal -->

---

## 6. How Claude Should Help

- **Language:** <!-- e.g., "Always respond in English" -->
- **Code stack:** <!-- e.g., "Python with sklearn, pandas, numpy" or "R with tidyverse" or "Stata" or "N/A (qualitative thesis)" -->
- **Writing style:** <!-- e.g., "Formal academic, third person, APA citations" -->
- **Explain level:** <!-- e.g., "Explain concepts from the ground up" or "Assume advanced knowledge, be concise" -->
- **AI use policy:** <!-- IMPORTANT: State your university's policy on AI assistance. e.g., "AI writing assistance is permitted with supervisor approval. All AI-assisted writing must be reviewed, understood, and owned by the student." -->

---

## 7. Chapter Structure

<!-- Define your thesis chapters. Skills like /wordcount and /write-section use this map. -->
<!-- Adjust chapter names, numbers, and file paths to match your thesis structure. -->

| Chapter | File | Word target |
|---------|------|-------------|
| Introduction | writing/ch1_introduction.md | <!-- e.g., 1000 --> |
| Literature Review | writing/ch2_literature.md | <!-- e.g., 2500 --> |
| Methodology | writing/ch3_methodology.md | <!-- e.g., 2500 --> |
| Results | writing/ch4_results.md | <!-- e.g., 2000 --> |
| Conclusion | writing/ch5_conclusion.md | <!-- e.g., 800 --> |

**Total word target:** <!-- FILL IN: e.g., 8800 -->
**Words per page estimate:** <!-- FILL IN: e.g., 250 (double-spaced) or 300 (single-spaced) -->

---

## 8. Project Folder Structure

> This structure is a sensible default. Rename, add, or remove folders as your project evolves. If you change paths, update section 9 so skills can find your files.

```
thesis-automation/
├── CLAUDE.md              # Auto-loaded by Claude Code (must stay at root)
├── .claude/
│   └── commands/          # Thesis skills (slash commands)
├── docs/                  # Course documents, guidelines, rubrics, syllabi
├── papers/                # Academic papers (PDFs) and reading notes
│   └── notes/             # Extracted paper summaries (created by /pdf)
├── data/
│   ├── raw/               # Raw datasets
│   └── processed/         # Cleaned data ready for analysis
├── code/                  # Scripts and notebooks
├── output/
│   ├── figures/           # All plots and charts
│   └── tables/            # Results tables
├── writing/               # Thesis chapter drafts
└── notes/                 # Working notes, meeting summaries, scratch
    └── ralph-state.md     # Session state (created by /ralph-loop)
```

---

## 9. File Paths (used by skills)

<!-- These defaults work out of the box. Only change them if you reorganize your folder structure. -->

| Purpose | Path |
|---------|------|
| Chapter drafts | writing/ |
| References file | papers/references.md |
| Paper notes | papers/notes/ |
| Session state | notes/ralph-state.md |
| Course documents | docs/ |

---

## 10. Google Docs Integration (optional)

<!-- DELETE this entire section if you do not use Google Docs for your thesis. -->
<!-- If you use Google Docs, you need the Google Workspace MCP server configured. -->

### Document ID Reference

| Doc | Google Doc ID |
|-----|--------------|
| <!-- e.g., Main Thesis Draft --> | <!-- paste Google Doc ID here --> |
| <!-- e.g., Shared Group Doc --> | <!-- paste Google Doc ID here --> |

### Overwrite Procedure (3 steps)

When pushing content to an existing Google Doc, always use this **overwrite procedure** to preserve the document ID and avoid creating duplicates. Never use `import_to_google_doc` on existing docs.

**Step 1 — Read the existing doc:**
```
mcp__google_workspace__get_doc_content(document_id, user_google_email)
```
Count the total characters to find `end_index`.

**Step 2 — Replace all content:**
```
mcp__google_workspace__modify_doc_text(
  document_id=<existing doc ID>,
  user_google_email=<email>,
  start_index=1,
  end_index=<total character length of current content>,
  text=<full new content as plain text>
)
```

**Step 3 — Verify:**
```
mcp__google_workspace__get_doc_content(document_id, user_google_email)
```

> **Note:** `modify_doc_text` inserts plain text only (no markdown formatting).

---

## 11. Skills Reference

Skills live in `.claude/commands/` and are invoked with `/skill-name`.

### Writing & Drafting
| Skill | Invocation | Description |
|-------|------------|-------------|
| write-section | `/write-section [section]` | Draft a thesis section. Multi-pass: outline, draft, style review. |
| write-introduction | `/write-introduction [outline \| draft \| both]` | Draft the introduction using the Shapiro/Head academic framework: Hook, RQ, Findings, Antecedents, Contribution, Roadmap. |
| rewrite-literature | `/rewrite-literature` | Multi-agent literature review drafting. Synthesizes papers into a coherent academic narrative by theme. |
| proofread | `/proofread [section or file]` | Grammar, style, clarity, and academic register review. Returns issues sorted by severity. |
| deep-review | `/deep-review [file]` | Three-agent parallel review: Language, Citation, Argumentation. Returns unified report. |
| humanize | `/humanize [file or text]` | Remove AI-writing patterns while preserving academic register, passive voice, and domain vocabulary. |

### Research & Literature
| Skill | Invocation | Description |
|-------|------------|-------------|
| literature-review | `/literature-review [topic]` | Annotated bibliography and synthesis on a given topic relevant to your thesis. |
| fact-check | `/fact-check [claim]` | Verify an empirical or literature claim. Returns SUPPORTED / PARTIALLY SUPPORTED / UNSUPPORTED. |
| research-guide | `/research-guide [focus]` | Socratic dialogue for research design. Helps think through methodology and research question. |
| pdf | `/pdf [PDF path]` | Extract structured content from a paper: RQ, methods, data, findings, quotes. Auto-registers citation. |
| cite | `/cite [PDF \| DOI \| manual]` | Extract citation metadata and append to references file. Prevents duplicates. |

### Code & Methodology
| Skill | Invocation | Description |
|-------|------------|-------------|
| review-code | `/review-code [file]` | Review a script/notebook for correctness and methodological mistakes. Includes defense prep notes. |
| check-methodology | `/check-methodology [focus]` | Review methodology validity: model selection, evaluation, features, robustness. |

### Quality & Progress
| Skill | Invocation | Description |
|-------|------------|-------------|
| thesis-review | `/thesis-review [scope]` | Full quality review across 5 dimensions scored 1–10. |
| wordcount | `/wordcount` | Word count per chapter, page estimates, progress toward target, deadline alerts. |

### Session Management
| Skill | Invocation | Description |
|-------|------------|-------------|
| ralph-loop | `/ralph-loop` | Session continuity for long work pipelines. Saves/resumes progress state. |
| setup | `/setup` | Reads your course documents in `docs/`, extracts config, asks follow-up questions, generates a filled CLAUDE.md. |
