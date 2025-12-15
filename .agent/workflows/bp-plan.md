---
description: Create a step-by-step implementation plan with backup support.
---

# bp-plan

## Description

Create a concise, step-by-step plan for the task and store it in `PLAN.md` for review.

## Steps

1. Use the text after `/bp-plan` as the planning prompt; ask clarifying questions about goals, constraints, and success criteria.

2. Locate `RESEARCH.md`, `REQUIREMENTS.md`, and `DESIGN.md` if they exist; incorporate relevant findings.

3. **Check for existing files**: If `PLAN.md`, `TODO.md`, or `ACT.md` exist, offer to:
   - Archive them to `archive/<timestamp>/` (preserves history)
   - Move to a task directory `tasks/<completed-task-name>/`
   - Create a new branch with `/bp-branch`
   - Overwrite (not recommended)

4. If archiving, create the archive directory and move files:
   ```
   archive/
     2025-12-15T23-30/
       PLAN.md
       TODO.md
       ACT.md
   ```

5. Produce a plan that is executable: ordered steps, dependencies, and verification/testing notes.

6. Write the plan to `PLAN.md`.

7. Present the plan and request explicit approval before proceeding.

8. Recommend the next step: run `/bp-define`.
