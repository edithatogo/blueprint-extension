---
description: Create a technical design document with architecture decisions and trade-offs.
---

# bp-design

## Description

Create a structured `DESIGN.md` documenting technical decisions, architecture, and trade-offs before implementation.

## Steps

1. Use the text after `/bp-design` as the design topic. Ask clarifying questions about:
   - What are the key technical decisions?
   - What are the constraints (performance, compatibility, etc.)?
   - Are there alternative approaches to consider?

2. **Check for existing file**: If `DESIGN.md` exists, offer to:
   - Archive it to `archive/<timestamp>/DESIGN.md`
   - Create in a task directory `tasks/<name>/DESIGN.md`
   - Overwrite

3. Locate `REQUIREMENTS.md` and `RESEARCH.md` if they exist; incorporate relevant context.

4. Create `DESIGN.md` with the following structure:

```markdown
# Design: [Feature Name]

## Overview
[What this design addresses]

## Requirements Reference
[Link to or summary of relevant requirements]

## Technical Approach
[High-level approach and architecture]

## Key Decisions
| Decision | Rationale | Alternatives Considered |
|----------|-----------|------------------------|
| ...      | ...       | ...                    |

## Components
- [Component 1]: [Description]
- [Component 2]: [Description]

## Trade-offs
- [Trade-off 1]: [Explanation]

## Risks
- [Risk 1]: [Mitigation]
```

5. Present `DESIGN.md` and request explicit approval.

6. Recommend next step: `/bp-plan`.
