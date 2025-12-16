---
description: Perform security and compliance audit of the codebase.
---

# audit

## Description

Perform a security and compliance audit of the codebase, identifying potential vulnerabilities, credential exposure, and best practice violations.

## Inputs

- **Focus** (optional): Specific audit type:
  - `security` - Vulnerabilities, injection risks, auth issues
  - `secrets` - Exposed credentials, API keys, tokens
  - `dependencies` - Vulnerable packages, outdated versions
  - `compliance` - License issues, coding standards
  - `all` (default) - Full audit

## Steps

1. **Scan for secrets and credentials**:
   ```bash
   # Look for potential secrets
   rg -i "(api[_-]?key|secret|password|token|credential)" --type-add 'code:*.{py,js,ts,go,rs,java,rb,env}' -t code
   
   # Check for .env files
   find . -name ".env*" -o -name "*.pem" -o -name "*.key"
   ```

2. **Check for security anti-patterns**:
   - SQL injection risks (string concatenation in queries)
   - Hardcoded credentials
   - Insecure HTTP usage
   - Disabled security features
   - Unsafe deserialization

3. **Audit dependencies** (if package files exist):
   ```bash
   # Python
   pip-audit -r requirements.txt 2>/dev/null || true
   
   # Node
   npm audit 2>/dev/null || true
   
   # Check for outdated
   pip list --outdated 2>/dev/null || npm outdated 2>/dev/null || true
   ```

4. **Check file permissions and gitignore**:
   - Sensitive files not in .gitignore
   - Overly permissive file modes
   - Secrets accidentally committed

5. **Review authentication/authorization patterns**:
   - Auth implementations
   - Session management
   - Access control checks

6. **Create the reports directory** if needed:
   ```bash
   mkdir -p reports
   ```

7. **Write report** to `reports/audit_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Security Audit Report
   
   Generated: [timestamp]
   
   ## Executive Summary
   - Critical: X issues
   - High: X issues
   - Medium: X issues
   - Low: X issues
   
   ## Critical Findings
   
   | ID | Issue | Location | Recommendation |
   |----|-------|----------|----------------|
   | ... | ... | ... | ... |
   
   ## Secrets Scan
   [findings or "No secrets detected"]
   
   ## Dependency Vulnerabilities
   [findings or "No known vulnerabilities"]
   
   ## Security Anti-Patterns
   [findings with locations]
   
   ## Recommendations
   1. [prioritized list]
   
   ## Methodology
   [tools and patterns used]
   ```

8. **Present summary** with critical findings and report path.

## Output

- `reports/audit_<YYYYMMDD-HHMM>.md`

## Examples

```
/audit
/audit focus=secrets
/audit focus=dependencies
```
