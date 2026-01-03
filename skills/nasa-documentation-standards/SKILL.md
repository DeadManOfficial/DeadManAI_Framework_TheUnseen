---
name: nasa-documentation-standards
description: FOUNDATIONAL BEHAVIORAL SKILL - NASA-style documentation standards based on official NASA procedural requirements (NPR 7120, NPR 7123, NPR 8735). Governs ALL work output with lifecycle phases, technical reviews, QA/QC, IV&V, configuration management, and lessons learned. Non-negotiable SOP basis for DeadManAI.
priority: CRITICAL
scope: GLOBAL
type: behavioral
version: 2.0.0
sources:
  - NPR 7120.5F (Space Flight Program/Project Management)
  - NPR 7123.1D (Systems Engineering Processes)
  - NPR 8735.2C (Quality Assurance)
  - NASA Systems Engineering Handbook (NASA/SP-2016-6105)
  - KSC-DF-107 (Technical Documentation Style Guide)
  - NASA Lessons Learned Information System (LLIS)
---

# NASA DOCUMENTATION STANDARDS v2.0

## FOUNDATIONAL DIRECTIVE

**THIS SKILL IS NON-NEGOTIABLE. IT APPLIES TO ALL WORK. NO EXCEPTIONS.**

This behavioral standard is derived from official NASA procedural requirements and governs how we operate. Every document, research file, implementation guide, and output follows these standards based on NASA's proven methodologies for mission-critical documentation.

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│   "If it's not documented, it didn't happen."                  │
│   "If it's not structured, it's not useful."                   │
│   "If it's not verifiable, it's not trustworthy."              │
│   "If it's not reviewed, it's not ready."                      │
│                                                                │
│                    // DEADMANAI SOP //                         │
│                    Based on NASA NPR 7120/7123                 │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## PART I: NASA LIFECYCLE FRAMEWORK

### 1.1 Lifecycle Phases (Per NPR 7120.5F)

NASA defines two major lifecycle phases: **Formulation** and **Implementation**.

```
NASA LIFECYCLE MODEL (Adapted for DeadManAI)
═══════════════════════════════════════════

FORMULATION PHASE                    IMPLEMENTATION PHASE
├── Pre-Phase A: Concept Studies     ├── Phase C: Final Design & Fabrication
├── Phase A: Concept Development     ├── Phase D: Assembly, Integration, Test
└── Phase B: Preliminary Design      ├── Phase E: Operations
                                     └── Phase F: Closeout

DeadManAI Mapping:
──────────────────
FORMULATION                          IMPLEMENTATION
├── Research (Rxx)                   ├── Implementation Docs (Rxx+1)
├── Analysis                         ├── Production Workflows
└── Design/Planning                  ├── Deployment
                                     └── Iteration/Optimization
```

### 1.2 Key Decision Points (KDPs)

| NASA KDP | Purpose | DeadManAI Equivalent |
|----------|---------|---------------------|
| KDP A | Approve concept studies | Source INTAKE decision |
| KDP B | Approve preliminary design | CONTEXTUALIZE compliance check |
| KDP C | Approve final design | DOCUMENT approval |
| KDP D | Approve operations | INDEX and deployment |

### 1.3 Phase Products

**Per NPR 7120.5F Appendix I - Required Products by Phase:**

| Phase | NASA Products | DeadManAI Products |
|-------|---------------|-------------------|
| Pre-A | Mission Concept Review materials | Source evaluation notes |
| A | System Requirements Review materials | Research analysis (Sections 1-3) |
| B | Preliminary Design Review materials | Full Rxx document draft |
| C | Critical Design Review materials | Implementation doc (Rxx+1) |
| D | Test plans, verification matrix | Checklist, testing status |
| E | Operations procedures | Production workflows |
| F | Lessons learned, closeout report | Integration status, updates |

---

## PART II: TECHNICAL REVIEW GATES

### 2.1 Review Types (Per NPR 7123.1D Appendix G)

NASA uses defined technical reviews with **entrance criteria** and **success criteria**.

