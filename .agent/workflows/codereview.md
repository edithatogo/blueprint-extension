---
description: Simulate code review for a file, PR, or set of changes.
---

# codereview

## Description

Simulate a thorough code review for a file, pull request, or set of changes. Provides feedback on code quality, best practices, potential bugs, and improvement suggestions.

## Inputs

- **Target** (required): File path, directory, or git diff range.
- **Focus** (optional): Specific aspects (`security`, `performance`, `style`, `logic`, `all`).
- **Severity** (optional): Minimum severity to report (`info`, `warning`, `error`).

## Steps

1. **Identify changes**:
   - For file: read entire file
   - For directory: scan all source files
   - For git range: `git diff [range]`

2. **Analyze code quality**:
   - Naming conventions
   - Code organization
   - DRY violations
   - Magic numbers/strings
   - Comment quality

3. **Check for bugs**:
   - Null/undefined handling
   - Error handling
   - Edge cases
   - Race conditions
   - Resource leaks

4. **Review security**:
   - Input validation
   - Authentication/authorization
   - Injection vulnerabilities
   - Sensitive data exposure

5. **Assess performance**:
   - Algorithmic complexity
   - Database queries (N+1)
   - Memory usage
   - Caching opportunities

6. **Check style**:
   - Formatting consistency
   - Import organization
   - Line length
   - Whitespace

7. **Create report** at `reports/code_review_<target>_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Code Review: [Target]
   
   Generated: [timestamp]
   
   ## Summary
   - Files reviewed: X
   - Issues found: X critical, X warnings, X suggestions
   
   ## Critical Issues
   | File:Line | Issue | Recommendation |
   |-----------|-------|----------------|
   
   ## Warnings
   [same format]
   
   ## Suggestions
   [same format]
   
   ## Positive Observations
   - [good patterns found]
   
   ## Recommended Actions
   1. [prioritized fixes]
   ```

8. **Suggest follow-ups**:
   - `/audit` for deeper security review
   - `/trace` for complex logic
   - `/hotspots` for risk assessment

## Output

- `reports/code_review_<target>_<YYYYMMDD-HHMM>.md`

## Examples

```
/codereview src/auth/login.py
/codereview HEAD~5..HEAD
/codereview src/ focus=security
```
