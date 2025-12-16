---
description: Verify figure reproducibility and data provenance.
---

# checkfigures

## Description

Verify that all figures in a research project are reproducible from source data using documented scripts. Checks for data provenance, script availability, and output consistency.

## Inputs

- **Scope** (optional): Specific figures to check (e.g., "Figure 1", "all").
- **Manuscript** (optional): Path to manuscript referencing the figures.

## Steps

1. **Inventory figures**:
   - Scan `figures/`, `plots/`, `images/` directories
   - Extract figure references from manuscript
   - List: Figure ID, file path, format, last modified

2. **For each figure, trace provenance**:
   - Find generation script (R, Python, etc.)
   - Identify source data files
   - Check for intermediate data
   - Document the pipeline: raw data → processed → figure

3. **Check reproducibility**:
   - Is the generation script present?
   - Is the source data available?
   - Are all dependencies documented?
   - Are random seeds set (if applicable)?

4. **Verify consistency**:
   - Do figure labels match manuscript references?
   - Is the figure format appropriate?
   - Are axis labels and legends present?
   - Does the figure match what's described?

5. **Optionally regenerate** (with user permission):
   ```bash
   # Example: run figure generation script
   python scripts/generate_figure_1.py
   ```

6. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

7. **Write report** to `reports/figure_check_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Figure Reproducibility Report
   
   Generated: [timestamp]
   
   ## Summary
   - Total figures: X
   - Fully reproducible: X
   - Partially reproducible: X
   - Not reproducible: X
   
   ## Figure Inventory
   
   | Figure | File | Script | Data | Status |
   |--------|------|--------|------|--------|
   | Fig 1 | fig1.png | plot_fig1.R | data/results.csv | ✅ |
   | Fig 2 | fig2.png | ❌ Missing | data/raw.csv | ⚠️ |
   
   ## Provenance Details
   
   ### Figure 1
   - **File**: `figures/fig1.png`
   - **Script**: `scripts/plot_fig1.R`
   - **Data**: `data/processed/results.csv`
   - **Pipeline**: `raw.csv → clean.R → results.csv → plot_fig1.R → fig1.png`
   - **Status**: ✅ Fully reproducible
   
   ### Figure 2
   - **File**: `figures/fig2.png`
   - **Script**: ❌ Not found
   - **Data**: `data/raw.csv`
   - **Status**: ⚠️ Script missing
   
   ## Issues
   
   | Figure | Issue | Recommendation |
   |--------|-------|----------------|
   | Fig 2 | Missing generation script | Create or locate script |
   
   ## Recommendations
   1. [prioritized action items]
   ```

8. **Present summary** with reproducibility status and report path.

## Output

- `reports/figure_check_<YYYYMMDD-HHMM>.md`

## Examples

```
/checkfigures
/checkfigures Figure 1
/checkfigures manuscript=manuscript/draft_v2.md
```
