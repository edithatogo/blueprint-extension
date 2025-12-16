---
description: Generate a test plan from requirements or existing code.
---

# testplan

## Description

Generate a comprehensive test plan based on requirements, existing code, or both. Identifies test cases, edge cases, and testing priorities.

## Inputs

- **Source** (optional): `requirements` (from REQUIREMENTS.md), `code` (from source), or `both`.
- **Scope** (optional): Specific module or feature to focus on.
- **Type** (optional): Test types to include (`unit`, `integration`, `e2e`, `all`).

## Steps

1. **Gather requirements**:
   - Read `REQUIREMENTS.md` if exists
   - Extract user stories and acceptance criteria
   - Identify functional requirements

2. **Analyze code**:
   - Identify public APIs
   - Find conditional branches
   - Locate error handling paths
   - Discover integration points

3. **Generate test cases**:
   
   ### Unit Tests
   - Happy path for each function
   - Edge cases (null, empty, boundary)
   - Error conditions
   
   ### Integration Tests
   - Component interactions
   - Database operations
   - External service calls
   
   ### E2E Tests
   - User workflows
   - Critical paths
   - Regression scenarios

4. **Identify edge cases**:
   - Boundary values
   - Invalid inputs
   - Concurrency issues
   - Resource exhaustion

5. **Prioritize by risk**:
   - Critical functionality first
   - Complex logic
   - Recently changed code
   - Historically buggy areas

6. **Create report** at `reports/test_plan_<YYYYMMDD-HHMM>.md`:
   ```markdown
   # Test Plan
   
   Generated: [timestamp]
   Source: [requirements/code/both]
   
   ## Overview
   - Total test cases: X
   - Unit: X | Integration: X | E2E: X
   
   ## Test Cases by Priority
   
   ### P0: Critical
   | ID | Description | Type | Inputs | Expected |
   |----|-------------|------|--------|----------|
   
   ### P1: High
   [same format]
   
   ### P2: Medium
   [same format]
   
   ## Edge Cases
   | Scenario | Test Case | Why Important |
   |----------|-----------|---------------|
   
   ## Test Data Requirements
   - [fixtures needed]
   - [mock services]
   
   ## Coverage Targets
   - Statements: X%
   - Branches: X%
   - Functions: X%
   
   ## Suggested Framework
   [based on tech stack]
   ```

7. **Suggest follow-ups**:
   - `/bp-test` to execute the plan
   - `/codereview` for implementation review

## Output

- `reports/test_plan_<YYYYMMDD-HHMM>.md`

## Examples

```
/testplan
/testplan source=requirements
/testplan scope=auth type=unit
```
