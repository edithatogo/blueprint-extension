# blueprint-resume

## Description

Detect the current Blueprint workflow state and recommend the next step.

## Steps

1. Search the workspace (and `tasks/`) for: `RESEARCH.md`, `PLAN.md`, `TODO.md`, `ACT.md`, `TEST.md`.
2. If files are found outside the current directory (e.g., under `tasks/`), ask the user to confirm which set to use.
3. Determine state by highest-precedence existing file: `TEST.md` → `ACT.md` → `TODO.md` → `PLAN.md` → `RESEARCH.md`.
4. Summarize current state and recommend the next workflow command.
5. If the next step is implementation and the user explicitly agrees, begin executing tasks from `TODO.md`.

