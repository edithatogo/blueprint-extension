# Blueprint Rules (Antigravity)

Use these rules for workspaces using the "Blueprint" workflows in `.agent/workflows/`.

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

## Commit Conventions

- Use Conventional Commits for all commits:
  - `feat:` new features
  - `fix:` bug fixes
  - `docs:` documentation changes
  - `chore:` maintenance tasks
  - `refactor:` code restructuring
  - `test:` test additions/changes
- Keep commit messages concise but descriptive.
- Use `/blueprint-commit` to ensure consistent formatting.

## CI Awareness

- Before marking a workflow as complete, verify that CI passes on the current branch.
- If CI fails, use `/blueprint-refine` to address the issues before proceeding.
- Check `.github/workflows/` for available CI configurations.

## Conflict & Drift Handling

- If `PLAN.md` and `TODO.md` become out of sync (e.g., after `/blueprint-refine` changes scope), update `PLAN.md` to reflect the actual direction.
- If `ACT.md` shows significant deviation from `PLAN.md`, document the rationale and ask if the plan should be revised.
- Use `/blueprint-review` to audit consistency before finalizing work.

## Repository Hygiene

- Follow existing project conventions (style, structure, naming) and update relevant docs when behavior changes.
- Keep changes focused on the requested scope; avoid drive-by refactors.
