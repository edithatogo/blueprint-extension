---
description: Break down the plan into actionable tasks with backup support.
---

# bp-define

## Description

Turn `PLAN.md` into a detailed, prioritized task checklist in `TODO.md`. Follows MoSCoW prioritization and includes clear completion criteria.

## Steps

1. Locate `PLAN.md` (it may be under `tasks/`). If missing, stop and ask whether to:
   - Run `/bp-plan` first
   - Provide a plan inline

2. **Check for existing TODO.md**: If `TODO.md` exists, offer to:
   - Archive it to `archive/<timestamp>/TODO.md`
   - Create in a task directory `tasks/<name>/TODO.md`
   - Overwrite

3. Break down each step in `PLAN.md` into actionable tasks following this structure:

```markdown
# TODO: [Feature Name]

> Generated from PLAN.md on [date]

## Progress

<!-- Update these counts as work progresses -->
- Total: X tasks
- Completed: 0
- Remaining: X

```
[░░░░░░░░░░] 0%
```

---

## Legend

| Symbol | Meaning |
|--------|---------|
| `[ ]` | Not started |
| `[/]` | In progress |
| `[x]` | Completed |
| `[~]` | Deferred |
| `[!]` | Blocked |

| Priority | Meaning (MoSCoW) |
|----------|------------------|
| `P0` | Must Have - Critical |
| `P1` | Should Have - Important |
| `P2` | Could Have - Nice to have |
| `P3` | Won't Have (this time) |

---

## Phase 1: [Phase Name]

### P0 - Must Have

- [ ] **Task title** `[P0]` `[estimate: 1h]`
  - Acceptance: [what "done" looks like]
  - Depends on: [blockers, if any]
  - [ ] Subtask 1
  - [ ] Subtask 2

- [ ] **Another task** `[P0]` `[estimate: 2h]`
  - Acceptance: [criteria]

### P1 - Should Have

- [ ] **Task title** `[P1]` `[estimate: 30m]`
  - Acceptance: [criteria]

### P2 - Could Have

- [ ] **Task title** `[P2]` `[estimate: 1h]`
  - Acceptance: [criteria]
  - Note: Defer if timeline is tight

---

## Phase 2: [Phase Name]

[Same structure]

---

## Verification Tasks

These run after implementation:

- [ ] All unit tests pass
- [ ] Linting passes
- [ ] Build succeeds
- [ ] Integration tests pass
- [ ] Manual smoke test
- [ ] Documentation updated

---

## Deferred / Out of Scope

Items explicitly excluded from this iteration:

- `[~]` [Deferred item] - Reason: [why deferred]
- `[~]` [Another item] - Planned for: [future iteration]

---

## Notes

[Any additional context or decisions made during definition]
```

4. Include for each task:
   - Clear acceptance criteria
   - Priority tag (P0/P1/P2/P3)
   - Time estimate (optional but recommended)
   - Dependencies (if blocked by other tasks)

5. Write the checklist to `TODO.md`.

6. Present `TODO.md` and request explicit approval before implementation.

7. Recommend the next step: run `/bp-implement`.

## Output

- `TODO.md` (prioritized task checklist)

## Standards Reference

- **MoSCoW Prioritization**: Must/Should/Could/Won't for priority levels
- **SMART Criteria**: Tasks should be Specific, Measurable, Achievable, Relevant, Time-bound
- **Definition of Done**: Each task has explicit completion criteria