```
REVIEW GATE SEQUENCE
════════════════════

    ┌─────┐     ┌─────┐     ┌─────┐     ┌─────┐     ┌─────┐
    │ SRR │────▶│ SDR │────▶│ PDR │────▶│ CDR │────▶│ ORR │
    └─────┘     └─────┘     └─────┘     └─────┘     └─────┘
       │           │           │           │           │
    System      System     Preliminary  Critical   Operational
   Require-    Definition    Design      Design     Readiness
    ments                   Review      Review      Review
```

### 2.2 Review Definitions

| Review | NASA Definition | DeadManAI Application |
|--------|-----------------|----------------------|
| **SRR** (System Requirements Review) | Examines functional and performance requirements | Source analysis complete, requirements understood |
| **SDR** (System Definition Review) | Examines proposed architecture and flow-down | Framework mapping complete, compliance assessed |
| **PDR** (Preliminary Design Review) | Demonstrates preliminary design meets requirements | Draft document with all sections present |
| **CDR** (Critical Design Review) | Demonstrates design maturity for full fabrication | Final document ready for deployment |
| **ORR** (Operational Readiness Review) | Confirms readiness for operations | Implementation tested, indexed, deployed |

### 2.3 Entrance and Success Criteria

**Adapted from NPR 7123.1D Appendix G:**

#### Document Creation - Entrance Criteria
```
□ Source has been fetched and content extracted
□ 3-Factor compliance assessment initiated
□ Document ID assigned (Rxx)
□ Template structure prepared
□ Prior related research identified
```

#### Document Creation - Success Criteria
```
□ All 11+ mandatory sections complete
□ All claims have citations
□ All data tables formatted correctly
□ Key takeaways numbered (5-12 items)
□ Integration status documented
□ Limitations acknowledged
□ Cross-references to related research added
□ Index entry prepared
```

#### Implementation Doc - Entrance Criteria
```
□ Theory document (Rxx) marked COMPLETE
□ Actionable workflows identified
□ Templates/prompts defined
□ Priority levels assigned
```

#### Implementation Doc - Success Criteria
```
□ All workflows have copy-paste ready templates
□ Usage guidelines included
□ Integration notes provided
□ Testing checklist present
□ Dependency on theory doc cited
```

---

## PART III: QUALITY ASSURANCE (QA/QC)

### 3.1 QA Program Requirements (Per NPR 8735.2C)

NASA's QA program ensures products meet mission objectives through systematic quality engineering and assurance practices.

**Core QA Principles:**
1. Quality assurance is applied through reviews of documentation and processes
2. All uses of QA surveillance are risk-based
3. Records shall be legible, traceable, identifiable, and readily retrievable
4. Verification demonstrates achievement of specified characteristics

### 3.2 DeadManAI QA Framework

```
QA VERIFICATION MATRIX
══════════════════════

REQUIREMENT                          VERIFICATION METHOD
─────────────────────────────────────────────────────────
All sections present                 Structure audit
Citations for all claims             Source verification
Tables for comparisons               Format inspection
Code blocks for templates            Format inspection
Numbered takeaways                   Count verification
Index entry added                    Repository check
Statistics updated                   Count verification
Cross-references complete            Link verification
```

### 3.3 Quality Checkpoints

**Checkpoint 1: Structure Verification**
```
□ Document has correct header format
□ Research ID follows Rxx-PROJECT-YEAR pattern
□ All 11+ mandatory sections present
□ No empty sections (use "N/A" or "TBD")
□ Proper markdown hierarchy (H1 → H2 → H3)
```

**Checkpoint 2: Content Verification**
```
□ Abstract accurately summarizes source
□ Problem statement clearly defined
□ Solution/framework completely described
□ All experimental data captured
□ All benchmarks included with sources
□ Framework application specific to DeadManAI
```

**Checkpoint 3: Citation Verification**
```
□ Primary source URL/DOI provided
□ All data tables cite sources
□ All benchmarks have attribution
□ Related research cross-referenced
□ No orphan claims (uncited statements)
```

**Checkpoint 4: Format Verification**
```
□ Tables use correct markdown syntax
□ Code blocks specify language
□ ASCII diagrams render correctly
□ Lists use appropriate type (numbered/bullet)
□ Headers follow hierarchy
```

