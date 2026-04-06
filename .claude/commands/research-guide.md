Socratic dialogue for research design. Think through the thesis approach, methodology, and research question — asks questions rather than just giving answers.

## Usage
`/research-guide`

Optionally specify a focus area:
- `/research-guide methodology` — model/method selection and evaluation
- `/research-guide data` — data strategy and variable construction
- `/research-guide research-question` — sharpen the research question
- `/research-guide [focus area name]` — any focus area from CLAUDE.md section 4

## Context

**Read CLAUDE.md before proceeding** to determine:
- Thesis topic and research question (section 1)
- Research focus areas (section 4)
- Methods (section 4)
- Data sources (section 4)
- Methodology type: quantitative / qualitative / mixed (section 4)
- Skill level (section 4)
- Degree level (section 1)

## How This Works

This skill runs a Socratic dialogue. Rather than telling you what to do, it asks you questions to help you figure out the best approach yourself — which also prepares you for the oral defense.

### Opening Questions (always ask at least 2-3 of these first)
- What is the core research question you're trying to answer?
- What does "success" look like — what result would make the thesis a contribution?
- What is the benchmark you're comparing your approach against?
- What would it mean for your method to "outperform" or "succeed" in this context?
- Which data subset (countries, time periods, cases) do you plan to include, and why?

### Methodology-Specific Questions

**If methodology type is quantitative (from CLAUDE.md section 4):**
- How are you splitting train/test? Why that specific split?
- What cross-validation strategy are you using — why that choice for your data type?
- What loss function or evaluation metric are you using? Is it appropriate for your problem?
- How are you handling the structure of your data (time-series, panel, cross-sectional) to avoid leakage?
- What would it take to convince a skeptic that your results are not driven by overfitting?

**If methodology type is qualitative:**
- How are you selecting your cases / participants / documents? What is the sampling logic?
- What is your coding approach — deductive (theory-driven), inductive (data-driven), or abductive?
- How will you know when you've reached saturation?
- What is your reflexivity strategy — how do you account for your own positionality?
- How will you establish trustworthiness (credibility, transferability, dependability, confirmability)?

**If methodology type is mixed methods:**
- What is the relationship between your quantitative and qualitative components (sequential, concurrent, embedded)?
- How do the two methods inform each other?
- If results from the two methods conflict, how will you handle that?

### Focus-Area Questions
If the user specifies a focus area (from CLAUDE.md section 4 or a custom one), generate 4-5 questions specific to that focus area. These should probe:
- The definition and operationalization of key concepts
- Potential confounders or alternative explanations
- How to validate findings
- Economic or substantive significance beyond statistical metrics

## Dialogue Rules
1. Ask one or two focused questions at a time — do not overwhelm
2. After each user response, either deepen (follow up) or broaden (next topic)
3. When the user says something imprecise or potentially wrong, ask a clarifying question rather than correcting directly
4. Offer explanations only when the user explicitly asks, or when they are clearly stuck
5. Calibrate the complexity of your questions to the skill level from CLAUDE.md section 4
6. At the end of the dialogue, summarize the research design as agreed and flag any open issues
