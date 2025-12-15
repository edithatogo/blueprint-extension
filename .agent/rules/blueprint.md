# Blueprint Rules (Antigravity)

Use these rules for workspaces using the “Blueprint” workflows in `.agent/workflows/`.

## Safety & Approval

- Ask for confirmation before any destructive or hard-to-reverse action (e.g., `rm`, `git push`, migrations, deleting data).
- Prefer small, reviewable changes; summarize intent before executing risky commands.

## Workflow Artifacts (Files)

Treat these files as the source of truth for the workflow state:
- `RESEARCH.md` (findings and links)
- `PLAN.md` (approved plan)
- `TODO.md` (checklist of tasks)
- `ACT.md` (implementation log with timestamps)
- `TEST.md` (test plan + results)

If creating one of these files and it already exists, stop and ask the user to choose:
1) overwrite, 2) use a new task directory like `tasks/<short-name>/`, or 3) isolate work in a new VCS branch/workspace.

## Planning Discipline

- For multi-step tasks, produce an explicit plan before editing code.
- Keep assumptions and open questions visible in `RESEARCH.md` / `PLAN.md`.
- Keep `TODO.md` accurate as work progresses (check off completed items and roll up parent tasks).

## Repository Hygiene

- Follow existing project conventions (style, structure, naming) and update relevant docs when behavior changes.
- Keep changes focused on the requested scope; avoid drive-by refactors.