**Checkpoint 5: Completeness Verification**
```
□ Key takeaways count matches significant findings
□ Integration status table complete
□ Limitations section addresses constraints
□ Next actions specified
□ Status fields set (COMPLETE/IN PROGRESS)
```

---

## PART IV: INDEPENDENT VERIFICATION & VALIDATION (IV&V)

### 4.1 IV&V Principles (Per NASA IV&V Program)

NASA established IV&V to provide highest achievable safety and effectiveness. IV&V answers two questions:

| Question | Focus | Method |
|----------|-------|--------|
| **"Are we building the product right?"** | Verification | Check compliance with requirements |
| **"Are we building the right product?"** | Validation | Check if product meets mission needs |

### 4.2 Independence Parameters (Per IEEE)

| Parameter | Definition | DeadManAI Application |
|-----------|------------|----------------------|
| **Technical Independence** | Assessment independent of developer | AUDIT step reviews with fresh perspective |
| **Managerial Independence** | Separate from development org | Step 8 AUDIT is distinct from Steps 1-7 |
| **Financial Independence** | Budget separate from development | Time allocated specifically for review |

### 4.3 AUDIT Step (IV&V Implementation)

**Step 8 AUDIT serves as our IV&V process:**

```
AUDIT PROCESS (IV&V)
════════════════════

Phase 1: RE-EVALUATE (Verification)
├── Compare document against template
├── Verify all required sections present
├── Check for missing data points
└── Identify gaps requiring correction

Phase 2: STRUCTURE (Compliance Check)
├── Section 1: Paper Overview - present?
├── Section 2: Core Problem - present?
├── Section 3: Framework/Solution - present?
├── Section 4: Experimental Results - present?
├── Section 5: Framework Application - present?
├── Section 6: Implementation Strategies - present?
├── Section 7: Compliance Check - present?
├── Section 8: Limitations - present?
├── Section 9: Source Citations - present?
├── Section 10: Key Takeaways - present?
├── Section 11: Integration Status - present?
└── Section 12+: Relationships - if applicable?

Phase 3: CORRECT (Fix Issues)
├── Missing section → Add with extracted data
├── Incomplete data → Supplement from source
├── Structural error → Reformat to template
└── Missing takeaways → Add based on findings

Phase 4: MERGE (Validation)
├── Index entry correct?
├── Statistics updated?
├── Structure diagram current?
├── Cross-references complete?
└── Status consistency verified?
```

---

## PART V: CONFIGURATION MANAGEMENT

### 5.1 CM Standard (Per NASA-STD-0005)

NASA Configuration Management provides systematic method to:
- Identify configuration at various points in time
- Systematically control changes
- Maintain integrity and traceability
- Preserve records throughout lifecycle

### 5.2 Configuration Baselines

**NASA defines four baselines (adapted for DeadManAI):**

| Baseline | NASA Definition | DeadManAI Equivalent |
|----------|-----------------|---------------------|
| **Functional** | Performance requirements at SRR | Source requirements understood |
| **Allocated** | Extended requirements at PDR | Document structure allocated |
| **Product** | Final configuration in production | Completed Rxx document |
| **As-Deployed** | Operational configuration at ORR | Indexed and integrated document |

### 5.3 Change Control

```
CHANGE CONTROL PROCESS
══════════════════════

Change Proposed
      │
      ▼
┌─────────────────┐
│ Evaluate Impact │
│ - Structure     │
│ - Content       │
│ - References    │
│ - Index         │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Approve/Reject  │
│ Document reason │
└────────┬────────┘
         │
    ┌────┴────┐
    │         │
    ▼         ▼
Implement   Archive
  Change    Rejection
    │       Reason
    ▼
Update Version
Update Index
Verify Integrity
```

### 5.4 Version Control

| Document Type | Version Format | When to Increment |
|---------------|----------------|-------------------|
| Research (Rxx) | Date-based (Last Updated) | Any content change |
| Skill | Semantic (MAJOR.MINOR.PATCH) | Per change type |
| Index | Date-based | Any entry change |

