# Journal Profiles

This directory contains profile templates for academic journals. Each profile defines journal-specific requirements and review priorities for use with the `/peerreview` workflow.

## Available Profiles

| Journal | File | Focus |
|---------|------|-------|
| Nature | `nature.md` | High-impact, broad audience, novelty |
| PLOS ONE | `plos_one.md` | Technical soundness, reproducibility |
| BMJ | `bmj.md` | Clinical relevance, patient outcomes |
| Nature Human Behaviour | `nature_human_behaviour.md` | Behavioral science, pre-registration |

## Profile Structure

Each profile includes:
- **Scope & Mission**: What the journal publishes
- **Manuscript Limits**: Word counts, figures, references
- **Emphasis Areas**: What reviewers prioritize
- **Common Rejection Reasons**: Frequent issues
- **Review Priorities**: Questions reviewers ask
- **Formatting Notes**: Specific requirements

## Adding Custom Profiles

Create a new `.md` file following the existing format:

```markdown
# [Journal Name]

## Scope & Mission
[What the journal publishes]

## Manuscript Limits
| Element | Limit |
|---------|-------|
| ... | ... |

## Emphasis Areas
- [Priority 1]
- [Priority 2]

## Common Rejection Reasons
- [Reason 1]
- [Reason 2]

## Review Priorities
1. [Key question]
2. [Key question]

## Formatting Notes
- [Requirement]
```

## Usage

```bash
/peerreview journal=nature
/peerreview journal=plos_one
/peerreview journal=bmj
```

If no journal is specified, a general academic review is performed.
