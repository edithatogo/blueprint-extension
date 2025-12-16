---
description: Compare two files or versions to identify differences.
---

# diff

## Description

Compare two files, directories, or git versions to identify and explain differences. Produces a report with a summary of changes and their significance.

## Inputs

- **Targets** (required): Two items to compare. Can be:
  - Two file paths: `file1.py file2.py`
  - Two git refs: `main feature-branch`
  - A file and git ref: `src/auth.py HEAD~5`
- **Focus** (optional): Specific aspect to focus on (e.g., "function signatures", "imports only")

## Steps

1. **Parse targets**: Identify what is being compared (files, directories, git refs).

2. **Retrieve content**:
   - For files: read the file contents
   - For git refs: use `git show` or `git diff`
   - For directories: list and compare file inventories

3. **Generate diff**:
   ```bash
   # File comparison
   diff -u file1 file2
   
   # Git comparison
   git diff ref1..ref2 -- [path]
   
   # Directory comparison
   diff -rq dir1 dir2
   ```

4. **Analyze changes**:
   - Categorize: additions, deletions, modifications
   - Identify semantic changes vs. formatting
   - Note potentially breaking changes

5. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

6. **Write report** to `reports/diff_<target1>_vs_<target2>_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Diff: [Target1] vs [Target2]
   
   Generated: [timestamp]
   
   ## Summary
   - X files changed
   - Y additions, Z deletions
   
   ## Changes by Category
   
   ### Added
   - ...
   
   ### Removed
   - ...
   
   ### Modified
   - ...
   
   ## Significant Changes
   [explanation of important/breaking changes]
   
   ## Full Diff
   [code block with diff output]
   ```

7. **Present summary** with key changes and report path.

## Output

- `reports/diff_<target1>_vs_<target2>_<YYYYMMDD-HHMM>.md`

## Examples

```
/diff src/auth.py src/auth_new.py
/diff main feature-branch
/diff HEAD~5 HEAD -- src/api/
```
