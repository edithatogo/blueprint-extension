---
description: Generate a concise summary of a file or directory.
---

# summarize

## Description

Generate a concise, informative summary of a file, directory, or set of files. Useful for quickly understanding unfamiliar code or documentation.

## Inputs

- **Target** (required): File or directory path to summarize.
- **Depth** (optional): For directories, how deep to summarize ("shallow" = top-level only, "deep" = recursive).
- **Focus** (optional): Specific aspect (e.g., "public API", "data structures", "dependencies").

## Steps

1. **Identify target type**: File or directory.

2. **For files**:
   - Read the file content
   - Identify: language, purpose, key exports/functions
   - Extract: docstrings, comments, function signatures
   - Note: dependencies, configuration patterns

3. **For directories**:
   - List contents with sizes
   - Identify purpose of each subdirectory
   - Find key entry points
   - Summarize overall structure

4. **Generate summary** with:
   - One-line purpose statement
   - Key components/exports
   - Dependencies and relationships
   - Usage patterns (if discernible)

5. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

6. **Write report** to `reports/summary_<target>_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Summary: [Target]
   
   Generated: [timestamp]
   
   ## Purpose
   [one-line description]
   
   ## Key Components
   
   | Component | Type | Description |
   |-----------|------|-------------|
   | ... | ... | ... |
   
   ## Dependencies
   - Internal: ...
   - External: ...
   
   ## Usage Patterns
   [how this is typically used]
   
   ## Notes
   [observations, potential issues]
   ```

7. **Present summary** in chat with path to full report.

## Output

- `reports/summary_<target>_<YYYYMMDD-HHMM>.md`

## Examples

```
/summarize src/auth/
/summarize config/settings.py
/summarize . depth=shallow
```
