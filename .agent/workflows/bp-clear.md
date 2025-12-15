# blueprint-clear

## Description

Find and delete all workflow-generated files (`RESEARCH.md`, `PLAN.md`, `TODO.md`, `ACT.md`, `TEST.md`).

## Steps

1. Search the workspace (including `tasks/`) for all matching workflow files.
2. List every file found and ask for explicit confirmation before deleting anything.
3. Delete the confirmed files.
4. Report what was removed (or that nothing was found).

