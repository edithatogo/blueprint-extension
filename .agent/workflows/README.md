# Antigravity Workflows: Blueprint

These Markdown files are intended to be used as Antigravity Workflows (invoked via `/bp-<name>`).

## Full Workflow Sequence

```
RESEARCH → REQUIREMENTS → DESIGN → PLAN → DEFINE → IMPLEMENT → TEST
    ↑                                                          ↓
    ←←←←←←←←←←←←←←←← REFINE / IMPROVE ←←←←←←←←←←←←←←←←←←←←←←←←←
```

## Discovery & Planning

| Command | Description | Output |
|---------|-------------|--------|
| `/bp-research` | Research a topic | `RESEARCH.md` |
| `/bp-requirements` | Gather formal requirements | `REQUIREMENTS.md` |
| `/bp-design` | Document technical design | `DESIGN.md` |
| `/bp-plan` | Create implementation plan | `PLAN.md` |
| `/bp-define` | Break plan into tasks | `TODO.md` |

## Execution

| Command | Description | Output |
|---------|-------------|--------|
| `/bp-implement` | Execute tasks with validation | `ACT.md` |
| `/bp-test` | Run test plan | `TEST.md` |

## Iteration

| Command | Description |
|---------|-------------|
| `/bp-refine` | Fix failures or incorporate feedback |
| `/bp-improve` | Proactively review and enhance artifacts |

## Utilities

| Command | Description |
|---------|-------------|
| `/bp-commit` | Commit with Conventional Commits |
| `/bp-review` | Self-review checklist |
| `/bp-branch` | Isolate work in a new branch |
| `/bp-resume` | Detect state and recommend next step |
| `/bp-clear` | Delete workflow files (with confirmation) |

## Investigation

Explore and understand codebases or research projects without making changes.

| Command | Description | Output |
|---------|-------------|--------|
| `/investigatecode` | Deep codebase exploration for ambiguous questions | `reports/codebase_investigation_*.md` |
| `/investigateresearch` | Deep research project exploration (protocol, manuscript, artifacts) | `reports/research_investigation_*.md` |
| `/map` | Create repository architecture map | `reports/codebase_map_*.md` |
| `/trace` | Trace call paths for a symbol | `reports/trace_*.md` |
| `/hotspots` | Identify complexity/risk hotspots | `reports/hotspots_*.md` |

