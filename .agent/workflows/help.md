---
description: Display all available workflows organized by category.
---

# help

## Description

Display a quick reference of all available workflows, organized by category. Useful for discovering commands and their purposes.

## Steps

1. **Display workflow catalog**:

## Blueprint Workflows

### Discovery & Planning
| Command | Description |
|---------|-------------|
| `/bp-research [topic]` | Research a topic → `RESEARCH.md` |
| `/bp-requirements [goal]` | Define requirements → `REQUIREMENTS.md` |
| `/bp-design [feature]` | Document design → `DESIGN.md` |
| `/bp-plan [goal]` | Create plan → `PLAN.md` |
| `/bp-define` | Break into tasks → `TODO.md` |

### Execution
| Command | Description |
|---------|-------------|
| `/bp-implement` | Execute tasks → `ACT.md` |
| `/bp-test` | Run tests → `TEST.md` |

### Iteration
| Command | Description |
|---------|-------------|
| `/bp-refine [feedback]` | Fix issues or incorporate feedback |
| `/bp-improve` | Review and enhance artifacts |

### Utilities
| Command | Description |
|---------|-------------|
| `/bp-commit` | Commit with Conventional Commits |
| `/bp-review` | Self-review checklist |
| `/bp-branch [name]` | Create new branch |
| `/bp-resume` | Detect state, recommend next step |
| `/bp-clear` | Delete workflow files |

---

## Investigation Workflows

### Core Investigation
| Command | Description | Output |
|---------|-------------|--------|
| `/investigatecode [question]` | Deep codebase exploration | `reports/codebase_investigation_*.md` |
| `/investigateresearch [question]` | Research project exploration | `reports/research_investigation_*.md` |
| `/map` | Repository architecture map | `reports/codebase_map_*.md` |
| `/trace [symbol]` | Call path analysis | `reports/trace_*.md` |
| `/hotspots` | Complexity/risk identification | `reports/hotspots_*.md` |

### Codebase Utilities
| Command | Description | Output |
|---------|-------------|--------|
| `/diff [a] [b]` | Compare files/versions | `reports/diff_*.md` |
| `/summarize [path]` | Summarize file/directory | `reports/summary_*.md` |
| `/audit` | Security audit | `reports/audit_*.md` |
| `/changelog` | Git changelog | `reports/changelog_*.md` |
| `/dependency-graph` | Module dependencies | `reports/dependency_graph_*.md` |
| `/codereview` | Simulate code review | `reports/code_review_*.md` |
| `/securityreview` | OWASP security review | `reports/security_review_*.md` |

### Research Utilities
| Command | Description | Output |
|---------|-------------|--------|
| `/validateclaims` | Verify manuscript claims | `reports/claim_validation_*.md` |
| `/checkfigures` | Figure reproducibility | `reports/figure_check_*.md` |
| `/citationaudit` | Citation completeness | `reports/citation_audit_*.md` |
| `/peerreview [journal=X]` | Simulate peer review | `reports/peer_review_*.md` |

### Documentation
| Command | Description | Output |
|---------|-------------|--------|
| `/codewiki` | Full documentation wiki | `wiki/` |
| `/codewiki-update` | Update wiki incrementally | `wiki/` |
| `/apidocs` | API reference only | `docs/api/` |
| `/testplan` | Generate test plan | `reports/test_plan_*.md` |

---

## Quick Tips

- Most investigation workflows are **read-only**
- Reports go to `reports/`, wikis to `wiki/`
- Use `journal=nature` with `/peerreview` for journal-specific review
- Chain workflows: `/investigatecode` → `/trace` → `/hotspots`

2. **No output file** - displays in chat only.
