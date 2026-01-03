# Research Integration Templates

Ready-to-use templates for each step of the research workflow.

---

## TEMPLATE 1: Research Document (Rxx)

```markdown
# RESEARCH: [TITLE IN CAPS]

**Research ID:** Rxx-[PROJECT]-[YEAR]
**Date Compiled:** [YYYY-MM-DD]
**Source:** [arXiv:xxxx.xxxxx / URL / Citation]
**Category:** [Category - Subcategory]

---

## 1. PAPER OVERVIEW

### 1.1 Citation

**Title:** [Full Paper Title]

**Authors:** [Author List]

**Institutions:** [Institution List]

**Published:** [Month Year] ([Conference/Journal if applicable])

**arXiv/DOI:** [Link]

### 1.2 Abstract Summary

[2-3 sentence summary of what the paper does]

### 1.3 Connection to Prior Work

| Paper | Relationship |
|-------|--------------|
| [Prior Work 1] | [How this builds on it] |
| [Prior Work 2] | [How this differs] |

---

## 2. CORE PROBLEM IDENTIFIED

### 2.1 Limitations Addressed

**Current Approach:**
```
[Diagram or description of existing approach]
```

**Problems:**
| Issue | Description |
|-------|-------------|
| [Problem 1] | [Description] |
| [Problem 2] | [Description] |

### 2.2 Tasks Affected

Tasks that suffer from these limitations:
- [Task 1]
- [Task 2]
- [Task 3]

---

## 3. PROPOSED FRAMEWORK/SOLUTION

### 3.1 Core Concept

**Approach:**
```
[Diagram or description of new approach]
```

### 3.2 Key Components

| Component | Function |
|-----------|----------|
| [Component 1] | [What it does] |
| [Component 2] | [What it does] |

### 3.3 Process/Algorithm

```
Step 1: [Description]
Step 2: [Description]
Step 3: [Description]
```

---

## 4. EXPERIMENTAL RESULTS

### 4.1 [Benchmark/Task 1]

**Task:** [Description]

**Results:**
| Method | Metric |
|--------|--------|
| Baseline | XX% |
| Proposed | XX% |

**Key Finding:** [Interpretation]

### 4.2 [Benchmark/Task 2]

[Same structure]

### 4.3 Summary of Results

| Benchmark | Improvement |
|-----------|-------------|
| [Task 1] | +XX% |
| [Task 2] | +XX% |

---

## 5. FRAMEWORK APPLICATION: [YOUR FRAMEWORK]

### 5.1 Direct Applications

| Framework Area | Application | Benefit |
|----------------|-------------|---------|
| [Area 1] | [How to apply] | [Why it helps] |
| [Area 2] | [How to apply] | [Why it helps] |

### 5.2 Integration Examples

**Example 1: [Use Case]**
```
[Specific example of how to use this]
```

### 5.3 Workflow Enhancement

```
Before: [Old workflow]
After: [Enhanced workflow with this research]
```

---

## 6. IMPLEMENTATION STRATEGIES

### 6.1 Prompt/Template

```
[Ready-to-use prompt or template]
```

### 6.2 When to Use

**Use When:**
- [Condition 1]
- [Condition 2]

**Skip When:**
- [Condition 1]
- [Condition 2]

---

## 7. COMPLIANCE CHECK

### 7.1 Assessment

| Factor | Status | Reasoning |
|--------|--------|-----------|
| [Factor 1] | PASS/FAIL | [Why] |
| [Factor 2] | PASS/FAIL | [Why] |
| [Factor 3] | PASS/FAIL | [Why] |

### 7.2 Integration Notes

- [Note about how this fits your framework]
- [Any caveats or considerations]

---

## 8. LIMITATIONS & CONSIDERATIONS

| Limitation | Mitigation |
|------------|------------|
| [Limitation 1] | [How to work around it] |
| [Limitation 2] | [How to work around it] |

---

## 9. SOURCE CITATIONS

### Primary Source
1. [Full citation]

### Related Work
2. [Citation]
3. [Citation]

### Implementation Resources
4. [GitHub, documentation, etc.]

---

## 10. KEY TAKEAWAYS

1. **[Key Point 1]** - [Brief explanation]
2. **[Key Point 2]** - [Brief explanation]
3. **[Key Point 3]** - [Brief explanation]
[Continue to 10]

---

## 11. INTEGRATION STATUS

| Integration Point | Status | Priority |
|-------------------|--------|----------|
| [Point 1] | Ready/Pending/N/A | HIGH/MED/LOW |
| [Point 2] | Ready/Pending/N/A | HIGH/MED/LOW |

---

**Research Status:** COMPLETE
**Applicability:** HIGH/MEDIUM/LOW
**Recommended Action:** [What to do next]
**Last Updated:** [DATE]
```

