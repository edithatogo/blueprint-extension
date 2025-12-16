---
description: Simulate peer review by editor and expert reviewers for a target journal.
---

# peerreview

## Description

Simulate the academic peer review process for a manuscript. Generates feedback from multiple reviewer perspectives (Editor, Statistical Reviewer, Domain Expert, Methods Specialist) tailored to a target journal's standards.

## Inputs

- **Manuscript** (optional): Path to manuscript file (auto-detected if not specified).
- **Journal** (optional): Target journal name (e.g., "Nature", "PLOS ONE", "BMJ"). Loads journal-specific profile if available.
- **Focus** (optional): Specific aspects to emphasize (e.g., "statistics", "methods", "novelty").
- **Reviewers** (optional): Which reviewers to simulate (default: all). Options: `editor`, `stats`, `domain`, `methods`.

## Steps

1. **Locate manuscript**:
   - Search for manuscript files (`.md`, `.docx`, `.tex`)
   - Identify the primary/latest version
   - If multiple found, ask user to specify

2. **Load journal profile** (if specified):
   - Check for `journal_profiles/<journal>.md` or use defaults
   - Note: word limits, reference style, emphasis areas, common concerns

3. **Read and analyze manuscript**:
   - Title, abstract, keywords
   - Introduction: background, objectives, hypothesis
   - Methods: design, participants, procedures, analysis
   - Results: findings, tables, figures
   - Discussion: interpretation, limitations, implications
   - References: count, recency, relevance

4. **Simulate Editor-in-Chief review**:
   - Assess scope fit for target journal
   - Evaluate significance and novelty
   - Check ethical compliance signals (IRB mention, data availability, COI)
   - Overall impression and preliminary decision

5. **Simulate Statistical Reviewer (Reviewer 1)**:
   - Sample size and power considerations
   - Appropriateness of statistical methods
   - Handling of assumptions and violations
   - Clarity of statistical reporting
   - Reproducibility of analyses

6. **Simulate Domain Expert (Reviewer 2)**:
   - Accuracy of background and literature
   - Validity of interpretations
   - Comparison with existing work
   - Clinical/practical relevance
   - Missing considerations

7. **Simulate Methods Specialist (Reviewer 3)**:
   - Protocol completeness
   - Reproducibility (could another researcher replicate?)
   - Data/code availability
   - Figure and table quality
   - Supplementary materials adequacy

8. **Synthesize feedback**:
   - Consolidate major concerns across reviewers
   - Prioritize issues by severity
   - Formulate overall recommendation

9. **Create the reports directory** if it doesn't exist:
   ```bash
   mkdir -p reports
   ```

10. **Write review report** to `reports/peer_review_<manuscript>_<YYYYMMDD-HHMM>.md`:
    ```markdown
    # Peer Review Report
    
    **Manuscript**: [Title]
    **Journal**: [Target Journal]
    **Date**: [Review Date]
    
    ## Editorial Decision
    **Recommendation**: [Accept / Minor Revision / Major Revision / Reject]
    **Summary**: [2-3 sentence rationale]
    
    ## Editor's Assessment
    [scope, significance, ethics, overall]
    
    ## Reviewer 1: Statistical Methods
    ### Major Concerns
    ### Minor Issues
    ### Strengths
    
    ## Reviewer 2: Domain Expertise
    [same structure]
    
    ## Reviewer 3: Methods & Reproducibility
    [same structure]
    
    ## Consolidated Action Items
    | # | Issue | Reviewer | Section | Action Required |
    |---|-------|----------|---------|-----------------|
    
    ## Journal-Specific Notes
    [requirements for target journal]
    ```

11. **Present summary** with key findings and report path.

12. **Offer next steps**:
    - Use `/validateclaims` to verify specific claims
    - Use `/checkfigures` to audit reproducibility
    - Use `/citationaudit` to check references

## Output

- `reports/peer_review_<manuscript>_<YYYYMMDD-HHMM>.md`

## Examples

```
/peerreview
/peerreview manuscript/draft_v3.md
/peerreview journal=Nature
/peerreview focus=statistics reviewers=stats,methods
```

## Journal Profiles

Place custom journal profiles in `journal_profiles/` directory:

```markdown
# journal_profiles/nature.md

## Nature

### Scope
- Significant advances of interest to broad scientific audience
- Novel findings with major implications

### Limits
- Main text: ~3000 words (excluding methods)
- Figures: 4-6 (plus Extended Data)
- References: ~50

### Emphasis
- Novelty and significance (primary criterion)
- Broad impact across disciplines
- Exceptional rigor

### Common Concerns
- "Incremental advance" - must show paradigm shift
- "Specialist interest only" - must appeal broadly
- Missing mechanistic insight
```

Default profiles are provided for common journals.
