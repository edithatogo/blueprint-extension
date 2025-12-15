# blueprint-implement

## Description

Implement the tasks in `TODO.md`, keep progress updated, and log work in `ACT.md`.

## Steps

1. Locate `PLAN.md` and `TODO.md` (they may be under `tasks/`). If missing, stop and ask how to proceed.
2. Execute `TODO.md` tasks sequentially. When a subtask completes, check if the parent can be marked complete.
3. Before destructive commands (e.g., `rm`, `git push`, schema/data changes), explain impact and ask for confirmation.
4. After each significant action, append to `ACT.md` with a timestamp: what changed, commands run, and notable output/errors.
5. Run relevant local verification steps when available (format, lint, build, unit tests) and record results in `ACT.md`.
6. When all tasks are addressed, summarize changes and point the user to `ACT.md` for details.
7. Recommend the next step: run `/blueprint-test`.