---

## TEMPLATE 2: Implementation Document (Rxx+1)

```markdown
# [TOPIC] IMPLEMENTATION LIBRARY

**Research ID:** Rxx-[PROJECT]-[YEAR]
**Date Compiled:** [YYYY-MM-DD]
**Dependency:** Rxx_[Source Research Document].md
**Category:** Production Tools - Ready to Deploy

---

## OVERVIEW

This document contains production-ready [prompts/workflows/templates] for [framework name] based on [source research]. Each [item] has been structured for immediate use.

**Key Difference from [Source]:**
- [Theory document] = Understanding (what/why)
- [This document] = Application (how)

**Usage:** Copy-paste directly or follow workflow steps.

---

## 1. [WORKFLOW/PROMPT 1] (Priority: HIGH)

### 1.1 Standard Version

```
[Full prompt or workflow - copy-paste ready]
```

### 1.2 [Variant] Version

Use when [specific condition].

```
[Variant prompt or workflow]
```

---

## 2. [WORKFLOW/PROMPT 2] (Priority: HIGH)

### 2.1 Standard Version

```
[Full prompt or workflow]
```

---

## 3. [WORKFLOW/PROMPT 3] (Priority: MEDIUM)

[Continue pattern...]

---

## N. USAGE GUIDELINES

### When to Use Which

| Situation | Use | Priority |
|-----------|-----|----------|
| [Situation 1] | [Workflow X] | HIGH |
| [Situation 2] | [Workflow Y] | MEDIUM |

### Integration with Other Research

**Combined Workflow:**
```
PHASE 1: [Research A]
├── [Workflow from A]
└── Output: [What it produces]

PHASE 2: [Research B]
├── [Workflow from B]
└── Output: [What it produces]
```

---

## CHECKLIST

| Workflow | Tested | Refined | In Use |
|----------|--------|---------|--------|
| 1.1 [Name] | [ ] | [ ] | [ ] |
| 1.2 [Name] | [ ] | [ ] | [ ] |
| 2.1 [Name] | [ ] | [ ] | [ ] |

---

**Document Status:** READY FOR DEPLOYMENT
**Next Action:** Test workflows on real production tasks
**Last Updated:** [DATE]
```

---

## TEMPLATE 3: Research Index Entry

**Add to 00_RESEARCH_INDEX.md:**

```markdown
| Rxx | [Document Title](Rxx_Filename.md) | Topic 1, topic 2, topic 3 |
```

**Update document count:**
```markdown
| Total Documents | [NEW COUNT] |
```

---

## TEMPLATE 4: Index Structure (00_RESEARCH_INDEX.md)

```markdown
# [PROJECT] RESEARCH REPOSITORY

---

## REPOSITORY OVERVIEW

**Project:** [Project Name]
**Purpose:** [What this repository contains]
**Compiled:** [Initial date]
**Status:** ACTIVE

---

## DOCUMENT INDEX

### CORE RESEARCH (R01-Rxx)

| ID | Document | Topics Covered |
|----|----------|----------------|
| R01 | [Title](R01_File.md) | Topics |

### ADVANCED RESEARCH (Ongoing)

| ID | Document | Topics Covered |
|----|----------|----------------|
| Rxx | [Title](Rxx_File.md) | Topics |

---

## KEY DATA POINTS

### Quick Reference

| Metric | Value |
|--------|-------|
| [Metric 1] | [Value] |

---

## DOCUMENT STATISTICS

| Metric | Value |
|--------|-------|
| Total Documents | XX |
| Combined Word Count | ~XX,000+ |
| Source Citations | XX+ |
| Research Date | [Date] |

---

**Repository Status:** ACTIVE
**Last Updated:** [DATE]
```