---

## PART VI: TECHNICAL WRITING STANDARDS

### 6.1 Core Principles (Per KSC-DF-107)

NASA's Technical Documentation Style Guide promotes writing that is:
- **Clear** - Unambiguous meaning
- **Concise** - No unnecessary words
- **Accurate** - Factually correct
- **Consistent** - Same terms throughout
- **Organized** - Logical structure
- **Usable** - Reader can act on it

### 6.2 Writing Rules

**Rule 1: Choose Shorter Words**
```
AVOID                    USE
─────────────────────────────────────
utilize                  use
demonstrate              show
implement                do, make
facilitate               help
subsequent               next
prior to                 before
in order to              to
```

**Rule 2: Choose Fewer Words**
```
AVOID                    USE
─────────────────────────────────────
at this point in time    now
in the event that        if
due to the fact that     because
for the purpose of       to, for
in spite of the fact     although
has the capability to    can
```

**Rule 3: Use Active Voice**
```
PASSIVE (avoid)          ACTIVE (use)
─────────────────────────────────────
The report was written   We wrote the report
It was determined that   We determined
Tests were conducted     We conducted tests
```

**Rule 4: One Idea Per Sentence**
```
AVOID: The system processes data and generates reports while
       maintaining logs and the user can configure settings.

USE:   The system processes data. It generates reports.
       It maintains logs. Users can configure settings.
```

### 6.3 Formatting Standards

**Numbers:**
- Spell out numbers ten or less (one, two, three...)
- Use numerals for 11 and above (11, 12, 13...)
- Always use numerals with units (5 GB, 3 seconds)
- Use numerals in tables

**Lists:**
- Use same bullet style throughout (solid black)
- Always use serial comma (a, b, and c)
- Keep parallel structure in list items

**Headings:**
- Use title case for H1, H2 (Capitalize Major Words)
- Use sentence case for H3, H4 (Capitalize first word only)
- No periods at end of headings

**Tables:**
- Always include header row
- Align numbers right, text left
- Include units in headers, not cells

---

## PART VII: LESSONS LEARNED

### 7.1 LLIS Requirements (Per NPR 7120.6)

NASA's Lessons Learned Information System captures knowledge to:
- Reduce risk
- Improve efficiency
- Promote validated practices
- Improve performance

### 7.2 Lesson Criteria

A lesson must be:

| Criterion | Definition | Verification |
|-----------|------------|--------------|
| **Significant** | Real or assumed impact on operations | Does it change how we work? |
| **Valid** | Factually and technically correct | Can it be verified? |
| **Applicable** | Identifies specific design/process/decision | Can it be applied? |

### 7.3 Lessons Learned Lifecycle

```
LESSONS LEARNED PROCESS
═══════════════════════

    COLLECT          RECORD           DISSEMINATE        APPLY
       │                │                  │               │
       ▼                ▼                  ▼               ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│ Identify    │  │ Document    │  │ Share via   │  │ Integrate   │
│ during work │──▶│ in standard │──▶│ repository  │──▶│ into        │
│             │  │ format      │  │ and index   │  │ practice    │
└─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘
```

### 7.4 DeadManAI Lessons Learned

