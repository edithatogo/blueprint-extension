---
description: Break down the plan into actionable tasks with backup support.
---

# bp-define

## Description

Turn `PLAN.md` into a detailed task checklist in `TODO.md` for tracking during implementation.

## Steps

1. Locate `PLAN.md` (it may be under `tasks/`). If missing, stop and ask whether to:
   - Run `/bp-plan` first
   - Provide a plan inline

2. **Check for existing TODO.md**: If `TODO.md` exists, offer to:
   - Archive it to `archive/<timestamp>/TODO.md`
   - Create in a task directory `tasks/<name>/TODO.md`
   - Overwrite

3. Break down each step in `PLAN.md` into:
   - Actionable tasks with clear completion criteria
   - Subtasks where appropriate (indented)
   - Use checkbox format: `- [ ] Task description`

4. Include:
   - Dependencies between tasks (note blockers)
   - Estimated complexity (optional)
   - Verification steps as tasks

5. Write the checklist to `TODO.md`.

6. Present `TODO.md` and request explicit approval before implementation.

7. Recommend the next step: run `/bp-implement`.
