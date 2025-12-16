---
description: Create and execute a test plan with structured results logging.
---

# bp-test

## Description

Create and execute a comprehensive test plan to validate the implementation. Follows IEEE 829 test documentation standards. Results logged in structured `TEST.md`.

## Steps

1. Locate `PLAN.md`, `TODO.md`, and `ACT.md` (they may be under `tasks/`).

2. If the user included explicit testing instructions after `/bp-test`, use those as the test plan.

3. Otherwise, derive a test plan by:
   - Checking acceptance criteria in `REQUIREMENTS.md`
   - Reviewing `PLAN.md` / `TODO.md` for verification steps
   - Scanning the repo for existing test commands/config
   - Identifying critical paths from `DESIGN.md`

4. Present the proposed test plan and request approval before running commands.

5. Create `TEST.md` with this comprehensive structure:

```markdown
# Test Report: [Feature Name]

> Testing [PLAN.md](./PLAN.md) | Date: [date] | Tester: [name/agent]

## Executive Summary

| Metric | Value |
|--------|-------|
| Total Test Cases | X |
| Passed | X (X%) |
| Failed | X (X%) |
| Skipped | X |
| Coverage | X% |
| Duration | Xm Xs |

**Overall Status**: ✅ PASS / ❌ FAIL / ⚠️ PARTIAL

---

## Test Environment

| Component | Version/Details |
|-----------|-----------------|
| OS | [e.g., macOS 14.0] |
| Runtime | [e.g., Python 3.11.5] |
| Database | [e.g., PostgreSQL 15] |
| Browser | [if applicable] |
| Dependencies | [package versions] |

**Environment Variables**:
```bash
NODE_ENV=test
DATABASE_URL=...
```

---

## Test Matrix

### Unit Tests

| Test Suite | Tests | Passed | Failed | Skipped | Duration |
|------------|-------|--------|--------|---------|----------|
| `test_models.py` | 15 | 15 | 0 | 0 | 1.2s |
| `test_services.py` | 23 | 22 | 1 | 0 | 2.5s |
| **Total** | **38** | **37** | **1** | **0** | **3.7s** |

### Integration Tests

| Test Suite | Tests | Passed | Failed | Skipped | Duration |
|------------|-------|--------|--------|---------|----------|
| `test_api.py` | 12 | 12 | 0 | 0 | 5.3s |
| **Total** | **12** | **12** | **0** | **0** | **5.3s** |

### E2E Tests

| Scenario | Status | Duration | Notes |
|----------|--------|----------|-------|
| User registration flow | ✅ Pass | 3.2s | |
| Login with valid creds | ✅ Pass | 1.1s | |
| Login with invalid creds | ✅ Pass | 0.8s | |

---

## Acceptance Criteria Validation

From REQUIREMENTS.md:

| ID | Criterion | Test Method | Result | Evidence |
|----|-----------|-------------|--------|----------|
| AC-001 | User can create resource | `test_create_resource` | ✅ Pass | [link] |
| AC-002 | Response time < 200ms | Load test | ✅ Pass | p95: 145ms |
| AC-003 | Error messages are clear | Manual review | ✅ Pass | Screenshot |

---

## Coverage Report

```
Name                      Stmts   Miss  Cover
----------------------------------------------
src/models.py                45      2    96%
src/services.py              78     12    85%
src/api/routes.py            34      5    85%
----------------------------------------------
TOTAL                       157     19    88%
```

**Coverage by Type**:
- Statements: 88%
- Branches: 82%
- Functions: 91%

---

## Failed Tests

### ❌ test_services.py::test_edge_case

**Error**:
```
AssertionError: Expected 200, got 500
```

**Stacktrace**:
```python
def test_edge_case():
    result = service.process(None)
>   assert result.status == 200
E   AssertionError: assert 500 == 200
```

**Analysis**: Edge case not handled when input is None.

**Recommended Fix**: Add null check in `service.process()`.

**Severity**: Medium

**Ticket**: [Create if needed]

---

## Manual Testing

| Test Case | Steps | Expected | Actual | Status |
|-----------|-------|----------|--------|--------|
| Create new user | 1. Go to /register<br>2. Fill form<br>3. Submit | Redirect to dashboard | Redirected | ✅ Pass |
| Invalid login | 1. Go to /login<br>2. Enter wrong password | Show error | Error shown | ✅ Pass |

---

## Performance Results

| Endpoint | Method | Avg (ms) | p50 | p95 | p99 | RPS |
|----------|--------|----------|-----|-----|-----|-----|
| `/api/users` | GET | 45 | 42 | 89 | 120 | 500 |
| `/api/users` | POST | 67 | 65 | 110 | 145 | 300 |

---

## Security Check

| Check | Tool | Status | Notes |
|-------|------|--------|-------|
| Dependency vulnerabilities | npm audit / pip-audit | ✅ Pass | 0 issues |
| SAST scan | semgrep / bandit | ✅ Pass | 0 findings |
| Secrets scan | gitleaks | ✅ Pass | No leaks |

---

## Commands Executed

```bash
# Unit tests
pytest tests/unit -v --cov=src
# Result: 37 passed, 1 failed

# Integration tests
pytest tests/integration -v
# Result: 12 passed

# Linting
ruff check src/
# Result: 0 errors

# Type checking
mypy src/
# Result: Success
```

---

## Recommendations

1. **Fix failing test**: `test_edge_case` - add null handling
2. **Improve coverage**: `src/services.py` at 85% - add edge case tests
3. **Consider**: Adding load tests before production deploy

---

## Approval

| Role | Name | Date | Status |
|------|------|------|--------|
| Developer | | | |
| QA | | | |
| Tech Lead | | | |

---

## Next Steps

- [ ] Fix failing tests
- [ ] Run `/bp-refine` if issues found
- [ ] Proceed to deployment if all pass
```

6. Execute the test plan:
   - Run automated tests
   - Perform manual tests if specified
   - Record all results

7. Summarize results. If failures occur:
   - Document root cause analysis
   - Recommend `/bp-refine` with the failure details

8. Update the Executive Summary with final metrics.

## Output

- `TEST.md` (comprehensive test report)

## Standards Reference

- **IEEE 829**: Standard for Software Test Documentation
- **ISTQB**: Test case and test report structure
- **Test Pyramid**: Unit → Integration → E2E coverage balance
