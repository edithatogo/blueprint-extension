# Investigator Rules (Antigravity)

Use these rules when running investigation workflows (`/investigatecode`, `/investigateresearch`, `/map`, `/trace`, `/hotspots`).

## Evidence-First Protocol

- **Every claim must cite evidence**: file path → artifact → location (line range, section, figure number).
- If evidence cannot be found, explicitly state "Not found" and list what was searched.
- Mark uncertain conclusions as **Hypothesis** and list what would confirm or refute them.
- Prefer short, relevant excerpts over large dumps.

## Read-Only Default

- Do not modify files unless the user explicitly requests changes.
- Investigation workflows are for understanding, not editing.
- If you discover issues worth addressing, note them in the report's "Recommendations" section.

## Investigation Loop (Repeatable)

When exploring any question:

1. **Restate the objective** in 1–2 sentences.
2. **Identify starting points**: entry files, config, docs, obvious keywords, README.
3. **Traverse by structure**: follow references, imports, citations—not just keyword grep.
4. **Record your trace**: every search term, file opened, branch followed, and dead end.
5. **Refine hypothesis**: after each exploration pass, update your understanding.
6. **Produce a report** using the appropriate domain template (below).

---

## Codebase Investigation Template

For `/investigatecode`, `/map`, `/trace`, `/hotspots`:

```markdown
# [Objective/Title]

## Executive Summary
- 3–7 bullet points capturing the key findings

## System/Feature Overview
What it is, where it lives, its purpose.

## Key Components

| Component | Location | Responsibility |
|-----------|----------|----------------|
| ...       | ...      | ...            |

## Main Flows
- Bullet points describing call chains or data flows
- Include: `caller() → callee() → ...` notation

## Configuration & Dependencies
- Config files, environment variables, external dependencies

## Risks & Sharp Edges
- Known issues, complexity hotspots, tech debt

## Open Questions / Unknowns
- What couldn't be confirmed; what needs further investigation

## Exploration Trace
- Search terms used
- Files opened (in order)
- Branches followed
- Dead ends encountered

## Appendix: Relevant Files
List of most relevant files discovered, with brief descriptions.
```

---

## Research Investigation Template

For `/investigateresearch`:

```markdown
# [Research Project/Question]

## Executive Summary
- 3–7 bullet points on project status, key findings, gaps

## Project Overview
- Research question/hypothesis
- Study design and methodology
- Current phase/status

## Artifacts Inventory

| Artifact Type | Location | Status | Notes |
|---------------|----------|--------|-------|
| Protocol | ... | Draft/Final | ... |
| Data files | ... | ... | ... |
| Manuscript | ... | ... | ... |
| Figures | ... | ... | ... |
| Tables | ... | ... | ... |
| Supplements | ... | ... | ... |

## Methods Traceability
- Protocol → Implementation → Results chain
- Data processing pipeline
- Statistical analysis workflow

## Manuscript Status

| Section | File | Status | Word Count |
|---------|------|--------|------------|
| Introduction | ... | ... | ... |
| Methods | ... | ... | ... |
| Results | ... | ... | ... |
| Discussion | ... | ... | ... |

## Figures & Tables

| ID | Title | Source Data | Script | Status |
|----|-------|-------------|--------|--------|
| Fig 1 | ... | ... | ... | ... |
| Table 1 | ... | ... | ... | ... |

## Supplementary Materials
- List of supplements with locations and purposes

## References & Citations
- Bibliography files
- Citation management setup
- Missing or incomplete citations

## Risks & Gaps
- Methodological concerns
- Missing data or artifacts
- Incomplete documentation

## Open Questions / Unknowns
- What couldn't be confirmed; what needs clarification

## Exploration Trace
- Search terms used
- Files opened (in order)
- Branches followed
- Dead ends encountered

## Appendix: Key Files
List of most relevant files discovered, with brief descriptions.
```

---

## Domain-Specific Guidance

### Codebase Investigation
- Follow imports, callers, type references
- Note file boundaries and module transitions
- Document complete call chains
- Consider: file size, git churn, TODO comments

### Research Investigation
- Follow citations, cross-references between documents
- Track data provenance from raw → processed → figures
- Verify manuscript claims against source data
- Check for version consistency across artifacts
