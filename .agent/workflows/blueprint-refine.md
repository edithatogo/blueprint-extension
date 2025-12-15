# blueprint-refine

## Description

Incorporate feedback or resolve issues by refining plans, tasks, code, or tests.

## Steps

1. Use the text after `/blueprint-refine` as the feedback/issue description.
2. Locate `RESEARCH.md`, `PLAN.md`, `TODO.md`, `ACT.md`, and `TEST.md` (where present).
3. Identify what needs refinement and propose a short plan; ask for approval before making changes.
4. Apply the approved changes, updating the relevant workflow file(s) and logging implementation work in `ACT.md`.
5. If the change targets a failing test, re-run the relevant tests and update `TEST.md`.
6. Summarize what changed and recommend the next workflow step (often `/blueprint-test` or `/blueprint-define`).

