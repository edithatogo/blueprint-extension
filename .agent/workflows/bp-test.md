# blueprint-test

## Description

Create and execute a test plan to validate the implementation, logging results in `TEST.md`.

## Steps

1. Locate `PLAN.md`, `TODO.md`, and `ACT.md` (they may be under `tasks/`).
2. If the user included explicit testing instructions after `/blueprint-test`, use those as the test plan.
3. Otherwise, derive a test plan by checking `PLAN.md` / `TODO.md`, then scanning the repo for existing test commands/config.
4. Present the proposed test plan and request approval before running commands.
5. Create/append `TEST.md` with the approved plan, timestamps, commands executed, and outcomes.
6. Summarize results. If failures occur, recommend `/blueprint-refine` with the failure details.

