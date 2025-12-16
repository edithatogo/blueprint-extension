---
description: Incrementally update code wiki with recent changes.
---

# codewiki-update

## Description

Incrementally update an existing code wiki by detecting changed files and regenerating only affected documentation. Preserves manual edits in designated sections.

## Inputs

- **Since** (optional): Update files changed since this date/commit (default: auto-detect from wiki timestamps).
- **Force** (optional): List of modules to force-regenerate regardless of changes.

## Steps

1. **Verify wiki exists**:
   - Check for `wiki/` directory
   - If not found, recommend running `/codewiki` first

2. **Detect changes**:
   ```bash
   # Find files modified since last wiki update
   find . -name "*.py" -o -name "*.js" -o -name "*.ts" -newer wiki/index.md
   
   # Or use git if available
   git diff --name-only HEAD~10 -- "*.py" "*.js" "*.ts"
   ```

3. **Map changes to wiki pages**:
   - Source file → module page
   - Source file → API reference entries
   - Config file → configuration page

4. **Identify affected pages**:
   ```
   For each changed file:
   - Direct page (module doc)
   - Cross-reference pages (imports, dependencies)
   - Architecture (if structure changed)
   ```

5. **Preserve manual content**:
   - Look for `<!-- MANUAL START -->` / `<!-- MANUAL END -->` markers
   - Extract and preserve these sections
   - Warn if manual sections would be affected

6. **Regenerate affected pages**:
   - Re-extract docstrings and signatures
   - Update cross-references
   - Refresh dependency graphs if relationships changed

7. **Update metadata**:
   ```markdown
   <!-- 
   Last updated: [timestamp]
   Source files: [list of files used]
   -->
   ```

8. **Validate updates**:
   - Check for broken links (especially if files removed)
   - Verify Mermaid diagrams
   - Ensure consistency with unchanged pages

9. **Generate update report**:
   ```markdown
   # Wiki Update Report
   
   Generated: [timestamp]
   
   ## Changes Detected
   - X source files modified
   - Y source files added
   - Z source files removed
   
   ## Pages Updated
   | Page | Reason |
   |------|--------|
   | modules/auth.md | auth.py modified |
   | api/classes.md | New class added |
   
   ## Pages Preserved
   [pages with no changes]
   
   ## Warnings
   - [any issues encountered]
   ```

10. **Present summary** with pages updated and any warnings.

## Output

- Updated pages in `wiki/`
- `reports/wiki_update_<YYYYMMDD-HHMM>.md` with change log

## Examples

```
/codewiki-update
/codewiki-update since=HEAD~5
/codewiki-update force=auth,api
```

## Manual Content Preservation

To protect manual edits, wrap them in markers:

```markdown
## Auto-Generated Section
[this will be regenerated]

<!-- MANUAL START -->
## Custom Notes
This section is preserved across updates.
<!-- MANUAL END -->

## Another Auto-Generated Section
[this will be regenerated]
```
