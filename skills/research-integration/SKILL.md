---
name: research-integration
description: Systematic research integration skill that processes academic papers, articles, and sources through a 9-step workflow - INTAKE, FETCH, ANALYZE, CONTEXTUALIZE, DOCUMENT, INDEX, IMPLEMENT, AUDIT, REPEAT - creating framework-ready research documents with actionable implementation templates and validated repository integrity
---

# Research Integration Skill

A systematic research processing skill designed to transform raw academic papers, articles, and information sources into structured, actionable research documents. This skill follows a rigorous 9-step workflow that ensures every piece of research is properly analyzed, contextualized, documented, validated, and integrated into a living knowledge repository.

## What This Skill Does

This skill acts as your research processing engine, transforming sources into actionable knowledge by:

1. **Systematic Processing** - Every source follows the same rigorous 9-step workflow
2. **Framework Contextualization** - Research is mapped to your specific use cases
3. **Compliance Verification** - Sources are checked against your ruling criteria
4. **Documentation Standards** - NASA-style documentation with full citations
5. **Implementation Bridge** - Theory documents generate practical implementation guides
6. **Quality Assurance** - AUDIT phase validates structure, corrects issues, merges repository
7. **Living Repository** - Index updates maintain a searchable knowledge base

## The 9-Step Research Workflow

```
1. INTAKE      → Receive source (URL, paper, article, document)
       ↓
2. FETCH       → Retrieve and extract content (WebFetch, Read, etc.)
       ↓
3. ANALYZE     → Extract core concepts, data, experimental results
       ↓
4. CONTEXTUALIZE → Map to framework, check compliance, identify applications
       │
       ├── 4.5 PARTIAL EXTRACTION → Extract value from rejected sources
       │
       └── 4.6 ADAPTIVE INTEGRATION → Transform philosophical failures into compliant implementations
       ↓
5. DOCUMENT    → Create Rxx research file with full structure
       ↓
6. INDEX       → Update master index with new entry
       ↓
7. IMPLEMENT   → If actionable, create implementation guide (Rxx+1)
       ↓
8. AUDIT       → Re-evaluate, verify structure, correct issues, merge repository
       ↓
9. REPEAT      → Ready for next source
```

## Workflow Step Details

### Step 1: INTAKE

**Purpose:** Receive and validate the research source

**Actions:**
- Receive URL, DOI, paper title, or document path
- Validate source accessibility
- Determine source type (academic paper, blog, documentation, etc.)
- Assign next research ID (Rxx)

**Output:** Validated source ready for fetching

### Step 2: FETCH

**Purpose:** Retrieve the full content of the source

**Actions:**
- Use WebFetch for URLs
- Use Read for local documents
- Extract abstract, methodology, results, conclusions
- Capture all relevant data tables and figures

**Output:** Raw content extracted and ready for analysis

### Step 3: ANALYZE

**Purpose:** Extract key insights and data from the source

**Analysis Framework:**
```
CORE CONCEPTS
├── Problem Statement: What problem does this solve?
├── Proposed Solution: What approach is introduced?
├── Key Innovation: What's new about this?
└── Experimental Validation: What proves it works?

DATA EXTRACTION
├── Benchmarks: Performance metrics and comparisons
├── Results Tables: Quantitative findings
├── Success Rates: Before/after comparisons
└── Limitations: Acknowledged constraints
```

**Output:** Structured analysis with key findings

### Step 4: CONTEXTUALIZE

**Purpose:** Map research to your specific framework and use cases

**Contextualization Process:**
```
FRAMEWORK MAPPING
├── Direct Applications: How does this apply to your work?
├── Integration Points: Where does this fit in your workflow?
├── Synergies: How does it combine with existing knowledge?
└── Gaps Filled: What problems does this solve for you?

COMPLIANCE CHECK
├── Factor 1: [Your first compliance criterion]
├── Factor 2: [Your second compliance criterion]
├── Factor 3: [Your third compliance criterion]
└── Overall: PASS/FAIL with reasoning
```