**Capture Points:**
- Step 4.5 Partial Extraction (what was extracted from rejected sources)
- Step 8 AUDIT (issues found and corrected)
- Implementation testing (what worked/didn't work)

**Documentation Format:**
```markdown
## LESSON LEARNED

**Date:** [YYYY-MM-DD]
**Source:** [Where lesson originated]
**Category:** [Research/Implementation/Process]

**Situation:** [What happened]
**Impact:** [Why it matters]
**Recommendation:** [What to do differently]
**Status:** [APPLIED/PENDING]
```

---

## PART VIII: DOCUMENT STRUCTURE STANDARDS

### 8.1 Research Documents (Rxx)

**MANDATORY SECTIONS - ALL MUST BE PRESENT:**

```
# RESEARCH: [TITLE IN CAPS]

**Research ID:** Rxx-[PROJECT]-[YEAR]
**Date Compiled:** [YYYY-MM-DD]
**Source:** [URL or Citation]
**Category:** [Category Name]

---

## 1. PAPER OVERVIEW
### 1.1 Citation
### 1.2 Abstract Summary
### 1.3 Connection to Prior Work

## 2. CORE PROBLEM IDENTIFIED
### 2.1 Limitations Addressed
### 2.2 Tasks Affected

## 3. PROPOSED FRAMEWORK/SOLUTION
### 3.1 Core Concept
### 3.2 Key Components
### 3.3 Process/Algorithm

## 4. EXPERIMENTAL RESULTS
### 4.1 Benchmark Data
### 4.2 Comparison Tables
### 4.3 Summary of Results

## 5. FRAMEWORK APPLICATION
### 5.1 Direct Applications
### 5.2 Integration Examples
### 5.3 Workflow Enhancement

## 6. IMPLEMENTATION STRATEGIES
### 6.1 Templates/Prompts
### 6.2 When to Use
### 6.3 When to Skip

## 7. COMPLIANCE CHECK
### 7.1 Assessment
### 7.2 Integration Notes

## 8. LIMITATIONS & CONSIDERATIONS

## 9. SOURCE CITATIONS

## 10. KEY TAKEAWAYS

## 11. INTEGRATION STATUS

## 12. RELATIONSHIP TO OTHER RESEARCH (if applicable)

---

**Research Status:** [COMPLETE/IN PROGRESS/DRAFT]
**Applicability:** [HIGH/MEDIUM/LOW]
**Recommended Action:** [Next step]
**Last Updated:** [YYYY-MM-DD]
```

### 8.2 Implementation Documents (Rxx+1)

```
# [TOPIC] IMPLEMENTATION LIBRARY

**Research ID:** Rxx+1-[PROJECT]-[YEAR]
**Date Compiled:** [YYYY-MM-DD]
**Dependency:** Rxx_[Theory Document]
**Category:** Production Tools - Ready to Deploy

---

## OVERVIEW
[Brief description]

## 1. [WORKFLOW 1] (Priority: HIGH/MEDIUM/LOW)
### 1.1 Standard Version
### 1.2 Variant Versions

## 2. [WORKFLOW 2] (Priority: HIGH/MEDIUM/LOW)
...

## N. USAGE GUIDELINES
### When to Use Which
### Integration with Other Research

## CHECKLIST
| Workflow | Tested | Refined | In Use |
|----------|--------|---------|--------|

---

**Document Status:** [READY/DRAFT]
**Last Updated:** [YYYY-MM-DD]
```

### 8.3 Index Documents

```
# [REPOSITORY NAME] INDEX

## REPOSITORY OVERVIEW
**Project:** [Name]
**Purpose:** [Description]
**Compiled:** [Date]
**Status:** [ACTIVE/ARCHIVED]

---

## DOCUMENT INDEX

### [CATEGORY 1]
| ID | Document | Topics Covered |
|----|----------|----------------|

### [CATEGORY 2]
...

---

## KEY DATA POINTS
[Quick reference tables]

---

## DOCUMENT STATISTICS
| Metric | Value |
|--------|-------|
| Total Documents | X |
| Word Count | ~X |
| Citations | X+ |
| Last Updated | [Date] |

---

## STRUCTURE DIAGRAM
```
[Repository]/
├── [File 1]
├── [File 2]
└── [Folder]/
```

---

**Repository Status:** [ACTIVE]
**Last Updated:** [YYYY-MM-DD]
```

---

## PART IX: COMPLIANCE FRAMEWORK

### 9.1 3-Factor Ruling

| Factor | Question | Requirement |
|--------|----------|-------------|
| **Factor 1: Human-in-Loop** | Does human control the process? | MUST PASS |
| **Factor 2: Retention Velocity** | Does it improve content quality? | MUST PASS |
| **Factor 3: Asset Reusability** | Does it create reusable assets? | MUST PASS |

**Scoring:**
- 3/3 = PASS (Full integration)
- 2/3 = CONDITIONAL (Requires justification)
- 1/3 or 0/3 = FAIL (Partial extraction only)

### 9.2 Partial Extraction (Step 4.5)

```
SOURCE FAILS FULL COMPLIANCE
    │
    ├── STOP: Do not immediately reject
    │
    ├── ASK: "Is there ANY extractable value?"
    │   ├── Data points or benchmarks?
    │   ├── Techniques or methodologies?
    │   ├── Prompt engineering insights?
    │   ├── Technical settings or parameters?
    │   ├── Vocabulary or terminology?
    │   ├── Failure modes to avoid?
    │   ├── Best practices from adjacent domain?
    │   └── Research citations worth following?
    │
    ├── IF YES: Extract and document
    │   ├── Add to existing related document
    │   ├── Create "Partial Extraction" section
    │   ├── Cite source for specific insight
    │   └── Note what was extracted vs rejected
    │
    └── IF NO: Proceed with full rejection
```

---

## PART X: ENFORCEMENT

### 10.1 Automatic Application

This skill is automatically applied. There is no opt-out.

### 10.2 Document Creation Workflow

```
1. IDENTIFY document type
2. APPLY corresponding template
3. COMPLETE all sections
4. RUN QA checkpoints (1-5)
5. EXECUTE AUDIT (IV&V)
6. UPDATE index and statistics
7. SET status to COMPLETE
```

### 10.3 Non-Compliance Response

| Issue | Response |
|-------|----------|
| Missing sections | Document marked INCOMPLETE, revision required |
| Uncited claims | Claims removed or sources added |
| Format errors | Reformatting required before use |
| Index not updated | Update required before marking complete |

---

## PART XI: SOURCES AND REFERENCES

### 11.1 Primary NASA Sources

| Document | Title | URL |
|----------|-------|-----|
| NPR 7120.5F | Space Flight Program/Project Management | [NODIS Library](https://nodis3.gsfc.nasa.gov/displayDir.cfm?t=NPR&c=7120&s=5F) |
| NPR 7123.1D | Systems Engineering Processes | [NODIS Library](https://nodis3.gsfc.nasa.gov/displayDir.cfm?Internal_ID=N_PR_7123_001D_) |
| NPR 8735.2C | Quality Assurance Program | [NODIS Library](https://nodis3.gsfc.nasa.gov/displayDir.cfm?t=NPR&c=8735&s=2C) |
| NASA/SP-2016-6105 | Systems Engineering Handbook | [NASA Reference](https://www.nasa.gov/reference/systems-engineering-handbook/) |
| KSC-DF-107 | Technical Documentation Style Guide | [NASA Standards](https://standards.nasa.gov/standard/KSC/KSC-DF-107) |
| NASA-STD-0005 | Configuration Management Standard | [NASA Standards](https://standards.nasa.gov/standard/NASA/NASA-STD-0005) |
| LLIS | Lessons Learned Information System | [NASA LLIS](https://llis.nasa.gov/) |

### 11.2 Related Standards

| Standard | Purpose |
|----------|---------|
| NPR 7150.2 | Software Engineering Requirements |
| NPR 8621.1 | Mishap Reporting and Lessons Learned |
| EIA-649 | Configuration Management |
| IEEE IV&V | Independent Verification & Validation |

---

## VERSION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-01-01 | Initial foundational skill creation |
| 2.0.0 | 2026-01-01 | Expanded with official NASA methodology (NPR 7120, 7123, 8735), added lifecycle phases, review gates, IV&V, CM, technical writing standards, lessons learned |

---

**Skill Status:** ACTIVE
**Scope:** GLOBAL - ALL WORK
**Priority:** CRITICAL - NON-NEGOTIABLE
**Type:** Behavioral Foundation
**Based On:** NASA Procedural Requirements (NPR)

---

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│   Structure enables excellence.                                │
│   Documentation enables continuity.                            │
│   Standards enable scale.                                      │
│   Verification enables trust.                                  │
│   Lessons enable improvement.                                  │
│                                                                │
│   This is not optional. This is how we operate.                │
│                                                                │
│                    // THE UNSEEN //                            │
│                    Per NASA NPR 7120/7123/8735                 │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```
