---
description: OWASP-aligned security review of the codebase.
---

# securityreview

## Description

Perform a comprehensive security review aligned with OWASP guidelines. More thorough than `/audit`, focusing on application security vulnerabilities and remediation.

## Inputs

- **Scope** (optional): Directory or file to review (default: entire codebase).
- **Standard** (optional): Security standard to follow (`owasp-top10`, `sans-top25`, `all`).

## Steps

1. **Identify application type**:
   - Web application
   - API service
   - CLI tool
   - Library

2. **OWASP Top 10 Checks**:

   ### A01: Broken Access Control
   - Missing authorization checks
   - IDOR vulnerabilities
   - CORS misconfiguration
   
   ### A02: Cryptographic Failures
   - Weak algorithms
   - Hardcoded keys
   - Insecure transmission
   
   ### A03: Injection
   - SQL injection
   - Command injection
   - XSS vulnerabilities
   
   ### A04: Insecure Design
   - Missing threat modeling
   - Insecure patterns
   
   ### A05: Security Misconfiguration
   - Default credentials
   - Verbose errors
   - Missing headers
   
   ### A06: Vulnerable Components
   - Outdated dependencies
   - Known CVEs
   
   ### A07: Authentication Failures
   - Weak passwords
   - Session management
   - Brute force protection
   
   ### A08: Data Integrity Failures
   - Unsigned updates
   - Deserialization issues
   
   ### A09: Logging Failures
   - Missing audit logs
   - Sensitive data in logs
   
   ### A10: SSRF
   - Unvalidated URLs
   - Internal service access

3. **Scan for patterns**:
   ```bash
   # Example searches
   rg "eval\(|exec\(|system\(" --type py
   rg "innerHTML|document\.write" --type js
   rg "SELECT.*\+|'.*\+.*'" --type py --type js
   ```

4. **Check configurations**:
   - Security headers
   - HTTPS enforcement
   - Rate limiting
   - Input validation

5. **Create report** at `reports/security_review_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Security Review
   
   Generated: [timestamp]
   Standard: OWASP Top 10 2021
   
   ## Executive Summary
   - Critical: X vulnerabilities
   - High: X
   - Medium: X
   - Low: X
   
   ## Findings by Category
   
   ### A01: Broken Access Control
   | Severity | Location | Issue | Remediation |
   |----------|----------|-------|-------------|
   
   [repeat for each category]
   
   ## Dependency Vulnerabilities
   [from package audit]
   
   ## Remediation Priority
   1. [Critical items first]
   
   ## Methodology
   [tools and patterns used]
   ```

6. **Suggest follow-ups**:
   - `/audit focus=dependencies` for package updates
   - `/codereview focus=security` for specific files

## Output

- `reports/security_review_<YYYYMMDD-HHMM>.md`

## Examples

```
/securityreview
/securityreview src/api/
/securityreview standard=owasp-top10
```
