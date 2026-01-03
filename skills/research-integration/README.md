# Research Integration Skill

Systematic research processing through a 9-step workflow: INTAKE, FETCH, ANALYZE, CONTEXTUALIZE, DOCUMENT, INDEX, IMPLEMENT, AUDIT, REPEAT.

## Quick Install

**Claude Code (User-level):**
```bash
cp -r research-integration ~/.claude/skills/
```

**Claude Code (Project-level):**
```bash
cp -r research-integration .claude/skills/
```

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Main skill definition |
| `templates.md` | Ready-to-use document templates |
| `HOW_TO_USE.md` | Detailed usage guide |
| `README.md` | This file |

## Quick Start

```
@research-integration

Source: https://arxiv.org/abs/2305.10601
Framework: MyProject
Output: G:\MyProject_Research\
```

## The 9-Step Workflow

```
1. INTAKE      → Receive source
2. FETCH       → Extract content
3. ANALYZE     → Find key insights
4. CONTEXTUALIZE → Map to your framework
5. DOCUMENT    → Create Rxx file
6. INDEX       → Update master index
7. IMPLEMENT   → Create implementation doc (if actionable)
8. AUDIT       → Re-eval, structure check, correct, merge
9. REPEAT      → Ready for next
```

## The AUDIT Phase (Step 8)

The AUDIT phase ensures quality through 4 sub-phases:
- **RE-EVAL** - Compare document against template, check for missing data
- **STRUCTURE** - Verify all required sections present
- **CORRECT** - Fix any issues identified
- **MERGE** - Ensure repository integrity (index, stats, diagrams)

## Origin

This skill was developed from the DeadManAI research workflow, processing papers like Tree of Thoughts, ReAct, and Graph of Thoughts into actionable frameworks.

---

**Version:** 1.1.0
**Created:** 2026-01-01
**Updated:** 2026-01-01 - Added AUDIT phase

