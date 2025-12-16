---
description: Validate manuscript claims against source data and analyses.
---

# validateclaims

## Description

Systematically validate claims made in a manuscript against the source data, statistical analyses, and figures. Produces a traceability report showing which claims are supported, unsupported, or unverifiable.

## Inputs

- **Manuscript** (optional): Path to manuscript file (auto-detected if not specified).
- **Focus** (optional): Specific sections to validate (e.g., "results", "abstract").

## Steps

1. **Locate manuscript**:
   - Search for manuscript files (`.md`, `.docx`, `.tex`)
   - Identify the primary/latest version

2. **Extract claims**:
   - Quantitative statements ("X increased by Y%")
   - Statistical results ("p < 0.05", "OR = 2.3")
   - Figure/table references ("as shown in Figure 1")
   - Comparative claims ("treatment A outperformed B")

3. **For each claim, trace to source**:
   - Find referenced figures/tables
   - Locate underlying data files
   - Identify analysis scripts that generated results
   - Check statistical output files

4. **Validate claims**:
   - Compare stated values to source data
   - Verify calculations are reproducible
   - Check figure labels match data
   - Confirm statistical test appropriateness

5. **Categorize findings**:
   - ✅ **Verified**: Claim matches source data
   - ⚠️ **Discrepancy**: Minor mismatch (rounding, labeling)
   - ❌ **Unsupported**: Cannot find supporting evidence
   - 🔍 **Unverifiable**: Source data/analysis not found

6. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

7. **Write report** to `reports/claim_validation_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Claim Validation Report
   
   Generated: [timestamp]
   Manuscript: [file path]
   
   ## Summary
   - Total claims analyzed: X
   - Verified: X (Y%)
   - Discrepancies: X
   - Unsupported: X
   - Unverifiable: X
   
   ## Validation Results
   
   ### ✅ Verified Claims
   | Claim | Location | Source | Notes |
   |-------|----------|--------|-------|
   | ... | ... | ... | ... |
   
   ### ⚠️ Discrepancies
   | Claim | Stated | Actual | Source |
   |-------|--------|--------|--------|
   | ... | ... | ... | ... |
   
   ### ❌ Unsupported Claims
   | Claim | Location | Issue |
   |-------|----------|-------|
   | ... | ... | ... |
   
   ### 🔍 Unverifiable
   | Claim | Location | Missing |
   |-------|----------|---------|
   | ... | ... | ... |
   
   ## Recommendations
   1. [action items to address issues]
   
   ## Traceability Matrix
   | Claim | Data File | Analysis Script | Figure/Table |
   |-------|-----------|-----------------|--------------|
   | ... | ... | ... | ... |
   ```

8. **Present summary** with critical findings and report path.

## Output

- `reports/claim_validation_<YYYYMMDD-HHMM>.md`

## Examples

```
/validateclaims
/validateclaims manuscript/draft_v2.md
/validateclaims focus=results
```