**Output:** Framework-specific applications and compliance status

### Step 4.5: PARTIAL EXTRACTION CHECK (Critical)

**Purpose:** Extract piecemeal value even from rejected sources

**The "School Analogy":** When you go to school, you don't utilize everything you learned - but pieces of that education prove extremely valuable later. Research works the same way.

**When a source fails full compliance but BEFORE full rejection:**

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
    ├── IF YES: Extract and integrate
    │   ├── Add to existing related document (as addendum)
    │   ├── Create "Extracted Insights" section
    │   ├── Cite the source for the specific insight
    │   └── Note what was extracted vs rejected
    │
    └── IF NO: Proceed with full rejection
```

**Extraction Categories:**

| Category | Example | Integration Target |
|----------|---------|-------------------|
| Prompt techniques | Speed descriptors, structure formulas | Add to implementation docs |
| Technical settings | FPS, blur values, parameters | Add to technical guides |
| Vocabulary | Domain-specific terms, camera moves | Add to reference sections |
| Benchmarks | Performance numbers, comparisons | Add to data tables |
| Failure modes | What doesn't work | Add to limitations sections |
| Best practices | Workflows from adjacent domains | Adapt to our workflow |

**Documentation of Partial Extraction:**

When extracting partial value, document:
```markdown
## PARTIAL EXTRACTION NOTE

**Source:** [Rejected source]
**Rejection Reason:** [Why full integration was rejected]
**Extracted Value:** [What was extracted]
**Integration Target:** [Where it was added]
**Date:** [Extraction date]
```

**Output:** Either extracted insights integrated into existing docs, or confirmed full rejection

### Step 4.6: ADAPTIVE INTEGRATION (Enhancement)

**Purpose:** Transform fixable failures into compliant implementations

**The Core Insight:** Some sources fail ONE factor due to philosophical design choices, not fundamental technical limitations. If the failing aspect can be REMOVED or MODIFIED without destroying core value, adaptation may yield a compliant result.

**When Adaptive Integration Applies:**

```
SOURCE FAILS 1-2 FACTORS
    │
    ├── Analyze WHY it failed
    │   ├── PHILOSOPHICAL failure (design choice)
    │   │   └── Example: "Never seek permission" = autonomy-first philosophy
    │   │
    │   └── FUNDAMENTAL failure (core to function)
    │       └── Example: Requires paid API = cannot make free
    │
    ├── IF PHILOSOPHICAL:
    │   ├── Can the philosophy be REMOVED while keeping patterns?
    │   ├── Can approval gates be ADDED at key points?
    │   ├── Does core value survive adaptation?
    │   │
    │   └── IF YES TO ALL:
    │       ├── Document original failure reason
    │       ├── Define specific adaptations required
    │       ├── Create adapted version specification
    │       ├── Re-evaluate adapted version against 3-Factor
    │       └── If 3/3 PASS → Proceed to implementation
    │
    └── IF FUNDAMENTAL:
        └── Proceed with Step 4.5 extraction only
```

**Adaptation Categories:**

| Original Issue | Adaptation Approach | Example |
|----------------|---------------------|---------|
| Autonomy-first | Add human approval gates | "Never seek permission" → require approval at deployments |
| Safety bypass mode | Remove entirely | "Ralph Wiggum Mode" → delete, don't adapt |
| Auto-execute patterns | Add confirmation steps | Auto-deploy → deploy-with-approval |
| Missing verification | Add verification phase | Straight to production → add VERIFY step |
| Wrong domain focus | Remap patterns to target domain | Startup dev patterns → content pipeline patterns |

**Adaptive Integration Document Structure:**

```markdown
## ADAPTIVE INTEGRATION ANALYSIS

**Original Source:** [Source name/URL]
**Original Score:** [X/3]
**Failed Factors:** [List]

### Failure Analysis

