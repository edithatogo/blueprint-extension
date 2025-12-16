---
description: Execute TODO.md tasks with validation and logging.
---

# bp-implement

## Description

Implement the tasks in `TODO.md`, validate completion, and maintain a structured implementation log in `ACT.md`. Follows Keep a Changelog format for traceability.

## Steps

1. Locate `PLAN.md` and `TODO.md` (they may be under `tasks/`). If missing, stop and ask how to proceed.

2. **Check for existing ACT.md**: If `ACT.md` exists, offer to:
   - Archive it to `archive/<timestamp>/ACT.md`
   - Append to existing file
   - Overwrite

3. Create/update `ACT.md` with this structure:

```markdown
# Implementation Log: [Feature Name]

> Implementation of [PLAN.md](./PLAN.md) | Started: [date] | Status: In Progress

## Summary

| Metric | Value |
|--------|-------|
| Tasks Completed | 0 / X |
| Time Elapsed | 0h |
| Files Changed | 0 |
| Tests Added | 0 |
| Commits | 0 |

---

## Session Log

### [YYYY-MM-DD HH:MM] Session Start

**Focus**: [What this session aims to accomplish]

---

#### ✅ Completed: [Task Title]

**Task**: [Description from TODO.md]
**Duration**: [time taken]

**Changes**:
- `path/to/file.py`: [what changed]
- `path/to/other.py`: [what changed]

**Commands Run**:
```bash
# Command and output summary
pytest tests/test_feature.py
# ✓ 5 passed
```

**Verification**:
- [x] Unit tests pass
- [x] Linting clean
- [ ] Integration tested

**Commit**: `abc123` - feat: add feature X

---

#### 🔄 In Progress: [Task Title]

**Task**: [Description]
**Started**: [time]
**Status**: [current state]

**Notes**:
- [observations, decisions made]

---

#### ⚠️ Blocked: [Task Title]

**Task**: [Description]
**Blocker**: [what's preventing progress]
**Action Needed**: [what would unblock]

---

#### ⏭️ Deferred: [Task Title]

**Task**: [Description]
**Reason**: [why deferred]
**Deferred To**: [future iteration/ticket]

---

### [YYYY-MM-DD HH:MM] Session End

**Accomplished**:
- [summary of what was done]

**Next Session**:
- [what to pick up next]

---

## Decisions Made

| Decision | Rationale | Date |
|----------|-----------|------|
| Chose X over Y | [why] | [date] |

---

## Issues Encountered

| Issue | Resolution | Time Lost |
|-------|------------|-----------|
| [problem] | [how solved] | [duration] |

---

## Files Changed

| File | Change Type | Description |
|------|-------------|-------------|
| `src/feature.py` | Added | New feature implementation |
| `tests/test_feature.py` | Added | Unit tests |
| `README.md` | Modified | Updated docs |

---

## Verification Summary

| Check | Status | Notes |
|-------|--------|-------|
| Unit Tests | ✅ Pass | 15/15 |
| Integration Tests | ✅ Pass | 5/5 |
| Linting | ✅ Pass | No errors |
| Type Check | ⚠️ Warn | 2 minor issues |
| Build | ✅ Pass | |
| Manual Test | ✅ Pass | Tested happy path |

---

## References

- [PLAN.md](./PLAN.md)
- [TODO.md](./TODO.md)
- [DESIGN.md](./DESIGN.md)
```

4. Execute `TODO.md` tasks sequentially:
   - Before starting each task, announce: "Starting: [task description]"
   - After completing each task, mark it `[x]` in `TODO.md`
   - Update `ACT.md` with the completion entry
   - When a subtask completes, check if the parent can be marked complete

5. Before destructive commands (e.g., `rm`, `git push`, schema/data changes), explain impact and ask for confirmation.

6. Run relevant verification steps and record in `ACT.md`:
   - Linting
   - Type checking
   - Unit tests
   - Build

7. **Validation Step**: Before completing:
   - Parse `TODO.md` and list any remaining `[ ]` items
   - If incomplete items exist, ask if they should be:
     - Completed now
     - Deferred (move to a new TODO)
     - Marked as out of scope
   - Do NOT recommend `/bp-test` until all items are resolved

8. Update the Summary section in `ACT.md` with final metrics.

9. When all tasks are addressed, summarize changes and point the user to `ACT.md` for details.

10. Recommend the next step: `/bp-test` or `/bp-review`.

## Output

- Updated `TODO.md` (with tasks marked complete)
- `ACT.md` (structured implementation log)

## Standards Reference

- **Keep a Changelog**: https://keepachangelog.com/ - Structured changelog format
- **Conventional Commits**: Commit message format for traceability
- **Definition of Done**: Verification steps before task completion
