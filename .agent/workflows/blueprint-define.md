# blueprint-define

## Description

Convert `PLAN.md` into an actionable checklist in `TODO.md`.

## Steps

1. Locate `PLAN.md` (it may be under `tasks/`). If it’s missing, recommend running `/blueprint-plan` first.
2. If `TODO.md` already exists, ask the user whether to:
   - overwrite it,
   - create a new task directory like `tasks/<short-name>/TODO.md`, or
   - move work to a new VCS branch/workspace.
3. Decompose `PLAN.md` into Markdown checkbox tasks using `- [ ]` items.
4. Use two-space indentation for parent/child task relationships and add optional tags (e.g., `[docs]`, `[test]`, `[refactor]`).
5. Note which tasks can be done in parallel.
6. Write `TODO.md`, present it for review, and request approval.
7. Recommend the next step: run `/blueprint-implement`.

