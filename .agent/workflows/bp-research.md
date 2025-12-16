---
description: Research a topic with evidence-based findings and structured citations.
---

# bp-research

## Description

Research a topic and capture findings in a structured `RESEARCH.md`. Follows evidence-based research practices with quality ratings and proper citations.

## Steps

1. Use the text after `/bp-research` as the research question; ask clarifying questions if scope or deliverables are unclear.

2. Search the workspace for an existing `RESEARCH.md` (including `tasks/` subdirectories).

3. If `RESEARCH.md` already exists, ask the user whether to:
   - Overwrite it
   - Create a new task directory like `tasks/<short-name>/RESEARCH.md`
   - Move work to a new VCS branch/workspace

4. Conduct research using:
   - User-provided links and documents (primary)
   - Repo context and existing code (primary)
   - Web search for external references (secondary)
   - Documentation and official sources (secondary)

5. Create `RESEARCH.md` with this comprehensive structure:

```markdown
# Research: [Topic]

> Research conducted: [date] | Researcher: [name/agent]

## Research Question

**Primary Question**: [Main question being investigated]

**Sub-questions**:
1. [Related question 1]
2. [Related question 2]

**Scope**: [What's in/out of scope]

---

## Executive Summary

[3-5 bullet points summarizing key findings]

- Finding 1
- Finding 2
- Finding 3

**Recommendation**: [High-level recommendation based on research]

---

## Methodology

| Source Type | Sources Consulted | Notes |
|-------------|-------------------|-------|
| Official Docs | [list] | |
| Academic Papers | [list] | |
| Community Resources | [list] | |
| Codebase Analysis | [files examined] | |
| Expert Input | [if any] | |

---

## Key Findings

### Finding 1: [Title]

**Summary**: [One paragraph summary]

**Evidence**:
| Source | Claim | Quality | Notes |
|--------|-------|---------|-------|
| [Source 1] | [What it says] | ⭐⭐⭐ High | [context] |
| [Source 2] | [What it says] | ⭐⭐ Medium | [context] |

**Confidence Level**: High / Medium / Low

**Implications**: [What this means for the project]

---

### Finding 2: [Title]

[Same structure]

---

## Comparison Matrix

[If comparing options/technologies]

| Criterion | Option A | Option B | Option C | Winner |
|-----------|----------|----------|----------|--------|
| Performance | ⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐ | A, C |
| Ease of Use | ⭐⭐ | ⭐⭐⭐ | ⭐⭐ | B |
| Community | ⭐⭐⭐ | ⭐⭐⭐ | ⭐ | A, B |
| Cost | Free | Free | Paid | A, B |
| **Overall** | **8/12** | **9/12** | **7/12** | **B** |

---

## Decision Matrix

[For making recommendations]

| Factor | Weight | Option A | Option B | Option C |
|--------|--------|----------|----------|----------|
| Fits requirements | 30% | 3 (0.9) | 2 (0.6) | 3 (0.9) |
| Team familiarity | 25% | 2 (0.5) | 3 (0.75) | 1 (0.25) |
| Long-term viability | 20% | 3 (0.6) | 3 (0.6) | 2 (0.4) |
| Implementation effort | 15% | 2 (0.3) | 3 (0.45) | 2 (0.3) |
| Cost | 10% | 3 (0.3) | 3 (0.3) | 2 (0.2) |
| **Weighted Total** | | **2.6** | **2.7** | **2.05** |

**Recommendation**: Option B

---

## Assumptions

| Assumption | Basis | Risk if Wrong |
|------------|-------|---------------|
| [Assumption 1] | [Why we assume this] | [Impact] |
| [Assumption 2] | [Why we assume this] | [Impact] |

---

## Open Questions

| Question | Importance | How to Resolve |
|----------|------------|----------------|
| [Question 1] | High | [Action needed] |
| [Question 2] | Medium | [Action needed] |

---

## Knowledge Gaps

Areas where more research is needed:

- [ ] [Gap 1] - [What would help]
- [ ] [Gap 2] - [What would help]

---

## Risks Identified

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | Medium | High | [How to address] |
| [Risk 2] | Low | Medium | [How to address] |

---

## Recommendations

### Primary Recommendation

[Detailed recommendation with rationale]

### Alternative Approaches

1. **Alternative A**: [Description] - [When to consider]
2. **Alternative B**: [Description] - [When to consider]

---

## References

### Primary Sources (High Confidence)

1. [Author/Org]. "[Title]." [Publication/Site], [Date]. [URL]
   - Key insight: [What we learned]
   - Quality: ⭐⭐⭐

2. [Author/Org]. "[Title]." [Publication/Site], [Date]. [URL]
   - Key insight: [What we learned]
   - Quality: ⭐⭐⭐

### Secondary Sources (Medium Confidence)

3. [Author/Org]. "[Title]." [Publication/Site], [Date]. [URL]
   - Key insight: [What we learned]
   - Quality: ⭐⭐

### Community/Informal Sources (Lower Confidence)

4. [Forum/Discussion]. "[Topic]." [URL]
   - Key insight: [What we learned]
   - Quality: ⭐
   - Note: Verify before relying on this

---

## Appendix

### Raw Notes

[Detailed notes, quotes, code snippets collected during research]

### Related Files in Codebase

| File | Relevance |
|------|-----------|
| `src/existing.py` | [How it relates] |

```

6. Apply evidence quality ratings:
   - ⭐⭐⭐ **High**: Official documentation, peer-reviewed, primary sources
   - ⭐⭐ **Medium**: Reputable blogs, well-maintained OSS, expert opinions
   - ⭐ **Low**: Forums, outdated content, unverified claims

7. Present a short summary and ask the user to confirm the research is sufficient.

8. Recommend the next step: `/bp-requirements` or `/bp-plan`.

## Output

- `RESEARCH.md` (structured research document)

## Standards Reference

- **Evidence-Based Practice**: Quality ratings and source verification
- **CRAAP Test**: Currency, Relevance, Authority, Accuracy, Purpose for source evaluation
- **Chicago/IEEE Citation**: Structured reference format
