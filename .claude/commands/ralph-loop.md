Session maintenance for long thesis work pipelines. Saves context, tracks stage completion, and resumes where you left off across multiple sessions.

## Usage
`/ralph-loop`

Optionally specify an action:
- `/ralph-loop status` — show current pipeline stage and progress
- `/ralph-loop save` — save current progress to the state file
- `/ralph-loop resume` — read saved state and resume from last checkpoint
- `/ralph-loop reset` — clear saved state and start fresh
- `/ralph-loop` (no action) — smart default: check state file, resume if it exists, start fresh if not

## Context

**Read CLAUDE.md before proceeding** to determine:
- The thesis topic and deadlines (sections 1 and 2)
- The state file path (section 9 — default: `notes/ralph-state.md`)

## Pipeline Stages

The thesis pipeline has these stages (tracked in the state file):

```
[ ] 1. RESEARCH      — literature collected, annotated, synthesized
[ ] 2. DATA          — data loaded, cleaned, exploratory analysis done
[ ] 3. METHODOLOGY   — methods specified, code written and reviewed
[ ] 4. RESULTS       — analysis run, outputs saved
[ ] 5. WRITING       — all chapters drafted
[ ] 6. REVIEW        — thesis review run, issues addressed
[ ] 7. REVISION      — revisions complete based on feedback
[ ] 8. FINAL         — proofreading done, ready for submission
```

## State File Format

```markdown
# Ralph Loop State — [Last Updated: YYYY-MM-DD HH:MM]

## Current Stage: [STAGE NAME]
## Next Action: [what to do when resuming]

## Stage Status
- [x] 1. RESEARCH — completed [date]
- [ ] 2. DATA — in progress
- [ ] 3. METHODOLOGY
...

## Open Issues
- [issue 1]
- [issue 2]

## Session Notes
[Free-form notes from the last session]
```

## Behavior

### On `/ralph-loop` (smart default)
1. Check if the state file exists
2. If yes: read it, report current stage and next action, ask if user wants to resume
3. If no: show the full pipeline, ask which stage to start from, create the state file

### On resuming
- Read the state file
- Summarize: what was done, what's open, what's next
- Check the deadlines from CLAUDE.md section 2 and flag any that are approaching
- Suggest which skill to run next (e.g., `/review-code` if at stage 3, `/write-section results` if at stage 5)

### On saving
- Update the state file with current stage, any new open issues, session notes
- Confirm the save with a timestamp

## Why This Exists
Long thesis pipelines span multiple sessions. Without a state tracker, context is lost between conversations. This skill provides lightweight continuity — not a full task manager, just enough structure to pick up where you left off.
