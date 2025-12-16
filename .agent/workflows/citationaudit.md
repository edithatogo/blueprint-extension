---
description: Audit citations for completeness, consistency, and correctness.
---

# citationaudit

## Description

Audit citations in a manuscript for completeness, consistency, and correctness. Identifies missing references, unused bibliography entries, and formatting issues.

## Inputs

- **Manuscript** (optional): Path to manuscript file (auto-detected if not specified).
- **Bibliography** (optional): Path to bibliography file (`.bib`, `.ris`, `.json`).

## Steps

1. **Locate files**:
   - Find manuscript file(s)
   - Find bibliography file(s)
   - Identify citation style (APA, Vancouver, etc.)

2. **Extract citations from manuscript**:
   - In-text citations: `[@key]`, `\cite{key}`, `(Author, Year)`
   - Reference list entries
   - Footnote citations

3. **Parse bibliography**:
   - Extract all defined references
   - Note: key, authors, title, year, DOI

4. **Cross-reference**:
   - Citations in text → entries in bibliography
   - Entries in bibliography → citations in text

5. **Check for issues**:
   - **Missing**: Citation in text but not in bibliography
   - **Unused**: Entry in bibliography but not cited
   - **Duplicates**: Same reference with different keys
   - **Incomplete**: Missing required fields (author, year, title)
   - **Format**: Inconsistent formatting

6. **Verify DOIs/URLs** (optional):
   - Check if DOIs resolve
   - Check if URLs are accessible

7. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

8. **Write report** to `reports/citation_audit_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Citation Audit Report
   
   Generated: [timestamp]
   Manuscript: [file path]
   Bibliography: [file path]
   
   ## Summary
   - Citations in manuscript: X
   - Entries in bibliography: Y
   - Missing references: X
   - Unused entries: X
   - Formatting issues: X
   
   ## Missing References
   Citations used but not in bibliography:
   
   | Citation Key | Location in Manuscript |
   |--------------|------------------------|
   | @Smith2020 | Line 45, 123 |
   
   ## Unused Bibliography Entries
   Entries defined but never cited:
   
   | Entry Key | Title |
   |-----------|-------|
   | @Jones2019 | "Unused Paper Title" |
   
   ## Incomplete Entries
   | Entry Key | Missing Fields |
   |-----------|----------------|
   | @Brown2021 | year, doi |
   
   ## Duplicate Entries
   | Keys | Likely Same Reference |
   |------|----------------------|
   | @Smith2020, @Smith2020a | "Same Paper Title" |
   
   ## Formatting Issues
   | Entry Key | Issue |
   |-----------|-------|
   | @Lee2022 | Inconsistent author format |
   
   ## Recommendations
   1. Add missing references to bibliography
   2. Remove or cite unused entries
   3. Complete missing fields
   
   ## Full Citation List
   [alphabetical list of all citations with status]
   ```

9. **Present summary** with critical issues and report path.

## Output

- `reports/citation_audit_<YYYYMMDD-HHMM>.md`

## Examples

```
/citationaudit
/citationaudit manuscript/paper.md
/citationaudit bibliography=references.bib
```
