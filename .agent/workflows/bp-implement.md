---
description: Execute TODO.md tasks with validation and logging.
---

# bp-implement

## Description

Implement the tasks in `TODO.md`, validate completion, and log work in `ACT.md`.

## Steps

1. Locate `PLAN.md` and `TODO.md` (they may be under `tasks/`). If missing, stop and ask how to proceed.

2. **Check for existing ACT.md**: If `ACT.md` exists, offer to:
   - Archive it to `archive/<timestamp>/ACT.md`
   - Append to existing file
   - Overwrite

3. Execute `TODO.md` tasks sequentially:
   - Before starting each task, announce: "Starting: [task description]"
   - After completing each task, mark it `[x]` in `TODO.md`
   - When a subtask completes, check if the parent can be marked complete

4. Before destructive commands (e.g., `rm`, `git push`, schema/data changes), explain impact and ask for confirmation.

5. After each significant action, append to `ACT.md` with a timestamp:
   - What changed
   - Commands run
   - Notable output/errors

6. Run relevant local verification steps when available (format, lint, build, unit tests) and record results in `ACT.md`.

7. **Validation Step**: Before completing:
   - Parse `TODO.md` and list any remaining `[ ]` items
   - If incomplete items exist, ask if they should be:
     - Completed now
     - Deferred (move to a new TODO)
     - Marked as out of scope
   - Do NOT recommend `/bp-test` until all items are resolved

8. When all tasks are addressed, summarize changes and point the user to `ACT.md` for details.

9. Recommend the next step: `/bp-test` or `/bp-review`.
