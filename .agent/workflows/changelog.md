---
description: Generate a changelog from git history.
---

# changelog

## Description

Generate a changelog from git history, organizing commits by type and significance. Useful for release notes and understanding recent changes.

## Inputs

- **Range** (optional): Git ref range (default: last tag to HEAD, or last 50 commits).
  - Examples: `v1.0.0..v1.1.0`, `HEAD~20..HEAD`, `main..feature`
- **Format** (optional): Output style (`keepachangelog`, `conventional`, `simple`).

## Steps

1. **Determine range**:
   ```bash
   # Find last tag if no range specified
   git describe --tags --abbrev=0 2>/dev/null || echo "No tags found"
   
   # Get commit range
   git log --oneline [range] | head -50
   ```

2. **Parse commits** and categorize by Conventional Commits prefixes:
   - `feat:` → Added
   - `fix:` → Fixed
   - `docs:` → Documentation
   - `refactor:` → Changed
   - `perf:` → Performance
   - `test:` → Tests
   - `chore:` → Maintenance
   - `BREAKING CHANGE:` → Breaking

3. **Extract details**:
   ```bash
   git log --pretty=format:"%h|%s|%an|%ad" --date=short [range]
   ```

4. **Identify significant changes**:
   - Breaking changes
   - New features
   - Security fixes
   - Major refactors

5. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

6. **Write report** to `reports/changelog_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Changelog
   
   Generated: [timestamp]
   Range: [from] → [to]
   
   ## Summary
   - X commits analyzed
   - Y features, Z fixes
   
   ## Breaking Changes
   - ...
   
   ## Added
   - [commit hash] description (@author)
   
   ## Fixed
   - ...
   
   ## Changed
   - ...
   
   ## Documentation
   - ...
   
   ## Other
   - ...
   
   ## Contributors
   - @author1 (X commits)
   - @author2 (Y commits)
   ```

7. **Present summary** with highlights and report path.

## Output

- `reports/changelog_<YYYYMMDD-HHMM>.md`

## Examples

```
/changelog
/changelog v1.0.0..HEAD
/changelog HEAD~20..HEAD format=simple
```