| Factor | Status | Failure Type | Adaptable? |
|--------|--------|--------------|------------|
| Factor 1 | PASS/FAIL | Philosophical/Fundamental | Yes/No |
| Factor 2 | PASS/FAIL | Philosophical/Fundamental | Yes/No |
| Factor 3 | PASS/FAIL | Philosophical/Fundamental | Yes/No |

### Proposed Adaptations

| Original Aspect | Adaptation | Rationale |
|-----------------|------------|-----------|
| [What failed] | [How to fix] | [Why this works] |

### Re-Evaluation (Post-Adaptation)

| Factor | Original | Adapted | Notes |
|--------|----------|---------|-------|
| Factor 1 | FAIL | PASS | [What changed] |
| Factor 2 | PASS | PASS | [Unchanged] |
| Factor 3 | PASS | PASS | [Unchanged] |

**Adapted Score:** [3/3]
**Action:** PROCEED TO IMPLEMENTATION / INFORMATIONAL ONLY / REJECT
```

**Critical Rules:**

1. **Never lower standards** - Adaptation makes sources MEET standards, not bypass them
2. **Document original failure** - Always record what failed before adaptation
3. **Verify core value survives** - Adaptation that destroys value is pointless
4. **Fundamental failures cannot be adapted** - Only philosophical failures qualify
5. **Re-evaluation is mandatory** - Adapted version must pass fresh 3-Factor check

**Output:** Adapted specification ready for implementation, OR determination that adaptation is not possible

### Step 5: DOCUMENT

**Purpose:** Create a comprehensive research document

**Document Structure:**
```markdown
# RESEARCH: [TITLE]

**Research ID:** Rxx-[PROJECT]-[YEAR]
**Date Compiled:** [DATE]
**Source:** [CITATION]
**Category:** [CATEGORY]

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
### 4.1 Benchmark 1
### 4.2 Benchmark 2
### 4.3 Summary of Results

## 5. FRAMEWORK APPLICATION
### 5.1 Direct Applications
### 5.2 Integration Examples
### 5.3 Workflow Enhancement

## 6. IMPLEMENTATION STRATEGIES
### 6.1 Prompt Templates (if applicable)
### 6.2 When to Use
### 6.3 When to Skip

## 7. COMPLIANCE CHECK
### 7.1 Assessment
### 7.2 Integration Notes

## 8. LIMITATIONS & CONSIDERATIONS

## 9. SOURCE CITATIONS

## 10. KEY TAKEAWAYS

## 11. INTEGRATION STATUS

---

**Research Status:** COMPLETE
**Applicability:** [HIGH/MEDIUM/LOW]
**Last Updated:** [DATE]
```

**Output:** Complete Rxx research document

### Step 6: INDEX

**Purpose:** Update the master research index

**Index Update Actions:**
- Add new entry to appropriate section
- Update document count
- Update combined statistics
- Set last updated date

**Index Entry Format:**
```markdown
| Rxx | [Document Title](Rxx_Filename.md) | Topics covered |
```

**Output:** Updated 00_RESEARCH_INDEX.md

### Step 7: IMPLEMENT

**Purpose:** Create actionable implementation documents if applicable

**Decision Tree:**
```
Is the research actionable?
├── YES (provides methods, prompts, workflows)
│   └── Create Rxx+1 Implementation Document
│       ├── Production-ready templates
│       ├── Copy-paste prompts
│       ├── Step-by-step workflows
│       └── Usage guidelines
│
└── NO (purely theoretical)
    └── Note in integration status
    └── Mark for future reference
```

**Implementation Document Structure:**
```markdown
# [TOPIC] IMPLEMENTATION LIBRARY

**Research ID:** Rxx+1-[PROJECT]-[YEAR]
**Date Compiled:** [DATE]
**Dependency:** Rxx_[Theory Document]
**Category:** Production Tools - Ready to Deploy

---

## OVERVIEW
[Brief description of what this implements]

## 1. [WORKFLOW/PROMPT 1] (Priority: HIGH)
### 1.1 Standard Version
[Full template/prompt]

### 1.2 Variant Version
[Alternative for specific cases]

