---
description: Deep exploration of academic research projects including protocol, artifacts, manuscript, and supplements.
---

# investigateresearch

## Description

Perform deep, evidence-based exploration of an academic research project to understand its structure, status, and completeness. Produces a comprehensive report covering protocol, data artifacts, manuscript, figures/tables, and supplementary materials.

## Inputs

- **Objective** (required): The question or aspect to investigate (text after `/investigateresearch`).
  - Examples: "What is the overall project status?", "Are all figures reproducible?", "What methods are documented?"
- **Constraints** (optional): Focus areas or exclusions (e.g., "focus on methods", "ignore raw data").

## Steps

1. **Parse the objective**: Use text after `/investigateresearch` as the investigation question. Ask clarifying questions if the scope is unclear.

2. **Generate a project inventory**:
   - Scan directory structure for research artifacts
   - Look for: protocols, data directories, manuscripts, figures, tables, supplements
   - Identify versioning conventions (dates, version numbers)
   - Note file formats (docx, md, pdf, csv, xlsx, R, py, etc.)

3. **Locate key artifacts**:
   - **Protocol/Methods**: Study design, ethics, methodology documents
   - **Data**: Raw data, processed data, databases
   - **Manuscript**: Draft files, versions, track changes
   - **Figures**: Generated images, source scripts, source data
   - **Tables**: Data tables, statistical outputs
   - **Supplements**: Appendices, additional methods, extended data
   - **References**: Bibliography files (.bib, .ris), citation databases

4. **Assess traceability**:
   - Can claims in the manuscript be traced to data/analyses?
   - Are figures reproducible from documented scripts?
   - Is there a clear data provenance chain?

5. **Iterative exploration**:
   - For each artifact category, open representative files
   - Follow cross-references between documents (e.g., "see Figure 2", "as described in Methods")
   - Record every file opened, search term used, and decision made
   - Refine understanding after each pass
   - Continue until confident or exhausted reasonable paths

6. **Handle uncertainty**:
   - Mark uncertain conclusions as **Hypothesis**
   - List what would confirm or refute each hypothesis
   - If you cannot find supporting evidence, explicitly state "Not found" and list what was searched

7. **Create the reports directory** if it doesn't exist:
   ```bash
   mkdir -p reports
   ```

8. **Write the report** to `reports/research_investigation_<topic>_<YYYYMMDD-HHMM>.md` using the Research Investigation Template from the investigator rule:
   - Executive Summary (3–7 bullets)
   - Project Overview (question, design, status)
   - Artifacts Inventory (table)
   - Methods Traceability
   - Manuscript Status (table by section)
   - Figures & Tables (table with provenance)
   - Supplementary Materials
   - References & Citations
   - Risks & Gaps
   - Open Questions / Unknowns
   - Exploration Trace
   - Appendix: Key Files

9. **Present a summary** in chat: 2–3 sentence overview + path to the full report.

10. **Recommend next steps**: Missing artifacts to create, traceability gaps to address, or verification actions.

## Output

- `reports/research_investigation_<topic>_<YYYYMMDD-HHMM>.md`

## Example

```
/investigateresearch What is the current manuscript status?
/investigateresearch Are all figures traceable to source data?
/investigateresearch What methods documentation exists?
```

Produces: `reports/research_investigation_manuscript_status_20251217-0000.md`

## Research Project Conventions

This workflow looks for common academic project structures:

```
project/
├── protocol/           # Study design, ethics, methods
├── data/
│   ├── raw/            # Original data files
│   └── processed/      # Cleaned/transformed data
├── analysis/           # Scripts, notebooks
├── manuscript/         # Draft versions
├── figures/            # Generated figures
├── tables/             # Data tables
├── supplements/        # Appendices, extended data
└── references/         # Bibliography files
```

Adapt to the actual structure found in the repository.
