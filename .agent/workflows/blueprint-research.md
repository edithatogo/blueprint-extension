# blueprint-research

## Description

Research a topic and capture findings in `RESEARCH.md` without changing code.

## Steps

1. Use the text after `/blueprint-research` as the research question; ask clarifying questions if scope or deliverables are unclear.
2. Search the workspace for an existing `RESEARCH.md` (including `tasks/` subdirectories).
3. If `RESEARCH.md` already exists, ask the user whether to:
   - overwrite it,
   - create a new task directory like `tasks/<short-name>/RESEARCH.md`, or
   - move work to a new VCS branch/workspace.
4. Prefer user-provided links and repo context; use web research only as needed.
5. Write `RESEARCH.md` with: summary, key findings, assumptions/open questions, and a references section (URLs).
6. Present a short summary and ask the user to confirm the research is sufficient.
7. Recommend the next step: run `/blueprint-plan`.