## 2. [WORKFLOW/PROMPT 2] (Priority: HIGH)
...

## N. USAGE GUIDELINES
### When to Use Which
### Integration with Other Research

## CHECKLIST
| Workflow | Tested | Refined | In Use |
```

**Output:** Complete implementation document (if applicable)

### Step 8: AUDIT

**Purpose:** Re-evaluate, verify structure, correct issues, and merge repository

The AUDIT step ensures research quality and repository integrity through a 4-phase validation process:

**Phase 1: RE-EVALUATE (Document Audit)**
```
For each newly created document (Rxx, Rxx+1):
├── Compare against template structure
├── Verify all required sections present
├── Check for missing data points
│   ├── All experimental results included?
│   ├── Scaling/fine-tuning results (if in source)?
│   ├── Ablation studies (if in source)?
│   ├── Failure cases/limitations?
│   └── Future work mentioned?
└── Identify gaps requiring correction
```

**Phase 2: STRUCTURE (Template Compliance)**
```
Verify document structure matches template:
├── Section 1: Paper Overview (citation, abstract, prior work)
├── Section 2: Core Problem (limitations, tasks affected)
├── Section 3: Framework/Solution (concept, components, process)
├── Section 4: Experimental Results (ALL benchmarks, summary)
├── Section 5: Framework Application (applications, examples, workflow)
├── Section 6: Implementation (prompts, when to use/skip)
├── Section 7: Compliance Check (factors, notes)
├── Section 8: Limitations (with mitigations)
├── Section 9: Source Citations (primary, related, implementation)
├── Section 10: Key Takeaways (numbered, comprehensive)
├── Section 11: Integration Status (points, priorities)
└── Section 12+: Relationship diagrams (if applicable)
```

**Phase 3: CORRECT (Fix Issues)**
```
For each issue identified:
├── Missing section → Add section with extracted data
├── Incomplete data → Supplement from source
├── Structural error → Reformat to match template
├── Missing takeaways → Add based on key findings
└── Verify fix applied correctly
```

**Phase 4: MERGE (Repository Integrity)**
```
Verify repository consistency:
├── Index Entry
│   ├── New document listed in correct section
│   ├── Topics accurately described
│   └── Link format correct
├── Statistics Updated
│   ├── Total document count
│   ├── Section counts (Core vs Advanced)
│   ├── Word count estimate
│   ├── Citation count
│   └── Data table count
├── Structure Diagram
│   └── File tree reflects current state
├── Cross-References
│   ├── Related research linked
│   └── Dependency chains documented
└── Status Consistency
    └── All status fields aligned (ACTIVE/COMPLETE)
```

**Audit Checklist:**
```
□ Document has all 11+ required sections
□ All experimental results from source captured
□ Scaling/fine-tuning results included (if present in source)
□ Key takeaways count matches significant findings
□ Index entry added with correct format
□ Document count updated
□ Word/citation/table counts updated
□ Structure diagram reflects new files
□ Cross-references to related research added
□ Status consistency verified
```

**Output:** Validated, corrected documents and consistent repository

### Step 9: REPEAT

**Purpose:** Prepare for next research source

**Actions:**
- Confirm all files written successfully
- Confirm AUDIT passed with no remaining issues
- Summarize what was added
- Identify related research opportunities
- Ready for next INTAKE

**Output:** Summary and readiness confirmation

## When to Use This Skill

**For New Research:**
- Processing academic papers (arXiv, journals, conferences)
- Integrating blog posts and technical articles
- Documenting tool/platform research
- Capturing industry benchmarks

**For Knowledge Management:**
- Building a searchable research repository
- Creating implementation libraries
- Maintaining living documentation
- Tracking research evolution

**For Team Collaboration:**
- Standardizing research documentation
- Sharing knowledge systematically
- Building institutional memory
- Onboarding new team members

## Example Invocations

### Process Academic Paper
```
@research-integration

Source: https://arxiv.org/abs/2305.10601
Framework: DeadManAI
Compliance Criteria: 3-Factor Ruling
Output Location: G:\DeadManAI_Research\
```

### Process Blog Post
```
@research-integration

