---
description: Stage, commit, and push changes with a conventional commit message.
---

# blueprint-commit

## Description

Stage changes, generate a conventional commit message, and push to the remote repository.

## Steps

1. Run `git status` to identify uncommitted changes.
2. If there are no changes, inform the user and stop.
3. Run `git diff --stat` to summarize what changed.
4. Propose a commit message following Conventional Commits:
   - `feat:` for new features
   - `fix:` for bug fixes
   - `docs:` for documentation changes
   - `chore:` for maintenance tasks
   - `refactor:` for code restructuring
   - `test:` for test additions/changes
5. Present the proposed message and ask for approval or edits.
6. Stage all relevant files with `git add`.
7. Commit with the approved message.
8. Ask if the user wants to push to the remote.
9. If approved, run `git push` and confirm success.
10. Recommend the next step if applicable (e.g., `/blueprint-test` or `/blueprint-review`).
