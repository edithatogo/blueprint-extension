---
description: Proactively review and improve plans, tasks, or designs before implementation.
---

# bp-improve

## Description

Proactively review and suggest improvements to workflow artifacts (REQUIREMENTS.md, DESIGN.md, PLAN.md, TODO.md) before proceeding with implementation.

## Steps

1. Use the text after `/bp-improve` as the focus area (e.g., "improve the plan", "review the requirements"). If not specified, review all available artifacts.

2. Locate available artifacts:
   - `REQUIREMENTS.md`
   - `DESIGN.md`
   - `PLAN.md`
   - `TODO.md`

3. For each artifact, evaluate:
   - **Completeness**: Are there missing sections or gaps?
   - **Clarity**: Is the language clear and unambiguous?
   - **Feasibility**: Are the tasks realistic given constraints?
   - **Consistency**: Do the artifacts align with each other?
   - **Testability**: Can success be verified?

4. Present findings in a structured format:

```markdown
## Improvement Suggestions

### [Artifact Name]
- ✅ Strength: [What's good]
- ⚠️ Improvement: [Suggested change]
- ❌ Issue: [Problem that should be fixed]
```

5. Ask the user which improvements to apply.

6. Apply approved changes, updating the relevant artifacts.

7. Recommend next step based on current workflow state.
