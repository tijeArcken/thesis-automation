# thesis-automation

17 Claude Code skills (slash commands) that automate thesis writing, research, and quality review. Works with any university, any topic, any discipline — quantitative, qualitative, or mixed methods.

## Quick Start

1. **Clone the repo**
   ```bash
   git clone https://github.com/YOUR_USERNAME/thesis-automation.git
   cd thesis-automation
   ```

2. **Drop your course documents** (syllabus, rubric, guidelines) into `docs/`

3. **Run setup** — opens Claude Code and configures everything
   ```bash
   claude
   # then type: /setup
   ```
   The `/setup` skill reads your documents, extracts deadlines/grading/requirements, and asks follow-up questions to generate your personalized `CLAUDE.md`.

4. **Start writing** — use any of the 17 skills below

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- A thesis to write

## Skills Reference

### Writing & Drafting

| Skill | What it does |
|-------|-------------|
| `/write-section [section]` | Draft any chapter (intro, literature, methodology, results, conclusion, abstract). Multi-pass: outline, draft, style review, humanize. |
| `/write-introduction [outline\|draft\|both]` | Draft the introduction using the Shapiro/Head academic framework: Hook, RQ, Findings, Antecedents, Contribution, Roadmap. |
| `/rewrite-literature` | Multi-agent literature review: inventory papers, group by theme, synthesize, review style, humanize. |
| `/proofread [file]` | Grammar, style, clarity, academic register. Returns issues as HIGH / MEDIUM / LOW with fixes. |
| `/deep-review [file]` | Three-agent parallel review: Language + Citation + Argumentation. Scored report with action plan. |
| `/humanize [file or text]` | Remove AI-writing patterns (24 categories) while preserving academic conventions. |

### Research & Literature

| Skill | What it does |
|-------|-------------|
| `/literature-review [topic]` | Find, annotate, and synthesize papers on a topic. Outputs annotated bibliography + gap analysis. |
| `/fact-check [claim]` | Verify a claim before including it. Returns SUPPORTED / PARTIALLY SUPPORTED / UNSUPPORTED. |
| `/research-guide [focus]` | Socratic dialogue for research design. Asks questions to sharpen your RQ, methodology, and approach. |
| `/pdf [file.pdf]` | Extract structured content from a paper: RQ, methods, data, findings, quotes. Auto-registers citation. |
| `/cite [PDF\|DOI\|manual]` | Add a formatted citation to your references file. Prevents duplicates. |

### Code & Methodology

| Skill | What it does |
|-------|-------------|
| `/review-code [file]` | Review a script/notebook for data leakage, evaluation errors, and correctness. Includes defense prep notes. |
| `/check-methodology [focus]` | Review methodology validity. Supports quantitative, qualitative, and mixed methods. |

### Quality & Progress

| Skill | What it does |
|-------|-------------|
| `/thesis-review [scope]` | Full quality review across 5 dimensions (RQ, literature, methodology, results, writing), each scored 1-10. |
| `/wordcount` | Word count per chapter, page estimates, progress bar toward target, deadline alerts. |

### Session & Setup

| Skill | What it does |
|-------|-------------|
| `/setup` | Read course docs, extract config, generate CLAUDE.md. Run this first. |
| `/ralph-loop` | Session continuity for long pipelines. Tracks 8 stages from research to submission. |

## How `/setup` Works

The setup skill uses a **hybrid doc-driven approach**:

1. **Scans `docs/`** for syllabi, rubrics, guidelines — extracts university, deadlines, grading, word limits, chapter requirements, AI policy
2. **Shows what it found** and asks you to confirm or correct
3. **Asks follow-up questions** only for what's missing: your research question, methods, skill level, code stack
4. **Generates** a filled `CLAUDE.md`, chapter files, references file, and session state

## Customization

### CLAUDE.md

All skills read their configuration from `CLAUDE.md` (auto-loaded by Claude Code). Key sections:

| Section | What to configure |
|---------|-------------------|
| 1. Project Context | University, course, topic, RQ, language |
| 2. Deadlines | Date + milestone table |
| 4. Research Design | Focus areas, methods, data, methodology type, skill level |
| 6. How Claude Should Help | Language, code stack, writing style, AI policy |
| 7. Chapter Structure | Chapter names, file paths, word targets |
| 9. File Paths | Where skills look for papers, references, notes |

See `CLAUDE.example.md` for a fully filled example.

### Folder Structure

The default structure works out of the box:

```
writing/     — chapter drafts (created by /setup)
papers/      — PDFs and reading notes
  notes/     — extracted summaries (created by /pdf)
data/        — datasets (raw/ and processed/)
code/        — scripts and notebooks
output/      — figures/ and tables/
docs/        — course documents (read by /setup)
notes/       — working notes and session state
```

To customize: rename or reorganize folders, then update the paths in CLAUDE.md section 9. All skills read paths from there.

## Google Docs Integration (optional)

If you use Google Docs for collaboration:

1. Set up the [Google Workspace MCP server](https://github.com/anthropics/claude-code) for Claude Code
2. Add your Google Doc IDs in CLAUDE.md section 10
3. Skills can push content to Google Docs using the overwrite procedure documented in CLAUDE.md

## FAQ

**Does this work for qualitative theses?**
Yes. `/check-methodology` has a full qualitative review track (trustworthiness, coding, sampling). `/research-guide` adapts its questions based on your methodology type. Writing skills work with any content.

**Can I use LaTeX instead of markdown?**
The skills generate markdown drafts in `writing/`. You can copy content into your LaTeX document, or modify the skills to output LaTeX directly by noting your preference in CLAUDE.md section 6.

**What about non-English theses?**
Set your language in CLAUDE.md section 1. Writing skills will draft in that language. Note: the `/humanize` skill's AI-pattern detection is optimized for English.

**Is AI use allowed?**
That depends on your university's policy. `/setup` will ask about this and configure CLAUDE.md accordingly. If AI writing is not permitted, skills will be limited to outlining and review rather than generating prose.

## Credits

- Original skills developed for the OF-14 ML & Real Estate thesis at UvA
- `/humanize` adapted from [blader/humanizer](https://github.com/blader/humanizer) based on [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- Introduction framework: Jesse Shapiro / Keith Head
