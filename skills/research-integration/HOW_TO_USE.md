# How to Use the Research Integration Skill

This guide walks you through using the research-integration skill to process sources into actionable knowledge.

---

## Quick Start

### 1. Invoke the Skill

```
@research-integration

Source: https://arxiv.org/abs/2305.10601
Framework: MyProject
Output: G:\MyProject_Research\
```

### 2. Follow the 9-Step Workflow

The skill will guide you through:
1. **INTAKE** - Validate and identify the source
2. **FETCH** - Retrieve full content
3. **ANALYZE** - Extract key insights
4. **CONTEXTUALIZE** - Map to your framework
5. **DOCUMENT** - Create research file (Rxx)
6. **INDEX** - Update master index
7. **IMPLEMENT** - Create implementation doc (if applicable)
8. **AUDIT** - Re-evaluate, verify structure, correct issues, merge repository
9. **REPEAT** - Ready for next source

---

## Complete Walkthrough Example

### The Source

Let's process the Tree of Thoughts paper: `https://arxiv.org/abs/2305.10601`

### Step 1: INTAKE

**You say:**
```
@research-integration

Source: https://arxiv.org/abs/2305.10601
Framework: DeadManAI
Compliance: 3-Factor Ruling
Output: G:\DeadManAI_Research\
Starting ID: R13
```

**Skill validates:**
- Source is accessible (arXiv URL)
- Source type: Academic paper
- Research ID: R13

### Step 2: FETCH

**Skill action:**
```
WebFetch: https://arxiv.org/abs/2305.10601
Prompt: Extract title, authors, abstract, methodology, results, conclusions
```

**Result:** Raw paper content extracted including:
- Title: Tree of Thoughts: Deliberate Problem Solving with Large Language Models
- Authors: Yao et al.
- Experimental results on Game of 24, Creative Writing, Crosswords

### Step 3: ANALYZE

**Skill extracts:**

```
CORE CONCEPTS
├── Problem: LLMs use linear token-by-token reasoning
├── Solution: Branch, evaluate, backtrack reasoning paths
├── Innovation: Self-evaluation of reasoning quality
└── Validation: 74% vs 4% on Game of 24

DATA EXTRACTION
├── Game of 24: 74% (ToT) vs 4% (CoT)
├── Creative Writing: 7.56 (ToT) vs 6.93 (CoT)
├── Crosswords: ~60% (ToT) vs ~16% (CoT)
└── Limitations: Higher compute cost
```

### Step 4: CONTEXTUALIZE

**Skill maps to framework:**

```
DEADMANAI APPLICATIONS
├── Hook Generation: Branch hook types, evaluate retention
├── Title Optimization: Generate variations, score CTR
├── Script Structure: Explore narrative paths, select best
└── Thumbnail Concepts: Branch designs, evaluate CTR

COMPLIANCE CHECK (3-Factor Ruling)
├── Factor 1 (Human-in-Loop): PASS - Human reviews branches
├── Factor 2 (Retention Velocity): PASS - Improves creative output
└── Factor 3 (Asset Reusability): PASS - Creates reusable templates
```

### Step 5: DOCUMENT

**Skill creates:** `G:\DeadManAI_Research\R13_Tree_of_Thoughts_LLM_Reasoning.md`

Full document with:
- Complete citation
- Problem/solution analysis
- Experimental results tables
- DeadManAI-specific applications
- Compliance verification
- Integration status
- 10 key takeaways

### Step 6: INDEX

**Skill updates:** `G:\DeadManAI_Research\00_RESEARCH_INDEX.md`

```markdown
### ADVANCED RESEARCH (Ongoing)

| ID | Document | Topics Covered |
|----|----------|----------------|
| R13 | [Tree of Thoughts](R13_Tree_of_Thoughts.md) | ToT framework, branching reasoning |

---

| Total Documents | 13 |
```

### Step 7: IMPLEMENT

**Skill determines:** Research is actionable (provides prompt patterns)

**Skill creates:** `G:\DeadManAI_Research\R14_ToT_Prompt_Implementation_Library.md`

Contains:
- Hook Generation ToT prompt (copy-paste ready)
- Title Optimization ToT prompt
- Topic Selection ToT prompt
- Script Structure ToT prompt
- Thumbnail Concept ToT prompt
- Usage guidelines

**Skill updates index:** Document count now 14

### Step 8: AUDIT

**Skill performs 4-phase validation:**

```
PHASE 1: RE-EVALUATE
├── Compare R13 against template structure
├── Check for missing data points
│   ├── All experimental results? ✓
│   ├── Scaling results (if in source)? ✓
│   └── Key takeaways complete? ✓
└── Result: No gaps identified

PHASE 2: STRUCTURE
├── Section 1: Paper Overview ✓
├── Section 2: Core Problem ✓
├── Section 3: Framework/Solution ✓
├── Section 4: Experimental Results ✓
├── Section 5: Framework Application ✓
├── Section 6: Implementation ✓
├── Section 7: Compliance Check ✓
├── Section 8: Limitations ✓
├── Section 9: Source Citations ✓
├── Section 10: Key Takeaways (10 items) ✓
└── Section 11: Integration Status ✓

PHASE 3: CORRECT
└── No corrections needed

PHASE 4: MERGE (Repository Integrity)
├── Index entry correct ✓
├── Document count updated (12 → 14) ✓
├── Statistics updated ✓
├── Structure diagram current ✓
└── Status consistency verified ✓

AUDIT RESULT: PASS
```

### Step 9: REPEAT