Source: https://example.com/technical-article
Framework: [Your Framework Name]
Quick Mode: Yes (skip implementation doc)
```

### Batch Process Multiple Sources
```
@research-integration

Sources:
1. https://arxiv.org/abs/xxxx.xxxxx
2. https://arxiv.org/abs/yyyy.yyyyy
3. https://example.com/article

Framework: [Your Framework Name]
Starting ID: R15
```

## Input Format

```json
{
  "source": "URL or file path",
  "source_type": "paper|article|documentation|video",
  "framework_name": "Your framework name",
  "compliance_criteria": [
    "Factor 1: Description",
    "Factor 2: Description",
    "Factor 3: Description"
  ],
  "output_location": "Path to research folder",
  "starting_id": "R15",
  "create_implementation": true,
  "update_index": true
}
```

## Output Format

**For Each Source Processed:**

```json
{
  "research_id": "R15",
  "title": "Research document title",
  "files_created": [
    "R15_Topic_Research.md",
    "R16_Topic_Implementation.md"
  ],
  "index_updated": true,
  "compliance_status": "PASS",
  "applicability": "HIGH",
  "next_id": "R17",
  "related_opportunities": [
    "Paper X builds on this",
    "Topic Y is related"
  ]
}
```

## Research Document Quality Standards

### Required Sections
- [ ] Full citation with authors, date, source
- [ ] Problem statement and solution overview
- [ ] Data tables with specific numbers
- [ ] Framework-specific applications
- [ ] Compliance verification
- [ ] Implementation status
- [ ] Key takeaways (numbered list)

### Formatting Standards
- [ ] NASA-style documentation
- [ ] Consistent table formatting
- [ ] Code blocks for prompts/templates
- [ ] Proper markdown hierarchy
- [ ] Source citations throughout

### Implementation Document Standards
- [ ] Copy-paste ready prompts
- [ ] Priority levels assigned
- [ ] Usage guidelines included
- [ ] Integration notes provided
- [ ] Testing checklist included

## Integration with Other Skills

This skill works well combined with:
- **Content Trend Researcher** - Find sources worth researching
- **Prompt Factory** - Generate prompts from research
- **CLAUDE.md Enhancer** - Document research in project context

## Best Practices

1. **Process Immediately** - Research while context is fresh
2. **Be Thorough** - Extract all relevant data points
3. **Contextualize Deeply** - Map to your specific use cases
4. **Implement When Possible** - Theory without practice fades
5. **Index Everything** - Findability is survival
6. **Link Related Research** - Build a knowledge graph
7. **Update Regularly** - Research evolves
8. **Extract Before Rejecting** - Even rejected sources may contain valuable pieces (Step 4.5)
9. **Mine Adjacent Domains** - Techniques from related fields often transfer
10. **Document What You Extracted** - Track partial extractions for future reference

## Limitations

- Requires source to be accessible (no paywalls without access)
- WebFetch may not extract all content from complex pages
- Implementation docs require understanding of practical applications
- Index updates require existing index structure

## Technical Notes

- Uses WebFetch for URL content extraction
- Creates markdown files with consistent structure
- Updates JSON-style metadata in index
- Follows kebab-case for file naming
- Preserves original source citations

## Philosophy

```
Research informs strategy.
Strategy drives execution.
Execution generates data.
Data enables research.

The cycle never stops.
```

---

**Version**: 1.3.0
**Last Updated**: 2026-01-02
**Compatibility**: Claude Code, Claude.ai, Claude API
**Origin**: DeadManAI Research Workflow
**Changelog**:
- v1.3.0 - Added Step 4.6 ADAPTIVE INTEGRATION (transform philosophical failures into compliant implementations)
- v1.2.0 - Added Step 4.5 PARTIAL EXTRACTION CHECK (extract value from rejected sources)
- v1.1.0 - Added Step 8 AUDIT (re-eval, structure, correct, merge)

