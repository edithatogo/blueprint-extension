---
description: Identify complexity and risk hotspots in the codebase.
---

# hotspots

## Description

Analyze the codebase to identify files and functions that may be complexity or risk hotspots. Uses file size, git history (if available), and pattern detection.

## Inputs

- **Focus** (optional): Limit analysis to specific directories or file types.

## Steps

1. **Measure file sizes**:
   ```bash
   find . -name "*.py" -o -name "*.js" -o -name "*.ts" -o -name "*.go" -o -name "*.rs" | \
     xargs wc -l | sort -rn | head -20
   ```
   (Adjust extensions based on detected tech stack)

2. **Check git history** (if available):
   ```bash
   # Files with most commits (churn)
   git log --format=format: --name-only | grep -v '^$' | sort | uniq -c | sort -rn | head -20
   
   # Recent activity
   git log --oneline -20 --stat
   ```

3. **Scan for suspicious patterns** using ripgrep:
   ```bash
   # TODOs and FIXMEs
   rg -c "TODO|FIXME|HACK|XXX" --type-add 'code:*.{py,js,ts,go,rs,java,rb}' -t code
   
   # Long functions (heuristic: many lines between def/function and next def/function)
   # Deep nesting (many indent levels)
   ```

4. **Analyze complexity indicators**:
   - Open the largest files and assess:
     - Function/method length
     - Nesting depth
     - Number of parameters
     - Cyclomatic complexity (estimate)
   - Note any obvious code smells

5. **Create the reports directory** if it doesn't exist:
   ```bash
   mkdir -p reports
   ```

6. **Write the report** to `reports/hotspots_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Hotspot Analysis
   
   Generated: [timestamp]
   
   ## Executive Summary
   - X files identified as potential hotspots
   - Primary risk areas: [list]
   
   ## Size Hotspots (by lines of code)
   | Rank | File | Lines | Notes |
   |------|------|-------|-------|
   | 1    | ...  | ...   | ...   |
   
   ## Churn Hotspots (by commit frequency)
   | Rank | File | Commits | Recent Changes |
   |------|------|---------|----------------|
   | 1    | ...  | ...     | ...            |
   
   ## Pattern Hotspots (TODOs, FIXMEs, etc.)
   | File | Count | Sample |
   |------|-------|--------|
   | ...  | ...   | ...    |
   
   ## Complexity Observations
   [narrative description of complex areas found]
   
   ## Recommendations
   - High priority: [files needing immediate attention]
   - Medium priority: [files to refactor when touched]
   - Low priority: [acceptable complexity for now]
   
   ## Methodology
   [brief description of analysis performed]
   ```

7. **Present a summary** with top 3–5 hotspots and report location.

## Output

- `reports/hotspots_<YYYYMMDD-HHMM>.md`

## Example

```
/hotspots
/hotspots focus on src/api
```