**Skill confirms:**
```
RESEARCH CYCLE COMPLETE

Files Created:
├── R13_Tree_of_Thoughts_LLM_Reasoning.md
└── R14_ToT_Prompt_Implementation_Library.md

Index Updated:
├── Document count: 12 → 14
└── New section: Advanced Research (Ongoing)

Audit Status: PASSED (all 4 phases)

Related Opportunities:
├── ReAct (reasoning + acting)
├── Reflexion (learning from failures)
└── Self-Consistency (voting on paths)

Ready for next INTAKE.
```

---

## Configuration Options

### Basic Configuration

```json
{
  "source": "https://arxiv.org/abs/xxxx.xxxxx",
  "framework_name": "MyProject",
  "output_location": "G:\\MyProject_Research\\",
  "starting_id": "R01"
}
```

### Advanced Configuration

```json
{
  "source": "https://arxiv.org/abs/xxxx.xxxxx",
  "source_type": "paper",
  "framework_name": "MyProject",
  "compliance_criteria": [
    "Factor 1: Must allow human oversight",
    "Factor 2: Must improve efficiency",
    "Factor 3: Must create reusable assets"
  ],
  "output_location": "G:\\MyProject_Research\\",
  "starting_id": "R15",
  "create_implementation": true,
  "update_index": true,
  "analysis_depth": "deep"
}
```

### Quick Mode (Skip Implementation)

```json
{
  "source": "https://example.com/article",
  "framework_name": "MyProject",
  "output_location": "G:\\MyProject_Research\\",
  "quick_mode": true
}
```

---

## Common Use Cases

### 1. Processing Academic Papers

```
@research-integration

Source: https://arxiv.org/abs/2210.03629
Type: Academic paper
Framework: MyProject
Depth: Full (include implementation doc)
```

### 2. Processing Technical Articles

```
@research-integration

Source: https://blog.example.com/technical-guide
Type: Article
Framework: MyProject
Depth: Quick (research doc only)
```

### 3. Batch Processing

```
@research-integration

Batch Mode: Yes
Sources:
1. https://arxiv.org/abs/2305.10601 (ToT)
2. https://arxiv.org/abs/2210.03629 (ReAct)
3. https://arxiv.org/abs/2303.11366 (Reflexion)

Framework: MyProject
Starting ID: R13
```

### 4. Processing Existing Documents

```
@research-integration

Source: G:\Documents\research_paper.pdf
Type: Local document
Framework: MyProject
```

---

## Setting Up Your Research Repository

### Initial Setup

1. Create your research folder:
```bash
mkdir "G:\MyProject_Research"
```

2. Create the index file:
```markdown
# MYPROJECT RESEARCH REPOSITORY

## DOCUMENT INDEX

| ID | Document | Topics |
|----|----------|--------|
| (empty - first research will populate) |

## DOCUMENT STATISTICS

| Total Documents | 0 |
| Last Updated | YYYY-MM-DD |
```

3. Define your compliance criteria:
```
Factor 1: [Your first requirement]
Factor 2: [Your second requirement]
Factor 3: [Your third requirement]
```

### First Research Document

Process your first source:
```
@research-integration

Source: [Your first source URL]
Framework: MyProject
Initialize: Yes
Output: G:\MyProject_Research\
```

The skill will:
- Create R01 document
- Initialize the index structure
- Set up document statistics

---

## Customizing Templates

### Modify Document Structure

Edit `templates.md` to change:
- Section headings
- Required fields
- Formatting preferences

### Add Custom Compliance Factors

Update your invocation:
```
@research-integration

Compliance:
  - Factor 1: Security - Must not expose sensitive data
  - Factor 2: Performance - Must not degrade system performance
  - Factor 3: Maintainability - Must include documentation
```

---

## Tips for Best Results

### 1. Be Specific About Framework Applications

Instead of: "Map to my project"
Say: "Map to content creation workflow focusing on hooks, titles, and thumbnails"

### 2. Extract All Data Points

Request: "Include all experimental results with specific percentages"

### 3. Request Implementation Docs

If research is actionable: "Create implementation document with copy-paste prompts"

### 4. Build Knowledge Graphs

Track relationships: "Note connections to R13 and R14"

### 5. Update Regularly

Set a schedule: "Review and update research quarterly"

---

## Troubleshooting

### Source Not Accessible

```
Error: Unable to fetch source content

Solutions:
1. Check URL is correct
2. Verify no paywall blocking access
3. Try alternative source (e.g., PDF instead of HTML)
4. Provide local copy if available
```

### Index Not Found

```
Error: 00_RESEARCH_INDEX.md not found

Solutions:
1. Initialize with "Initialize: Yes"
2. Create manually using template
3. Specify correct output location
```

### Implementation Not Generated

```
Note: No implementation document created

Reasons:
1. Research is purely theoretical
2. quick_mode was enabled
3. No actionable prompts/workflows found

Solutions:
1. Request explicitly: "create_implementation: true"
2. Provide more context about applications
```

---

## Integration Examples

### With Content Trend Researcher

```
Step 1: Use content-trend-researcher to find topics
Step 2: Use research-integration to process relevant papers
Step 3: Apply findings to content strategy
```

### With Prompt Factory

```
Step 1: Process research with research-integration
Step 2: Use prompt-factory to generate prompts based on findings
Step 3: Test and refine prompts
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-01-01 | Initial release |
| 1.1.0 | 2026-01-01 | Added Step 8 AUDIT (re-eval, structure, correct, merge) |

---

**Skill:** research-integration
**Version:** 1.1.0
**Last Updated:** 2026-01-01

