# blueprint-plan

## Description

Create a concise, step-by-step plan for the task and store it in `PLAN.md` for review.

## Steps

1. Use the text after `/blueprint-plan` as the planning prompt; ask clarifying questions about goals, constraints, and success criteria.
2. Locate `RESEARCH.md` if it exists (it may be under `tasks/`); incorporate relevant findings.
3. If `PLAN.md` already exists, ask the user whether to:
   - overwrite it,
   - create a new task directory like `tasks/<short-name>/PLAN.md`, or
   - move work to a new VCS branch/workspace.
4. Produce a plan that is executable: ordered steps, dependencies, and verification/testing notes.
5. Write the plan to `PLAN.md`.
6. Present the plan and request explicit approval before proceeding.
7. Recommend the next step: run `/blueprint-define`.