---

## TEMPLATE 5: Compliance Check

```markdown
## COMPLIANCE CHECK

### [Your Ruling/Framework Name]

| Factor | Requirement | Status | Evidence |
|--------|-------------|--------|----------|
| Factor 1 | [What must be true] | PASS/FAIL | [Why] |
| Factor 2 | [What must be true] | PASS/FAIL | [Why] |
| Factor 3 | [What must be true] | PASS/FAIL | [Why] |

**Overall Status:** COMPLIANT / NON-COMPLIANT / PARTIAL

**Notes:**
- [Any caveats or conditions]
```

---

## TEMPLATE 6: AUDIT Checklist (Step 8)

Use this template to validate research documents before completing the cycle.

```markdown
## AUDIT CHECKLIST

**Document:** Rxx_[Name].md
**Audit Date:** [DATE]

### PHASE 1: RE-EVALUATE (Document Completeness)

| Check | Status | Notes |
|-------|--------|-------|
| All experimental results from source captured | ☐ | |
| Scaling/fine-tuning results included (if present) | ☐ | |
| Ablation studies captured (if present) | ☐ | |
| Failure cases/limitations documented | ☐ | |
| Future work mentioned (if in source) | ☐ | |
| Key takeaways count matches findings | ☐ | |

### PHASE 2: STRUCTURE (Template Compliance)

| Section | Present | Complete | Notes |
|---------|---------|----------|-------|
| 1. Paper Overview | ☐ | ☐ | |
| 2. Core Problem | ☐ | ☐ | |
| 3. Framework/Solution | ☐ | ☐ | |
| 4. Experimental Results | ☐ | ☐ | |
| 5. Framework Application | ☐ | ☐ | |
| 6. Implementation Strategies | ☐ | ☐ | |
| 7. Compliance Check | ☐ | ☐ | |
| 8. Limitations | ☐ | ☐ | |
| 9. Source Citations | ☐ | ☐ | |
| 10. Key Takeaways | ☐ | ☐ | |
| 11. Integration Status | ☐ | ☐ | |
| 12. Relationship Diagram | ☐ | ☐ | |

### PHASE 3: CORRECT (Issues Found)

| Issue | Location | Fix Applied | Verified |
|-------|----------|-------------|----------|
| [Issue 1] | [Section] | ☐ | ☐ |
| [Issue 2] | [Section] | ☐ | ☐ |

### PHASE 4: MERGE (Repository Integrity)

| Check | Status | Notes |
|-------|--------|-------|
| Index entry added correctly | ☐ | |
| Topics accurately described | ☐ | |
| Link format correct | ☐ | |
| Total document count updated | ☐ | |
| Section counts updated (Core/Advanced) | ☐ | |
| Word count estimate updated | ☐ | |
| Citation count updated | ☐ | |
| Data table count updated | ☐ | |
| Structure diagram reflects new files | ☐ | |
| Cross-references added | ☐ | |
| Status consistency verified | ☐ | |

---

**AUDIT RESULT:** PASS / FAIL

**Issues Remaining:** [None / List issues]

**Auditor Notes:**
[Any additional observations]
```

---

## TEMPLATE 7: Research Summary (End of Workflow)

```markdown
## Research Cycle Complete

**Source:** [Citation]
**Processing Date:** [Date]

### Files Created

| File | Purpose |
|------|---------|
| Rxx_[Name].md | Theory/research document |
| Rxx+1_[Name].md | Implementation document |

### Index Updated

- Document count: [Old] → [New]
- New section: [If applicable]

### Integration Status

| Area | Ready | Priority |
|------|-------|----------|
| [Area 1] | Yes/No | HIGH/MED/LOW |

### Related Research Opportunities

- [Paper/topic that builds on this]
- [Related area to explore]

### Next Source

Ready for next INTAKE.
```

---

**Templates Version:** 1.1.0
**Last Updated:** 2026-01-01
**Changelog:** v1.1.0 - Added TEMPLATE 6: AUDIT Checklist

