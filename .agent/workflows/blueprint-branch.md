---
description: Isolate work in a new Git branch with workflow files.
---

# blueprint-branch

## Description

Create a new Git branch and optionally a task directory to isolate workflow state for parallel or experimental work.

## Steps

1. Use the text after `/blueprint-branch` as the branch name hint. If not provided, ask for a short, descriptive name.

2. Sanitize the branch name (lowercase, hyphens, no spaces). Propose the final name and ask for confirmation.

3. Check for uncommitted changes with `git status`. If changes exist, ask:
   - Stash them?
   - Commit them first?
   - Abort?

4. Create the new branch with `git checkout -b <branch-name>`.

5. Ask if the user wants to create a dedicated task directory (e.g., `tasks/<branch-name>/`) for workflow files. If yes:
   - Create the directory.
   - Move or copy existing `PLAN.md`, `TODO.md`, etc. if they exist.

6. Confirm branch creation and current working directory.

7. Recommend the next step: `/blueprint-plan` or `/blueprint-resume`.
