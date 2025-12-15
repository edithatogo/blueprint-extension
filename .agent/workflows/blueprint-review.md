---
description: Self-review checklist before finalizing work.
---

# blueprint-review

## Description

Run a self-review checklist to ensure work is complete, consistent, and ready to ship.

## Steps

1. **Check for uncommitted changes**: Run `git status`. If changes exist, ask if the user wants to commit first (recommend `/blueprint-commit`).

2. **Verify CI status**: If a CI workflow exists (e.g., `.github/workflows/`), check if the latest commit passed. If not, summarize failures and recommend `/blueprint-refine`.

3. **Audit TODO.md**: Locate `TODO.md` and check for incomplete items (`[ ]`). If any remain, ask if they should be completed or deferred.

4. **Compare PLAN.md and ACT.md**: Check if what was planned matches what was implemented. Flag any significant drift and ask if `PLAN.md` should be updated.

5. **Run lint/format checks**: If the project has lint or format commands (e.g., `npm run lint`, `ruff check`), run them and report results.

6. **Summarize**: Present a review summary with:
   - ✅ Passing checks
   - ⚠️ Warnings or items needing attention
   - ❌ Blocking issues

7. If all checks pass, recommend closing the workflow or running `/blueprint-commit` if not yet pushed.
