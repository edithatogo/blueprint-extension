---
description: Deep codebase exploration for ambiguous questions. Produces a comprehensive report.
---

# investigatecode

## Description

Perform deep, evidence-based exploration of a codebase to answer ambiguous or high-level questions. Produces a comprehensive report with summary, analysis, and exploration trace.

## Inputs

- **Objective** (required): The question or topic to investigate (text after `/investigatecode`).
- **Constraints** (optional): Focus areas or exclusions (e.g., "focus on auth", "ignore tests").

## Steps

1. **Parse the objective**: Use text after `/investigatecode` as the investigation question. Ask clarifying questions if the scope is unclear.

2. **Generate a quick repo map**:
   - Scan directory structure
   - Identify languages, frameworks, build/test tooling
   - Locate entry points and key configuration files
   - This can be abbreviated if a recent `/map` report exists

3. **Identify candidate areas**: List 3–5 most likely starting points based on:
   - File/directory names matching the objective
   - Documentation references
   - Entry points and configuration

4. **Iterative exploration**:
   - For each candidate, open the file and read relevant sections
   - Follow imports, callers, and type references (prefer structure over keyword search)
   - Record every file opened, search term used, and decision made
   - Refine your hypothesis after each pass
   - Continue until confident or exhausted reasonable paths

5. **Handle uncertainty**:
   - Mark uncertain conclusions as **Hypothesis**
   - List what would confirm or refute each hypothesis
   - If you cannot find supporting evidence, explicitly state "Not found" and list what was searched

6. **Create the reports directory** if it doesn't exist:
   ```bash
   mkdir -p reports
   ```

7. **Write the report** to `reports/codebase_investigation_<topic>_<YYYYMMDD-HHMM>.md` using the Codebase Investigation Template from the investigator rule:
   - Executive Summary (3–7 bullets)
   - System/Feature Overview
   - Key Components (table)
   - Main Flows
   - Configuration & Dependencies
   - Risks & Sharp Edges
   - Open Questions / Unknowns
   - Exploration Trace (search terms, files, branches, dead ends)
   - Appendix: Relevant Files

8. **Present a summary** in chat: 2–3 sentence overview + path to the full report.

9. **Recommend next steps**: Further investigation paths, related workflows (`/trace`, `/hotspots`), or actions if issues were found.

## Output

- `reports/codebase_investigation_<topic>_<YYYYMMDD-HHMM>.md`

## Example

```
/investigatecode How does authentication work?
```

Produces: `reports/codebase_investigation_authentication_20251217-0000.md`
