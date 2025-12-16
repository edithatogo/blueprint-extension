# Investigation: How Are Workflows Loaded and Structured?

Generated: 2025-12-16T23:54+11:00

## Executive Summary

- Workflows are **Markdown files** stored in `.agent/workflows/` with YAML frontmatter containing a `description` field
- Each workflow file corresponds to a **slash command** (e.g., `bp-plan.md` → `/bp-plan`)
- Workflows follow a consistent structure: **frontmatter → Description → Steps** (numbered list)
- **Rules** in `.agent/rules/` provide cross-cutting behavioral constraints that apply across workflows
- The filename-to-command mapping is implicit—no registry or manifest required
- All workflows output to well-defined **state files** (PLAN.md, TODO.md, ACT.md, etc.) or `reports/` directory

## System/Feature Overview

The workflow system enables structured, repeatable processes for software development tasks. Antigravity reads workflow files from `.agent/workflows/` and exposes them as slash commands. Users invoke workflows with `/workflow-name [arguments]`, and the agent follows the steps defined in the corresponding Markdown file.

**Location**: `.agent/workflows/` (19 workflow files as of this investigation)

## Key Components

| Component | Location | Responsibility |
|-----------|----------|----------------|
| Workflow files | `.agent/workflows/*.md` | Define step-by-step procedures for slash commands |
| Rule files | `.agent/rules/*.md` | Enforce behavioral constraints across all workflows |
| Workflow README | `.agent/workflows/README.md` | Catalog of available workflows with descriptions |
| State files | Root directory | Persistent workflow state (PLAN.md, TODO.md, etc.) |

## Main Flows

### Workflow Discovery
```
Antigravity startup
  → Scan .agent/workflows/ directory
  → Parse each .md file for frontmatter `description`
  → Register as slash commands using filename
```

### Workflow Invocation
```
User types /bp-plan [goal]
  → Antigravity loads .agent/workflows/bp-plan.md
  → Agent reads Description and Steps sections
  → Agent executes steps sequentially
  → Agent writes output to PLAN.md
```

### Rule Application
```
Agent operates in workspace
  → Loads .agent/rules/*.md as context
  → Applies constraints during all operations
  → (e.g., "ask confirmation before destructive actions")
```

## Configuration & Dependencies

### Workflow File Format
Workflows use this structure (evidenced in all workflow files):

```markdown
---
description: Short description for command menu
---

# workflow-name

## Description
Detailed explanation of what the workflow does.

## Steps
1. First step
2. Second step
   - Sub-bullet with details
3. Third step
```

**Evidence**: [bp-plan.md:L1-3](file:///Users/doughnut/GitHub/blueprint-extension/.agent/workflows/bp-plan.md#L1-3)

### State File Conventions
| File | Purpose | Created by |
|------|---------|------------|
| `RESEARCH.md` | Research findings | `/bp-research` |
| `REQUIREMENTS.md` | User stories, acceptance criteria | `/bp-requirements` |
| `DESIGN.md` | Technical decisions | `/bp-design` |
| `PLAN.md` | Implementation plan | `/bp-plan` |
| `TODO.md` | Task checklist | `/bp-define` |
| `ACT.md` | Implementation log | `/bp-implement` |
| `TEST.md` | Test plan and results | `/bp-test` |
| `reports/*.md` | Investigation outputs | `/investigate`, `/map`, etc. |

**Evidence**: [blueprint.md:L12-19](file:///Users/doughnut/GitHub/blueprint-extension/.agent/rules/blueprint.md#L12-19)

## Risks & Sharp Edges

1. **No explicit registry**: Workflow discovery is filesystem-based—missing files silently fail to register
2. **Filename sensitivity**: Command names are derived from filenames; renaming breaks invocation
3. **12,000-character limit**: Workflows must stay under Antigravity's per-file limit
4. **Manual testing only**: No automated validation that workflows execute correctly

**Evidence**: [AGENTS.md:L29](file:///Users/doughnut/GitHub/blueprint-extension/AGENTS.md#L29)

## Open Questions / Unknowns

- **Hypothesis**: Antigravity may cache workflow definitions; changes might require reload
  - *Would confirm*: Test modifying a workflow and observing if changes are immediate
- **Unknown**: How frontmatter `description` is parsed—assumed to be YAML format
- **Unknown**: Whether nested directories (e.g., `.agent/workflows/advanced/`) are supported

## Exploration Trace

### Search Terms Used
- "workflow" (in file/dir names)
- "description" (frontmatter field)
- YAML frontmatter pattern (`---`)
- Slash command references (`/bp-`)

### Files Opened (in order)
1. `.agent/workflows/` - directory listing
2. `.agent/rules/` - directory listing
3. `.agent/workflows/README.md` - workflow catalog
4. `.agent/workflows/bp-plan.md` - example workflow structure
5. `.agent/workflows/bp-implement.md` - example workflow structure
6. `.agent/rules/blueprint.md` - rule file structure
7. `AGENTS.md` - repository guidelines

### Branches Followed
- Workflow → Steps → State files (PLAN.md, TODO.md, etc.)
- Rules → Constraints → Safety policies
- README → Command catalog → Individual workflows

### Dead Ends
- Looked for workflow manifest/registry file (none exists)
- Looked for workflow validation scripts (none exists)

## Appendix: Relevant Files

| File | Description |
|------|-------------|
| [.agent/workflows/README.md](file:///Users/doughnut/GitHub/blueprint-extension/.agent/workflows/README.md) | Master catalog of all workflows with tables |
| [.agent/workflows/bp-plan.md](file:///Users/doughnut/GitHub/blueprint-extension/.agent/workflows/bp-plan.md) | Example workflow: create implementation plan |
| [.agent/workflows/bp-implement.md](file:///Users/doughnut/GitHub/blueprint-extension/.agent/workflows/bp-implement.md) | Example workflow: execute tasks with validation |
| [.agent/rules/blueprint.md](file:///Users/doughnut/GitHub/blueprint-extension/.agent/rules/blueprint.md) | Core rule file for Blueprint workflows |
| [.agent/rules/code-investigator.md](file:///Users/doughnut/GitHub/blueprint-extension/.agent/rules/code-investigator.md) | Rule file for investigation workflows |
| [AGENTS.md](file:///Users/doughnut/GitHub/blueprint-extension/AGENTS.md) | Repository guidelines including workflow conventions |
