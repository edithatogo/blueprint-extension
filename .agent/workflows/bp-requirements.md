---
description: Gather and document formal requirements with user stories and acceptance criteria.
---

# bp-requirements

## Description

Create a structured `REQUIREMENTS.md` with user stories, acceptance criteria, and constraints before designing or planning implementation.

## Steps

1. Use the text after `/bp-requirements` as the feature/goal description. Ask clarifying questions about:
   - Who are the users/stakeholders?
   - What problem is being solved?
   - What are the success criteria?

2. **Check for existing file**: If `REQUIREMENTS.md` exists, offer to:
   - Archive it to `archive/<timestamp>/REQUIREMENTS.md`
   - Create in a task directory `tasks/<name>/REQUIREMENTS.md`
   - Overwrite

3. Locate `RESEARCH.md` if it exists; incorporate relevant findings.

4. Create `REQUIREMENTS.md` with the following structure:

```markdown
# Requirements: [Feature Name]

## Overview
[Brief description of the feature/change]

## User Stories
- As a [user type], I want [goal] so that [benefit]

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Constraints
- [Technical, time, or resource constraints]

## Out of Scope
- [What this does NOT include]
```

5. Present `REQUIREMENTS.md` and request explicit approval.

6. Recommend next step: `/bp-design` or `/bp-plan`.
