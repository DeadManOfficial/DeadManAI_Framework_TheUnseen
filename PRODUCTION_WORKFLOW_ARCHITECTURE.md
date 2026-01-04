# PRODUCTION WORKFLOW ARCHITECTURE: DeadManAI // The Unseen

**Document ID:** PROD-ARCH-DeadManAI-2026-v1.0
**Date Created:** 2026-01-03
**Category:** Production Framework Architecture
**Status:** ACTIVE - FOUNDATIONAL DOCUMENT
**Compliance:** NASA NPR 7120.5E (Program Management), NPR 7123.1C (Systems Engineering), NPR 8735.2C (Technical Excellence)

---

## 1. EXECUTIVE SUMMARY

### 1.1 Document Purpose

This document defines the complete end-to-end production workflow architecture for DeadManAI // The Unseen, a faceless YouTube content creation system. It provides the operational blueprint for transforming ideas into published, multi-platform content while maintaining quality standards, scalability, and human creative direction.

**Coverage:**
- 7-phase production lifecycle (Ideation → Distribution)
- Multi-platform strategy (YouTube primary, TikTok/Instagram/Twitch secondary)
- Complete tool stack with alternatives and decision matrices
- 4-gate quality control system
- Human-in-loop enforcement points
- Asset reusability framework
- Scalability path (1 video/week → daily production)
- Team structure evolution (solo → production team)

### 1.2 Integration with Research Foundation

**Source Research Documents:** R01-R64 (Complete DeadManAI Research Repository)

**Key Dependencies:**
- R63: Niche Selection & Viral Mechanics (Strategic foundation)
- R36-R64: Production Research Synthesis (Operational procedures)
- R28-R29: Fabric AI Patterns (Automation framework)
- R13-R18: LLM Reasoning (AI augmentation methods)
- CLAUDE.md: NASA Standards & Session Continuity (Quality framework)

### 1.3 Workflow Performance Targets

| Metric | Solo Creator | Small Team (2-3) | Production Team (4+) |
|--------|--------------|------------------|---------------------|
| **Production Time/Video** | 3-4 hours | 2-3 hours | 1.5-2 hours |
| **Weekly Output** | 1-2 videos | 3-4 videos | 5-7 videos |
| **Quality Score (CTR × AVD)** | 2.5-3.5% | 3.0-4.0% | 3.5-5.0% |
| **Factual Error Rate** | <0.2 per video | <0.1 per video | <0.05 per video |
| **Time to Market** | 5-7 days | 3-5 days | 1-3 days |

**Mission Alignment:** All workflows enforce 3-Factor Ruling (Human-in-Loop ✓ | Retention Velocity ✓ | Asset Reusability ✓)

---

## 2. ARCHITECTURAL OVERVIEW

### 2.1 Production Lifecycle Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DEADMANAI PRODUCTION WORKFLOW                         │
│                         7-PHASE ARCHITECTURE                             │
└─────────────────────────────────────────────────────────────────────────┘

PHASE 1: IDEATION & VALIDATION
├─ Niche Selection (R63 Framework)
├─ Topic Research (Perplexity + VidIQ)
├─ Viral Potential Assessment (STEPPS + K-factor)
└─ GATE 1: Strategic Validation
    ↓
PHASE 2: RESEARCH & SCRIPTING
├─ Research Stream (Perplexity + Fabric extract_wisdom)
├─ Script Outlining (Claude + Template Library)
├─ First Draft Generation (Claude + ChatGPT)
└─ GATE 2: Completeness Check
    ↓
PHASE 3: VERIFICATION & REFINEMENT
├─ Fact-Checking (Originality.ai + Manual)
├─ Citation Integration (Source compilation)
├─ Polish & Consistency (Trinka AI + Claude)
└─ GATE 3: Fact Integrity
    ↓
PHASE 4: VISUAL PRODUCTION
├─ Thumbnail Design (Canva + A/B Testing)
├─ B-roll Sourcing (Stock + AI generation)
├─ Animation & Motion Graphics (After Effects / Resolve Fusion)
└─ GATE 4: Production Readiness
    ↓
PHASE 5: AUDIO PRODUCTION
├─ Voice Generation (ElevenLabs + Processing)
├─ Music Selection (Epidemic Sound / Artlist)
├─ Audio Mixing (DAW: Reaper / Audition)
└─ Audio QA: LUFS -14 to -16
    ↓
PHASE 6: EDITING & POST-PRODUCTION
├─ Video Assembly (DaVinci Resolve)
├─ Pacing & Rhythm (15-25 cuts/min target)
├─ Pattern Interrupts (Visual/Audio/Narrative)
└─ Final Export (YouTube specs)
    ↓
PHASE 7: PUBLISHING & DISTRIBUTION
├─ Metadata Optimization (Title/Description/Tags)
├─ YouTube Upload + End Screens
├─ Multi-Platform Adaptation (TikTok/IG/Twitch)
└─ Analytics Monitoring (CTR/AVD/Retention tracking)
    ↓
CONTINUOUS: ITERATION & LEARNING
├─ Performance Analysis (Weekly review)
├─ A/B Testing (Thumbnails/Titles/CTAs)
├─ Lessons Learned Documentation
└─ Process Refinement (Quarterly optimization)
```

### 2.2 Critical Path Visualization

```
TIME AXIS (Solo Creator, 3-Hour Production Target):
┌────────────────────────────────────────────────────────────────┐
│ 0min                                                       180min│
│  │                                                            │  │
│  ├─ RESEARCH (15 min) ────────────────────────────────────┤  │
│  │  [Perplexity + VidIQ]                                    │  │
│  │                                                            │  │
│  ├─ SCRIPTING (65 min) ────────────────────────────────────┤  │
│  │  [Outline: 5m | Draft: 25m | Verify: 15m | Polish: 20m]  │  │
│  │                                                            │  │
│  ├─ VISUAL (30 min) ──────────────────────────────────────┤  │
│  │  [Thumbnail: 10m | B-roll sourcing: 20m]                 │  │
│  │                                                            │  │
│  ├─ AUDIO (25 min) ───────────────────────────────────────┤  │
│  │  [Voice gen: 10m | Music: 5m | Mix: 10m]                 │  │
│  │                                                            │  │
│  ├─ EDIT (35 min) ────────────────────────────────────────┤  │
│  │  [Assembly: 15m | Pacing: 10m | Export: 10m]             │  │
│  │                                                            │  │
│  ├─ PUBLISH (10 min) ─────────────────────────────────────┤  │
│  │  [Metadata + Upload]                                      │  │
│  │                                                            │  │
└────────────────────────────────────────────────────────────────┘
TOTAL: 180 minutes (3 hours) - AI-Augmented Workflow
COMPARISON: 480 minutes (8 hours) - Manual Workflow
TIME SAVINGS: 62.5% reduction
```

### 2.3 Information Flow Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                      DATA FLOW DIAGRAM                           │
└─────────────────────────────────────────────────────────────────┘

PLANNING FILES (Persistent Context)
┌──────────────────────────────────┐
│ task_plan.md                      │ ←──── Session Continuity
│ notes.md                          │       (5-min checkpoints)
│ deliverable.md                    │
│ STYLE_GUIDE.md (Series)          │
└──────────────────────────────────┘
        ↓                    ↑
        ↓                    │ (Continuous Updates)
        ↓                    │
RESEARCH PHASE              LESSONS LEARNED
┌──────────────────────────────────┐
│ Perplexity → research_brief.md   │
│ VidIQ → niche_analysis.md        │
│ Fabric → pattern_insights.md     │
└──────────────────────────────────┘
        ↓
SCRIPT GENERATION
┌──────────────────────────────────┐
│ script_outline.md (Phase 1)      │ → GATE 1: Coverage
│ script_draft_v1.md (Phase 2)     │ → GATE 2: Completeness
│ script_verified_v2.md (Phase 3)  │ → GATE 3: Fact Integrity
│ script_final.md (Phase 4)        │ → GATE 4: Readiness
└──────────────────────────────────┘
        ↓
ASSET PRODUCTION
┌──────────────────────────────────┐
│ Thumbnail: thumbnail_v1.png      │ → A/B Test Variants
│ Audio: voiceover_final.wav       │ → LUFS Verification
│ B-roll: broll_library/           │ → Asset Tagging
│ Music: music_bed.mp3             │ → Licensing Check
└──────────────────────────────────┘
        ↓
VIDEO ASSEMBLY
┌──────────────────────────────────┐
│ project.drp (DaVinci Resolve)    │
│ timeline_v1.xml                  │
│ export_youtube.mp4               │
└──────────────────────────────────┘
        ↓
PUBLISHING
┌──────────────────────────────────┐
│ metadata.txt (Title/Desc/Tags)   │
│ YouTube: Primary upload          │
│ TikTok: 60s adaptation           │
│ Instagram: Reel adaptation       │
└──────────────────────────────────┘
        ↓
ANALYTICS TRACKING
┌──────────────────────────────────┐
│ analytics_snapshot_24hr.json     │ → Performance Review
│ analytics_snapshot_7day.json     │   (Weekly)
│ analytics_snapshot_30day.json    │
└──────────────────────────────────┘
        ↓
        └──────→ Feedback Loop to PLANNING FILES
                 (Inform future content decisions)
```

---

## 3. PHASE-BY-PHASE BREAKDOWN

### PHASE 1: IDEATION & VALIDATION

**Objective:** Identify high-potential topics with proven audience demand and viral mechanics.

**Duration:** 15-60 minutes (depending on research depth)

**Human Decision Points:**
- [CRITICAL] Niche/topic selection (AI suggests, human decides)
- [CRITICAL] Strategic alignment with channel identity
- [MEDIUM] Viral potential prioritization

#### 3.1.1 Tasks & Procedures

**TASK 1.1: Niche/Topic Discovery (5-15 min)**

**Tool Stack:**
| Tool | Purpose | Input | Output |
|------|---------|-------|--------|
| **VidIQ / TubeLab** | Search volume + competition | Keyword list | Demand metrics |
| **Perplexity** | Trending topics research | Niche area | Topic opportunities |
| **YouTube Trending** | Real-time viral signals | Category filter | Trending topics |
| **Google Trends** | Long-term interest curve | Topic keywords | Trend trajectory |

**Execution Workflow:**
```bash
# Step 1: Generate topic ideas (Fabric pattern)
fabric --pattern generate_ideas --context "[Niche area]" > topic_candidates.md

# Step 2: Validate search demand (VidIQ browser extension)
# Manual: Check each topic candidate for:
# - Monthly search volume (Target: >1,000)
# - Competition level (Target: <50 strong channels)
# - Search Demand Ratio (Target: >2.0x)

# Step 3: Trending analysis (Perplexity)
# Query: "What are the trending topics in [niche] for January 2026?"
# → Extract 5-10 trending angles

# Step 4: Document in notes.md
# Format: | Topic | Search Vol | Competition | Ratio | Trending |
```

**TASK 1.2: Viral Potential Assessment (5-10 min)**

**Framework:** STEPPS Analysis (R63)

**Scorecard Template:**
```markdown
## VIRAL POTENTIAL SCORECARD

**Topic:** [Topic Title]

| STEPPS Factor | Score (0-5) | Evidence/Reasoning |
|---------------|-------------|-------------------|
| **Social Currency** | X/5 | Does it make sharer look smart/informed? |
| **Triggers** | X/5 | Is it tied to common experiences/news? |
| **Emotion (High-Arousal)** | X/5 | Does it evoke awe/excitement/anger? |
| **Public Visibility** | X/5 | Can viewers easily share/discuss? |
| **Practical Value** | X/5 | Does it help people solve problems? |
| **Stories** | X/5 | Can it be packaged as narrative? |
| **TOTAL** | X/30 | >20 = High viral potential |

**K-Factor Estimate:** [Expected shares per viewer]
**Decision:** PROCEED / REFINE / REJECT
```

**TASK 1.3: Strategic Alignment Check (2-5 min)**

**Checklist:**
```
□ Aligns with channel niche (not random pivot)
□ Sustainable topic (can create 5+ related videos)
□ Matches audience persona (R36 Audience Persona Development)
□ Fits 70/20/10 content mix (Evergreen/Trending/Experimental)
□ CPM potential acceptable (>$4 for sustainability)
□ Human creator passion/interest present (burnout prevention)
```

**GATE 1: STRATEGIC VALIDATION**

**Pass Criteria:**
- [ ] Search Demand Ratio ≥2.0x OR Trending signal strong
- [ ] STEPPS score ≥18/30 OR High practical value (≥4/5)
- [ ] All strategic alignment checklist items = TRUE
- [ ] Topic can generate 5+ related videos (series potential)

**Fail Action:** Return to TASK 1.1 (select different topic)

**Output Artifacts:**
- `notes.md` (Topic research section with metrics)
- `task_plan.md` (Updated with selected topic + rationale)

---

### PHASE 2: RESEARCH & SCRIPTING

**Objective:** Generate production-ready script with verified sources and optimal structure.

**Duration:** 60-80 minutes (AI-augmented) vs. 290 minutes (manual)

**Human Decision Points:**
- [CRITICAL] Script structure selection (HBC / PAS / Listicle / etc.)
- [CRITICAL] Creative tone and voice decisions
- [MEDIUM] Source credibility assessment
- [LOW] Phrasing refinements

#### 3.2.1 Research Stream (15-20 min)

**TASK 2.1: Deep Research Brief (Perplexity)**

**Tool:** Perplexity Pro ($20/mo)

**Prompt Template:**
```
I'm creating a YouTube video on [TOPIC]. Provide:

1. KEY STATISTICS (3-5 data points with sources)
2. EXPERT PERSPECTIVES (2-3 authoritative viewpoints)
3. COMMON MISCONCEPTIONS (what viewers get wrong)
4. ACTIONABLE INSIGHTS (practical takeaways)
5. RECENT DEVELOPMENTS (2025-2026 updates)
6. RELATED TOPICS (for series expansion)

Format all findings with clickable source citations.
Target audience: [Audience description]
Video length: [X minutes]
```

**Output:** `research_brief.md` with citations

**TASK 2.2: Content Pattern Analysis (Fabric)**

**Tool:** Fabric CLI (R28-R29)

**Workflow:**
```bash
# Analyze top-performing competitor content
fabric -y "https://youtube.com/watch?v=[TOP_VIDEO_ID]" \
  --pattern extract_wisdom \
  > competitor_insights.md

# Extract narrative structure
fabric -y "https://youtube.com/watch?v=[TOP_VIDEO_ID]" \
  --pattern extract_article_wisdom \
  > structure_analysis.md

# Identify hooks and retention strategies
fabric --pattern analyze_claims \
  --input competitor_insights.md \
  > hook_patterns.md
```

**Output:** `competitor_insights.md`, `structure_analysis.md`, `hook_patterns.md`

#### 3.2.2 Script Drafting (40-50 min)

**TASK 2.3: Outline Development (5-10 min)**

**Tool:** Claude (Primary) or ChatGPT

**Prompt Template (Claude):**
```
Create a detailed script outline for a [X-minute] YouTube video.

TOPIC: [Topic title]
TARGET AUDIENCE: [Audience description]
GOAL: [Educational / Entertaining / Persuasive]
STRUCTURE: [HBC / PAS / Listicle / etc. - see R63 templates]

REQUIREMENTS:
- Hook (0-15 seconds): [Stat / Question / Promise format]
- Body sections (3-5 main points)
- Pattern interrupts every 60-90 seconds
- Call-to-action (final 10 seconds)
- Target retention: 70%+ at 30 seconds, 45%+ average

RESEARCH CONTEXT:
[Paste research_brief.md findings]

OUTPUT FORMAT:
## HOOK (0-15s)
[Beat-by-beat breakdown]

## SECTION 1 (15s-90s)
[Beat-by-beat breakdown]

[Continue for all sections...]

Include timing estimates for each beat.
```

**Output:** `script_outline.md`

**GATE 2: COVERAGE CHECK**

**Pass Criteria:**
- [ ] All outline sections have supporting research (3+ sources per claim)
- [ ] Outline matches target retention pattern (hook → body → CTA)
- [ ] Timing estimates sum to target video length (±10% acceptable)
- [ ] Hook, body, CTA sections clearly defined

**Fail Action:** Return to TASK 2.1 (insufficient research depth)

**TASK 2.4: First Draft Generation (20-30 min)**

**Tool:** Claude (long-form) or ChatGPT (rapid iteration)

**Prompt Template (Claude):**
```
Expand the following outline into a complete YouTube script.

OUTLINE:
[Paste script_outline.md]

STYLE GUIDE:
- Tone: [Conversational expert / Professional / Energetic / etc.]
- Reading level: 8th grade (clear, accessible)
- Voice perspective: Second person ("you")
- Sentence length: 15-20 words average
- Pacing: 150 words per minute (WPM)

STRUCTURE REQUIREMENTS:
- Include [VISUAL CUE] markers for b-roll/graphics
- Mark [BREATH] points every 2-3 sentences
- Indicate [MUSIC SHIFT] for emotional beats
- Add [TEXT OVERLAY: "..."] for key points

RETENTION TECHNIQUES:
- Pattern interrupts every 60-90 seconds
- Mini-hooks between sections ("But here's the thing...")
- Question prompts to engage viewer thinking
- Cliffhangers before potential drop-off points

OUTPUT: Full dialogue script with visual/audio cues and timing markers.
```

**Output:** `script_draft_v1.md`

**GATE 3: COMPLETENESS CHECK**

**Pass Criteria:**
- [ ] All outline beats developed into dialogue
- [ ] Visual cues present for 80%+ of content
- [ ] Timing estimates within ±10% of target
- [ ] Voice/tone consistent throughout (use Trinka AI for series)

**Fail Action:** Generate alternative draft with different structure

---

### PHASE 3: VERIFICATION & REFINEMENT

**Objective:** Ensure factual accuracy, source integrity, and maximum engagement potential.

**Duration:** 30-40 minutes

**Human Decision Points:**
- [CRITICAL] Source credibility evaluation (flagged claims)
- [CRITICAL] Creative refinements (hook strength, transitions)
- [MEDIUM] Fact resolution for disputed claims

#### 3.3.1 Fact-Checking Workflow (15-20 min)

**TASK 3.1: Automated Fact Verification**

**Tool:** Originality.ai ($14.95/mo)

**Process:**
```
1. Export script_draft_v1.md as plain text
2. Run through Originality.ai Fact Checker
3. Review flagged claims (accuracy: 86.69%)
4. Categorize flags:
   - GREEN: Verified (no action)
   - YELLOW: Needs source citation
   - RED: Contradictory sources (investigate)
```

**TASK 3.2: Manual Source Verification**

**For YELLOW/RED flags:**
```bash
# Use Perplexity for claim verification
# Query: "Verify this claim: [FLAGGED CLAIM]. Provide 3+ authoritative sources."

# Cross-reference with research_brief.md
# If sources conflict:
#   - Choose most recent (2025-2026 preferred)
#   - Choose most authoritative (peer-reviewed > news > blog)
#   - If unresolvable: Remove claim or hedge ("Studies suggest..." vs "Proven fact")
```

**TASK 3.3: Citation Integration**

**Format (in script):**
```
"According to a 2025 study by Stanford University, 78% of users..."
[CITATION: Stanford Digital Economy Lab, 2025]

"Experts estimate the market will reach $50 billion by 2027..."
[CITATION: Gartner Market Research, 2026]
```

**Output:** `script_verified_v2.md`

#### 3.3.2 Polish & Optimization (15-20 min)

**TASK 3.4: Hook Strength Assessment**

**Hook Scorecard (0-15 second opening):**
```
HOOK EVALUATION RUBRIC:

□ CURIOSITY GAP (1-5): Does it create unanswered question?
□ EMOTIONAL SPIKE (1-5): High-arousal emotion present?
□ SPECIFICITY (1-5): Concrete numbers/details vs. vague?
□ RELEVANCE (1-5): Immediately clear why viewer should care?
□ UNIQUENESS (1-5): Differentiated from competitor content?

TOTAL: ___/25

18-25: STRONG (Proceed)
12-17: MODERATE (Consider revision)
0-11: WEAK (Mandatory revision)
```

**TASK 3.5: Pacing & Flow Refinement**

**Tool:** Claude (refinement pass) + Trinka AI (consistency)

**Prompt Template (Claude):**
```
Refine this script for optimal pacing and engagement.

SCRIPT:
[Paste script_verified_v2.md]

OPTIMIZATION TARGETS:
- Hook (0-15s): Strengthen to 20/25+ on rubric
- Pattern interrupts: Verify every 60-90 seconds
- Transitions: Smooth section changes with mini-hooks
- Pacing variance: <10% deviation from 150 WPM
- Call-to-action: Clear, compelling, single ask

MAINTAIN:
- All factual claims and citations
- Core narrative structure
- Visual/audio cues

OUTPUT: Polished script ready for production.
```

**Output:** `script_final.md`

**GATE 4: FACT INTEGRITY & READINESS**

**Pass Criteria:**
- [ ] All claims have source citations (>95% coverage)
- [ ] No "red flag" claims (contradicting sources resolved)
- [ ] Hook strength ≥18/25
- [ ] Pacing consistent (variance <10%)
- [ ] CTA clear and compelling
- [ ] Brand voice matches channel identity

**Fail Action:**
- If fact issues: Return to TASK 3.2 (source verification)
- If engagement issues: Return to TASK 3.5 (refinement pass)

**Output Artifacts:**
- `script_final.md` (Production-ready script)
- `sources.md` (Complete citation list)
- `task_plan.md` (Updated: Scripting phase COMPLETE)

---

### PHASE 4: VISUAL PRODUCTION

**Objective:** Create high-CTR thumbnail and source all visual assets (b-roll, graphics, animations).

**Duration:** 25-35 minutes

**Human Decision Points:**
- [CRITICAL] Thumbnail design concept approval
- [CRITICAL] Visual brand consistency
- [MEDIUM] B-roll selection for emotional impact
- [LOW] Animation timing adjustments

#### 3.4.1 Thumbnail Design (10-15 min)

**TASK 4.1: Thumbnail Concept Development**

**Tool:** Canva Pro ($13/mo)

**Design Principles (R36 Thumbnail Optimization):**

**The 3-Second Rule Framework:**
```
┌────────────────────────────────────────┐
│  PRIMARY ELEMENT (50% of frame)        │  ← Face/Character OR
│  - High contrast                        │    Dominant visual metaphor
│  - Emotionally expressive               │
│                                         │
│  TEXT (3-7 words, 30% of frame)        │  ← Large, high-contrast font
│  - Front-loaded power words             │    (Impact/Montserrat Bold)
│  - 4.5:1 contrast ratio minimum         │
│                                         │
│  BACKGROUND (20% of frame)             │  ← Simple, complementary
│  - Supports, doesn't distract           │    (blur/gradient/solid)
└────────────────────────────────────────┘

COLOR PSYCHOLOGY APPLICATION:
├─ Urgent/Breaking: Red + Yellow
├─ Educational/How-To: Blue + Orange
├─ Success/Money: Green + Gold
└─ Mystery/Deep Dive: Purple + White
```

**Workflow:**
```
1. Create 3 thumbnail variations (A/B/C test candidates)
   - Variation A: Face-focused (if applicable)
   - Variation B: Visual metaphor-focused
   - Variation C: Text-dominant

2. Mobile legibility test (resize to 240×180px)
   - If text unreadable: Simplify or enlarge

3. Contrast verification (WebAIM Contrast Checker)
   - Text-to-background: ≥4.5:1
   - Primary-to-background: ≥7:1

4. Export:
   - thumbnail_A.png (1280×720, <2MB)
   - thumbnail_B.png
   - thumbnail_C.png
```

**Output:** `thumbnails/thumbnail_[A/B/C].png`

**TASK 4.2: A/B Testing Strategy**

**Platform:** YouTube Studio A/B Test Feature

**Protocol:**
```
INITIAL UPLOAD: Use thumbnail_A.png (best guess)

AFTER 1,000 IMPRESSIONS (typically 24-48 hours):
├─ If CTR <3%: Swap to thumbnail_B.png
├─ If CTR 3-5%: Test thumbnail_B.png (50/50 split)
└─ If CTR >5%: Keep thumbnail_A.png, document winning pattern

AFTER 5,000 IMPRESSIONS:
└─ Lock winning thumbnail, add pattern to template library
```

#### 3.4.2 B-roll Asset Sourcing (10-15 min)

**TASK 4.3: Visual Asset Acquisition**

**Tool Stack:**
| Source Type | Tools | Cost | Use Case |
|------------|-------|------|----------|
| **Stock Video** | Pexels, Pixabay | FREE | Generic b-roll |
| **Premium Stock** | Storyblocks, Envato | $15-30/mo | High-quality, unique |
| **AI Generation** | Runway Gen-2, Pika | $10-90/mo | Custom scenes |
| **Screen Recording** | OBS Studio | FREE | Software demos |
| **Animation** | After Effects, Canva | $13-55/mo | Motion graphics |

**Sourcing Workflow:**
```bash
# Step 1: Extract visual cue list from script_final.md
grep "\[VISUAL CUE\]" script_final.md > broll_requirements.txt

# Step 2: Categorize requirements
# - STOCK: Generic scenes (office, nature, people)
# - AI-GEN: Specific scenes unavailable in stock
# - ANIMATION: Data visualizations, text animations
# - SCREEN: Software/tool demonstrations

# Step 3: Download/generate assets
# Naming convention: broll_[section]_[number].mp4
# Example: broll_hook_01.mp4, broll_section1_02.mp4

# Step 4: Organize in asset library
DeadManAI_AssetLibrary/
├── stock/
│   ├── people/
│   ├── technology/
│   └── nature/
├── ai_generated/
└── animations/
```

**Output:** `broll_library/` (organized asset folder)

#### 3.4.3 Animation & Motion Graphics (5-10 min)

**TASK 4.4: Motion Graphic Creation**

**Tool Options:**
| Tool | Complexity | Cost | Best For |
|------|------------|------|----------|
| **Canva Pro** | Beginner | $13/mo | Simple text animations |
| **Resolve Fusion** | Intermediate | FREE | Integrated with editing |
| **After Effects** | Advanced | $20/mo | Professional motion graphics |
| **MotionElements** | N/A (Templates) | $16.50/mo | Pre-made templates |

**Common Animation Needs:**
```
1. INTRO LOGO (2-3 seconds)
   └─ Fade in + scale with audio logo

2. TEXT OVERLAYS (Throughout video)
   ├─ Pop-in with ease-out (0.3s duration)
   ├─ On-screen duration: 2-3 seconds
   └─ Font: Consistent with thumbnail

3. LOWER THIRDS (For statistics/quotes)
   ├─ Slide-in from left (0.5s)
   └─ On-screen: 3-5 seconds

4. TRANSITION ELEMENTS (Section breaks)
   ├─ Whoosh/swipe (0.5-1s)
   └─ Consistent sonic identity

5. OUTRO/END SCREEN (5-20 seconds)
   └─ End screen elements animate in
```

**Template Library Strategy:**
```
Create once, reuse indefinitely:
├── intro_logo_template.aep (After Effects)
├── text_overlay_template.aep
├── lower_third_template.aep
├── transition_pack.aep
└── outro_endscreen_template.aep

Export as Fusion templates for DaVinci Resolve integration
```

**Output:** `animation_assets/` (Motion graphic files)

**QA Checkpoint: Visual Production**
```
□ Thumbnail passes 3-second legibility test (mobile size)
□ Thumbnail contrast ratios meet accessibility standards (4.5:1+)
□ All [VISUAL CUE] requirements from script have sourced assets
□ Animation templates saved for reuse (if created)
□ Asset library organized with clear naming convention
□ Visual brand consistency verified (colors, fonts match channel)
```

---

### PHASE 5: AUDIO PRODUCTION

**Objective:** Generate professional voiceover, select music, and mix to broadcast standards.

**Duration:** 20-30 minutes

**Human Decision Points:**
- [CRITICAL] Voice selection (tone, pace, character fit)
- [CRITICAL] Music mood matching
- [MEDIUM] Emotional beat alignment (music shifts)
- [LOW] EQ fine-tuning

#### 3.5.1 Voice Generation (10-15 min)

**TASK 5.1: AI Voice Selection & Generation**

**Tool:** ElevenLabs ($5-330/mo, recommend $22/mo Creator tier)

**Voice Selection Criteria (R36 AI Voice Production):**
```
CHANNEL PERSONALITY MAPPING:

Energetic/Entertainment → Young, upbeat, 160+ WPM pace
Educational/Professional → Middle-aged, warm, 130-160 WPM
Mystery/Investigative → Mature, serious, 100-130 WPM
Tech/Reviews → Professional, clear, 140-160 WPM
```

**Workflow:**
```
1. SCRIPT PREPARATION:
   - Export script_final.md as plain text (remove visual cues)
   - Insert [BREATH] markers every 2-3 sentences
   - Mark emotional cues: [EXCITED], [SERIOUS], [CONCERNED]

2. VOICE TESTING (First video only):
   - Generate 30-second sample with 3-5 different voices
   - Human review: clarity, tone match, naturalness
   - Select winner, document in STYLE_GUIDE.md

3. FULL GENERATION:
   - Upload script to ElevenLabs
   - Set stability: 50-70% (more expressive)
   - Set clarity: 70-85% (articulation)
   - Export as WAV (highest quality)

4. QUALITY CHECK:
   - Listen for mispronunciations (re-generate problem sentences)
   - Check pacing consistency (should match 150 WPM ±10%)
   - Verify emotional tone matches script cues
```

**Output:** `audio/voiceover_raw.wav`

#### 3.5.2 Post-Processing (5-10 min)

**TASK 5.2: Voice Processing Chain**

**Tool:** Reaper (FREE), Audacity (FREE), or Adobe Audition ($20/mo)

**Processing Chain (Order Matters):**
```
INPUT: voiceover_raw.wav

1. NOISE GATE
   ├─ Threshold: -40 to -35 dB
   ├─ Attack: 0.1-1 ms
   ├─ Release: 100-300 ms
   └─ Purpose: Remove background noise between words

2. EQ (EQUALIZATION)
   ├─ High-pass filter: 80-100 Hz (remove rumble)
   ├─ Presence boost: +2-3 dB at 3-5 kHz (clarity)
   └─ Harshness cut: -2 dB at 6-8 kHz (if sibilant)

3. COMPRESSOR
   ├─ Ratio: 3:1 to 4:1
   ├─ Threshold: -18 to -12 dB
   ├─ Attack: 10-30 ms
   ├─ Release: 100-300 ms
   ├─ Makeup gain: +3-6 dB
   └─ Purpose: Even volume, professional sound

4. DE-ESSER
   ├─ Target frequency: 4-8 kHz
   ├─ Reduction: 3-6 dB
   └─ Purpose: Soften harsh "S" sounds

5. LIMITER (Final safety)
   ├─ Ceiling: -1 dBTP (true peak)
   ├─ Release: 100 ms
   └─ Purpose: Prevent clipping

OUTPUT: voiceover_processed.wav
```

**Reaper Template (Save as project template):**
```
1. Load chain as FX preset: "DeadManAI_Voice_Chain"
2. Future videos: Load template, drag audio, render
3. Processing time: <2 minutes per video
```

**Output:** `audio/voiceover_processed.wav`

#### 3.5.3 Music Selection & Mixing (5-10 min)

**TASK 5.3: Music Bed Selection**

**Tool:** Epidemic Sound ($15/mo) or Artlist ($14.99/mo)

**Music Mood Mapping (R36 Audio Mixing):**
| Video Type | Music Mood | BPM Range | Energy Level |
|-----------|------------|-----------|--------------|
| **Tutorial/How-To** | Upbeat, positive | 100-120 | Medium |
| **Serious/News** | Ambient, minimal | 60-80 | Low |
| **High Energy/Hype** | Electronic, driving | 120-140 | High |
| **Emotional/Story** | Piano, strings | 70-90 | Medium-Low |
| **Comedic/Fun** | Quirky, playful | 110-130 | Medium-High |

**Selection Criteria:**
```
□ Matches video emotional arc
□ Loopable (for videos of varying length)
□ No distracting melody (supports, doesn't compete with voice)
□ Licensing cleared for YouTube (Epidemic/Artlist = full clearance)
```

**TASK 5.4: Audio Mixing**

**Mix Balance (YouTube Standard - R36):**
```
VOICE (DIALOGUE):    -12 to -6 dBFS (loudest element)
     ↓
MUSIC (BACKGROUND):  -24 to -18 dBFS (12-18 dB below voice)
     ↓
SFX (EFFECTS):       -18 to -12 dBFS (varies by impact)
     ↓
AMBIENCE:            -30 to -24 dBFS (subtle texture)
```

**Ducking (Sidechain Compression):**
```
PURPOSE: Music automatically reduces when voice plays

SETTINGS (Reaper/Audition):
├─ Sidechain source: Voiceover track
├─ Ratio: 6:1 to 10:1
├─ Threshold: Adjust so music ducks 6-12 dB
├─ Attack: 10-20 ms (fast response)
├─ Release: 200-500 ms (gradual return)
└─ Result: Voice always intelligible, music fills silence
```

**Final Loudness Check:**
```
Tool: Youlean Loudness Meter (FREE plugin) or built-in DAW meter

TARGET SPECS (YouTube):
├─ Integrated LUFS: -14 to -16
├─ True Peak: -1 dBTP (prevents clipping)
└─ Loudness Range (LRA): 4-9

If outside range:
├─ Too quiet (<-16 LUFS): Increase limiter makeup gain
└─ Too loud (>-14 LUFS): Reduce master fader or limiter ceiling
```

**Output:** `audio/final_mix.wav` (export at 48kHz, 24-bit)

**QA Checkpoint: Audio Production**
```
□ Voiceover clarity: All words clearly intelligible
□ Processing artifacts: No robotic/unnatural sounds
□ Music level: 12-18 dB below voice (ducking working)
□ LUFS: -14 to -16 integrated (YouTube spec)
□ True Peak: -1 dBTP (no clipping)
□ Breath sounds: Reduced but not eliminated (natural)
□ Consistency: Matches previous videos (if series)
```

---

### PHASE 6: EDITING & POST-PRODUCTION

**Objective:** Assemble all assets into cohesive video with optimized pacing and retention mechanisms.

**Duration:** 30-45 minutes

**Human Decision Points:**
- [CRITICAL] Pacing rhythm and cut timing
- [CRITICAL] Pattern interrupt placement
- [MEDIUM] B-roll selection for emotional beats
- [MEDIUM] Color grading consistency

#### 3.6.1 Video Assembly (15-20 min)

**TASK 6.1: Project Setup**

**Tool:** DaVinci Resolve (FREE) or DaVinci Resolve Studio ($295 one-time)

**Project Template Structure:**
```
TIMELINE ORGANIZATION (Top to Bottom):

Track V5: TEXT OVERLAYS & GRAPHICS
Track V4: ANIMATIONS & MOTION GRAPHICS
Track V3: B-ROLL & VISUAL ASSETS
Track V2: PRIMARY VIDEO (if any) or COLOR BARS
Track V1: THUMBNAIL PLACEHOLDER (for end screen preview)

Track A1: VOICEOVER (processed)
Track A2: MUSIC BED (ducked)
Track A3: SOUND EFFECTS
Track A4: AMBIENCE (optional)
```

**Import Checklist:**
```
□ audio/final_mix.wav → Tracks A1-A2 (already mixed) OR
□ audio/voiceover_processed.wav → Track A1 (separate mixing)
□ audio/music_bed.mp3 → Track A2
□ broll_library/* → Media pool
□ animation_assets/* → Media pool
□ thumbnails/thumbnail_A.png → Media pool
```

**TASK 6.2: Rough Assembly**

**Workflow:**
```
1. LAY VOICEOVER FOUNDATION:
   - Place voiceover_processed.wav on Track A1
   - This is timing reference for entire video

2. SYNC B-ROLL TO SCRIPT:
   - Read script [VISUAL CUE] markers
   - Place corresponding b-roll clips on Track V3
   - Align visuals with voiceover timing

3. ADD ANIMATIONS:
   - Intro logo: 0-3 seconds
   - Text overlays: Per script cues
   - Lower thirds: For statistics/quotes
   - Outro/end screen: Final 5-20 seconds

4. MUSIC PLACEMENT:
   - Music starts: 0 seconds (with intro) OR 3 seconds (after cold open)
   - Music volume automation: Fade in/out at emotional beats
   - Music ends: 5 seconds before video end (CTA clarity)
```

**Output:** Timeline rough cut (V1)

#### 3.6.2 Pacing & Rhythm Optimization (10-15 min)

**TASK 6.3: Cut Frequency Calibration**

**Target Cut Rate (R36 Video Pacing):**
| Content Type | Cuts/Minute | Rationale |
|--------------|-------------|-----------|
| **Fast-paced (gaming, reaction)** | 40-60 | Match high-energy content |
| **Tutorial (faceless)** | 15-25 | Allow comprehension |
| **Narrative (storytelling)** | 10-20 | Let story breathe |
| **Talking head (monologue)** | 8-12 | Emphasize speaker |

**DeadManAI Target:** 15-25 cuts/minute (educational/entertainment blend)

**Pacing Audit:**
```bash
# Manual count (in Resolve timeline):
# 1. Note total video duration: [X minutes]
# 2. Count total cuts (V3 track): [Y cuts]
# 3. Calculate: Y cuts ÷ X minutes = Z cuts/min
# 4. If Z < 15 or Z > 25: Adjust b-roll frequency
```

**TASK 6.4: Pattern Interrupt Implementation**

**Interrupt Techniques (R64 Audience Psychology):**

**Visual Interrupts (8-12% retention boost):**
```
EVERY 60-90 SECONDS, insert one:
├─ Camera angle change (if talking head)
├─ Zoom in/out (emphasize key point)
├─ B-roll shift (new scene/context)
├─ Color/filter shift (mood change)
└─ Text overlay appear/disappear
```

**Audio Interrupts (10-15% retention boost):**
```
STRATEGIC PLACEMENT:
├─ Music tempo change (slow → fast or vice versa)
├─ Sound effect (whoosh, ding, impact for emphasis)
├─ Strategic silence (2-3 seconds before big reveal)
└─ Volume shift (music swell, then duck for voiceover)
```

**Narrative Interrupts (15-20% retention boost):**
```
SCRIPT-BASED (already in script_final.md):
├─ Question posed to viewer ("But have you considered...")
├─ Unexpected fact revealed ("Here's the shocking part...")
├─ Story direction pivot ("This is where it gets interesting...")
└─ Callback to earlier moment ("Remember when I mentioned...")
```

**Interrupt Placement Map:**
```
0-15s:   HOOK (high engagement, no interrupts needed)
15-60s:  First interrupt (60s mark)
60-120s: Second interrupt (90s mark)
120-180s: Third interrupt (150s mark)
[Continue pattern every 60-90s until end]
```

**TASK 6.5: Retention Curve Alignment**

**Critical Zones (R64 Retention Mechanisms):**
```
ZONE 1: HOOK WINDOW (0-15s)
├─ Target retention: 75-85%
├─ Technique: Cold open (jump to most exciting moment)
├─ Edit: Fastest cuts, high energy
└─ No slow intro, immediate value signal

ZONE 2: FIRST HALF (15s - 50% mark)
├─ Target retention: 65-75%
├─ Technique: Deliver on hook promise quickly
└─ Edit: Maintain pacing, frequent b-roll changes

ZONE 3: MID-VIDEO VALLEY (35-65% of video)
├─ Target retention: Prevent drop-off
├─ Technique: Pattern interrupts CRITICAL here
├─ Edit: Increase cut frequency slightly
└─ Narrative: Mid-roll hook ("The next part will shock you...")

ZONE 4: CLIMAX (75-95% of video)
├─ Target retention: Build to peak
├─ Technique: Speed up pacing, increase tension
└─ Edit: Faster cuts, music swell, visual intensity

ZONE 5: OUTRO/CTA (Final 5-20s)
├─ Target: 40-50% retention (natural drop-off)
├─ Technique: Satisfy viewer, clear CTA
└─ Edit: Moderate pace, end screen elements animate in
```

**Output:** Timeline optimized cut (V2)

#### 3.6.3 Color Grading & Final Polish (5-10 min)

**TASK 6.6: Color Correction & Grading**

**Workflow (DaVinci Resolve Color Page):**
```
1. COLOR CORRECTION (Technical):
   - Exposure: Balanced (not too dark/bright)
   - White balance: Neutral (unless creative intent)
   - Contrast: Moderate (avoid blown highlights/crushed blacks)

2. COLOR GRADING (Creative):
   - Apply LUT (Look-Up Table) for consistent style
   - Saturation: +10-15% (vibrant but not cartoonish)
   - Consistency: All clips match (no jarring shifts)

3. DELIVERABLE:
   - Save grade as "DeadManAI_House_Style.drx"
   - Apply to all future videos (brand consistency)
```

**TASK 6.7: Final QA Pass**

**Checklist:**
```
VISUAL QA:
□ No black frames or gaps in timeline
□ All b-roll clips properly aligned with voiceover
□ Text overlays readable (3-second rule, mobile tested)
□ Animations smooth (no stuttering)
□ Color grading consistent across all clips
□ Thumbnail preview accurate (if embedded)

AUDIO QA:
□ Voiceover intelligible throughout
□ No audio clipping (red peaks in meter)
□ Music ducking working (voice always audible)
□ Sound effects not overpowering
□ No audio gaps or pops

TECHNICAL QA:
□ Timeline framerate: 24, 30, or 60 fps (consistent)
□ Resolution: 1920×1080 (minimum) or 3840×2160 (4K)
□ Aspect ratio: 16:9 (YouTube standard)
□ Total duration matches target (±10% acceptable)
```

**Output:** Timeline final (V3)

#### 3.6.4 Export & Rendering (5-10 min)

**TASK 6.8: Export Settings**

**YouTube Recommended Specs (2026):**
```
CONTAINER: MP4
VIDEO CODEC: H.264 (broad compatibility) or H.265 (smaller file size)
RESOLUTION: 1920×1080 (1080p) or 3840×2160 (4K)
FRAMERATE: Match source (23.976, 24, 25, 29.97, 30, 50, 60 fps)
BITRATE: 8-12 Mbps (1080p) or 35-45 Mbps (4K)
AUDIO CODEC: AAC-LC
AUDIO BITRATE: 192-320 kbps
AUDIO SAMPLE RATE: 48 kHz
COLOR SPACE: Rec. 709 (SDR) or Rec. 2020 (HDR)
```

**DaVinci Resolve Export Preset:**
```
Deliver Page → YouTube 1080p Preset

MODIFICATIONS (if needed):
├─ Bitrate: "Restrict to 10,000 Kbps" (10 Mbps)
├─ Audio: AAC, 48 kHz, 256 kbps
└─ Filename: [YYYYMMDD]_[Topic_Slug]_DeadManAI.mp4
   Example: 20260103_AI_Tools_Replace_Jobs_DeadManAI.mp4
```

**Rendering:**
```
1. Add to render queue
2. Start render (typical time: 2-5 minutes for 5-minute video)
3. QA rendered file:
   - Play back in VLC/QuickTime
   - Verify audio sync
   - Check for encoding artifacts
4. If issues: Adjust settings, re-render
```

**Output:** `exports/[DATE]_[TOPIC]_DeadManAI.mp4`

**QA Checkpoint: Editing & Post-Production**
```
□ Pacing: 15-25 cuts/minute (appropriate to content type)
□ Pattern interrupts: Every 60-90 seconds
□ Retention alignment: Hook strong, mid-video valley addressed
□ Audio LUFS: -14 to -16 (verified in final render)
□ Export specs: Match YouTube recommendations
□ File size: <2GB (for upload efficiency)
□ Visual QA: All elements visible, no errors
□ Audio QA: Clean, balanced, no clipping
```

---

### PHASE 7: PUBLISHING & DISTRIBUTION

**Objective:** Optimize metadata for discovery, upload to YouTube, and adapt for secondary platforms.

**Duration:** 15-25 minutes

**Human Decision Points:**
- [CRITICAL] Title/description optimization (keyword research)
- [CRITICAL] Multi-platform adaptation strategy
- [MEDIUM] Publishing schedule timing
- [LOW] Tag variations

#### 3.7.1 Metadata Optimization (10-15 min)

**TASK 7.1: Title Engineering**

**Title Formula (R61 Metadata Optimization):**
```
[HOOK/BENEFIT] + [SPECIFICITY] + [CURIOSITY GAP]

CHARACTER LIMIT: 50-60 (full mobile display) | 100 max
FRONT-LOAD: Most important words first (left side)
```

**Power Words Bank:**
| Category | Words | CTR Boost |
|----------|-------|-----------|
| **Curiosity** | Secret, Hidden, Revealed, Exposed | +8-12% |
| **Urgency** | Now, Today, 2026, Before, Deadline | +5-10% |
| **Benefit** | Free, Easy, Simple, Fast, Proven | +10-15% |
| **Authority** | Expert, Professional, Ultimate, Complete | +7-12% |
| **Emotion** | Shocking, Amazing, Incredible, Devastating | +12-18% |

**Title Variations (Test 3-5 options):**
```
1. [BENEFIT-FOCUSED]
   "5 Free AI Tools That Will Save You 10 Hours Per Week in 2026"

2. [CURIOSITY-FOCUSED]
   "The Hidden AI Tool Big Tech Doesn't Want You to Know About"

3. [URGENCY-FOCUSED]
   "Before 2027, These 3 AI Skills Will Be Mandatory for Your Job"

4. [AUTHORITY-FOCUSED]
   "Expert Analysis: Why 90% of AI Tools Fail (And 3 That Don't)"

5. [EMOTION-FOCUSED]
   "This AI Breakthrough Will Change Everything You Know About [Topic]"
```

**Selection Process:**
```
1. Generate 5 title variations using formula
2. Run through TubeBuddy/VidIQ Score (Target: 70+/100)
3. Check competitor titles (avoid direct duplication)
4. Human gut check (would YOU click?)
5. Select winner, save alternates for A/B test (if CTR <5% after 48hr)
```

**TASK 7.2: Description Optimization**

**Description Structure:**
```
═══════════════════════════════════════════════════════════
FIRST 2 LINES (Shown before "Show more" - CRITICAL):
[Reinforce hook from title + primary keyword]
[Create intrigue to expand description]

Example:
"Discover the 5 AI tools that top professionals use to save 10+ hours every week. The third one is a complete game-changer for content creators like us.

[EMOJI] Timestamps below..."
═══════════════════════════════════════════════════════════
MAIN BODY (After expansion):

[3-5 sentence value proposition - what will viewer gain?]

[TIMESTAMPS - if video >5 minutes]
0:00 - Introduction
0:45 - Tool #1: [Name] - [Benefit]
2:15 - Tool #2: [Name] - [Benefit]
3:45 - Tool #3: [Name] - [Benefit]
5:10 - Conclusion & Next Steps

[RELATED VIDEOS/PLAYLISTS]
Watch next: [Link to related video]
Full playlist: [Link to series]

[CALL-TO-ACTION]
Like this video if you found it helpful!
Subscribe for weekly AI tools and strategies: [Channel link]
Comment below: Which tool are you most excited to try?

[RESOURCES - if applicable]
Links to tools mentioned: [in pinned comment for tracking]
═══════════════════════════════════════════════════════════
FOOTER:

[SOCIAL MEDIA]
Twitter: @DeadManAI
Newsletter: [link]

[AFFILIATE DISCLOSURE - if applicable]
Some links may be affiliate links. We only recommend tools we use.

[CREDITS]
Music: [Track name] by [Artist] via Epidemic Sound
Stock footage: Pexels, Pixabay

#AITools #Productivity #ContentCreation
═══════════════════════════════════════════════════════════
```

**Keyword Integration:**
```
PRIMARY KEYWORD: Mentioned 3-4 times naturally
SECONDARY KEYWORDS: Mentioned 1-2 times each
LSI KEYWORDS: Related terms (synonyms, variations)

Density: 2-3% (not spammy, natural reading)
```

**TASK 7.3: Tag Strategy**

**Tag Hierarchy (R61):**
```
1. BRAND TAG (Always first):
   "DeadManAI" or "The Unseen"

2. PRIMARY KEYWORD (2-3 variations):
   ├─ Exact match: "AI tools for productivity"
   ├─ Plural: "AI productivity tools"
   └─ Question: "best AI tools 2026"

3. SECONDARY KEYWORDS (4-6 tags):
   ├─ "content creation tools"
   ├─ "time saving AI"
   ├─ "AI automation"
   └─ "productivity hacks"

4. LONG-TAIL (3-5 tags):
   ├─ "AI tools for content creators 2026"
   ├─ "free AI productivity software"
   └─ "AI tools to save time"

TOTAL: 15-20 tags (quality > quantity)
```

**Tool:** TubeBuddy Tag Explorer (find low-competition, high-search tags)

**Output:** `metadata.txt` (Title, Description, Tags compiled)

#### 3.7.2 YouTube Upload & Configuration (5-10 min)

**TASK 7.4: YouTube Studio Upload**

**Upload Workflow:**
```
1. UPLOAD:
   - Drag exports/[FILE].mp4 to YouTube Studio
   - While processing: Prepare metadata

2. BASIC INFO:
   - Title: [Paste from metadata.txt]
   - Description: [Paste from metadata.txt]
   - Thumbnail: Upload thumbnail_A.png (custom)
   - Playlist: Add to relevant playlist
   - Audience: Not made for kids (unless it is)

3. VIDEO ELEMENTS:
   - End screen: Template applied (5-20 seconds)
     ├─ Best for viewer: Video (right)
     ├─ Subscribe button: Center
     ├─ Specific video: Video (left)
     └─ Playlist: Bottom

   - Cards: Add 2-3 cards
     ├─ Early card (20-30%): Related video
     ├─ Mid-roll card (50-60%): Playlist/series
     └─ Late card (80-90%): Next video

4. ADVANCED SETTINGS:
   - Tags: [Paste from metadata.txt]
   - Category: Education / Science & Technology / etc.
   - Comments: Enabled (engagement)
   - Captions: Upload .srt (if available) or auto-generate
   - Allow embedding: Yes
   - Publish to subscriptions: Yes
   - Age restriction: None (unless applicable)

5. MONETIZATION (if eligible):
   - Monetization: On
   - Ad types: All selected (max revenue)
   - Sponsorships: Declare if applicable

6. PUBLISH:
   - Visibility: Public (immediate) OR Scheduled (strategic timing)
   - If scheduled: Select date/time (see Task 7.5)
```

**TASK 7.5: Strategic Publishing Timing**

**Best Upload Times (YouTube Algorithm, 2026):**
| Day | Time (EST) | Rationale |
|-----|------------|-----------|
| **Thursday** | 12-3 PM | Highest engagement day |
| **Friday** | 12-3 PM | Pre-weekend traffic |
| **Saturday** | 9-11 AM | Weekend leisure browsing |
| **Sunday** | 3-6 PM | Weekend winding down |

**Avoid:** Monday mornings (work focus), Late nights (low engagement)

**Frequency Strategy:**
```
SOLO CREATOR (1-2 videos/week):
└─ Consistent schedule: Same day/time each week (Thursday 2 PM)

SMALL TEAM (3-4 videos/week):
├─ Monday, Wednesday, Friday (M-W-F pattern)
└─ Thursday + Sunday (high-engagement days)

PRODUCTION TEAM (5-7 videos/week):
└─ Daily uploads (same time each day for algorithm consistency)
```

#### 3.7.3 Multi-Platform Adaptation (5-10 min)

**TASK 7.6: Secondary Platform Distribution**

**Platform Specifications:**

**TikTok (60-second vertical):**
```
ADAPTATION STRATEGY:
├─ Extract hook + best 60 seconds (0-60s of YouTube video)
├─ Re-edit for vertical (9:16 aspect ratio)
├─ Add text overlays (TikTok culture: auto-captions)
├─ Re-export: 1080×1920, H.264, <100MB

PUBLISHING:
├─ Upload to TikTok
├─ Caption: Hook from title + trending hashtags
├─ Sound: Original audio (or trending sound if applicable)
└─ CTA: "Full video on YouTube - link in bio"
```

**Instagram Reels (90-second vertical):**
```
ADAPTATION STRATEGY:
├─ Extract hook + best 90 seconds
├─ Re-edit for vertical (9:16 aspect ratio)
├─ Music: Use Instagram music library (avoid copyright)
├─ Re-export: 1080×1920, H.264

PUBLISHING:
├─ Upload as Reel
├─ Caption: Shorter than TikTok (125 char preview)
├─ Hashtags: 5-10 relevant (#AI #Productivity #ContentCreator)
└─ CTA: "Full version on YouTube 🔗 in bio"
```

**Twitch (Live Discussion / VOD):**
```
STRATEGY (Optional):
├─ Go live: Discuss video topic in-depth
├─ Play YouTube video on stream (with commentary)
├─ Engage with chat (Q&A)
└─ VOD: Auto-uploaded to Twitch channel (additional reach)
```

**Twitter/X (Thread):**
```
THREAD STRATEGY:
├─ Tweet 1: Hook + YouTube link
├─ Tweet 2-5: Key takeaways (pull from video)
├─ Tweet 6: CTA ("Watch full breakdown: [link]")
└─ Pin thread to profile during launch week
```

**Output:** Multi-platform content distributed

**QA Checkpoint: Publishing & Distribution**
```
□ Title: 50-60 characters, front-loaded, power words used
□ Description: First 2 lines compelling, timestamps present
□ Tags: 15-20 tags, brand tag first, hierarchy followed
□ Thumbnail: Custom thumbnail uploaded (thumbnail_A.png)
□ End screen: Configured (5-20s, 4 elements max)
□ Cards: 2-3 cards placed strategically
□ Visibility: Public or scheduled for optimal time
□ Multi-platform: TikTok/Instagram adaptations uploaded (if applicable)
□ Metadata file saved: metadata.txt for future reference
```

---

## 4. MULTI-PLATFORM STRATEGY

### 4.1 Platform Prioritization Matrix

**Decision Framework:**

```
┌─────────────────────────────────────────────────────────────────┐
│                   PLATFORM PRIORITY MATRIX                       │
│                  (DeadManAI Strategic Focus)                     │
└─────────────────────────────────────────────────────────────────┘

PRIMARY PLATFORM: YOUTUBE
├─ Rationale:
│  ├─ Longest content lifespan (evergreen discovery)
│  ├─ Highest CPM for educational/tech content ($5-20)
│  ├─ Search-driven traffic (sustainable growth)
│  ├─ Monetization maturity (AdSense + sponsorships)
│  └─ Faceless content highly viable
├─ Investment: 80% of production effort
└─ Success Metrics: CTR 5-7%, AVD 40-50%, Sub conversion 1-2%

SECONDARY PLATFORMS: TIKTOK + INSTAGRAM REELS
├─ Rationale:
│  ├─ Viral discovery potential (algorithm amplification)
│  ├─ Younger demographic reach (18-34 year olds)
│  ├─ Content repurposing efficiency (same script, reformatted)
│  ├─ Traffic funnel to YouTube (link in bio strategy)
│  └─ Faceless content thriving (voiceover + b-roll format)
├─ Investment: 15% of production effort (adaptation only)
└─ Success Metrics: Views >10K per post, CTR to YouTube >2%

TERTIARY PLATFORMS: TWITTER/X + LINKEDIN (Optional)
├─ Rationale:
│  ├─ Thought leadership positioning
│  ├─ Direct audience engagement (discussions, threads)
│  ├─ B2B networking (potential sponsorships/collabs)
│  └─ Content syndication (threads summarizing videos)
├─ Investment: 5% of production effort (text-based)
└─ Success Metrics: Engagement rate >3%, follower growth >10%/mo

EXPERIMENTAL: TWITCH (Live Commentary)
├─ Rationale:
│  ├─ Real-time audience interaction
│  ├─ Extended content format (go deep on topics)
│  ├─ Community building (loyal fanbase)
│  └─ Monetization: Subs, bits, donations
├─ Investment: Variable (if testing live format)
└─ Success Metrics: Concurrent viewers >50, chat engagement high
```

### 4.2 Content Adaptation Playbook

**YouTube → TikTok/Instagram Reels (Vertical Video):**

```
ADAPTATION WORKFLOW (DaVinci Resolve):

1. TIMELINE SETUP:
   ├─ New timeline: 1080×1920 (9:16 vertical)
   ├─ Import YouTube project or final export
   └─ Target duration: 60s (TikTok) or 90s (Instagram)

2. CONTENT SELECTION:
   ├─ Extract: Hook (0-15s) + Best segment (15-60s)
   ├─ Prioritize: High-energy moments, key insights
   └─ Ensure: Complete thought (not mid-sentence cutoff)

3. REFORMATTING:
   ├─ Crop/reframe: Center subjects (vertical composition)
   ├─ Add text overlays: ALL KEY POINTS (mobile viewing, sound-off)
   ├─ Increase font size: 2x larger than YouTube (legibility)
   └─ Captions: Auto-generate or manual (TikTok trend)

4. PACING ADJUSTMENT:
   ├─ Increase cut frequency: 30-40 cuts/min (faster than YouTube)
   ├─ Shorten b-roll clips: 2-3 seconds max (attention span)
   └─ Pattern interrupts: Every 15-20 seconds (vs. 60-90s on YouTube)

5. AUDIO MIXING:
   ├─ Music: Higher energy (trending sounds if applicable)
   ├─ Voiceover: Louder relative to music (mobile speakers)
   └─ Sound effects: More prominent (engagement cue)

6. PLATFORM-SPECIFIC:
   TikTok:
   ├─ Hook: First 3 seconds CRITICAL (even faster than YouTube)
   ├─ Text: Large, colorful, dynamic (TikTok aesthetic)
   ├─ Music: Use trending sounds (algorithm boost)
   └─ CTA: "Watch full video on YouTube 🔗" (overlay at 50s mark)

   Instagram Reels:
   ├─ Hook: First 5 seconds (slightly more forgiving)
   ├─ Text: Cleaner, less chaotic (Instagram aesthetic)
   ├─ Music: Instagram music library (avoid copyright)
   └─ CTA: "Link in bio for full breakdown" (text overlay)

7. EXPORT:
   ├─ Resolution: 1080×1920
   ├─ Codec: H.264
   ├─ Bitrate: 8-10 Mbps
   ├─ File size: <100MB (upload efficiency)
   └─ Filename: [YYYYMMDD]_[Topic]_TikTok.mp4 / _Reel.mp4
```

**YouTube → Twitter/X (Thread):**

```
THREAD STRUCTURE:

Tweet 1 (Hook + Link):
"[Compelling stat or question from video] 🧵

I just broke down [topic] in my latest video.

Here are the 5 key insights you can't miss: 👇

[YouTube link]"

Tweet 2-6 (Key Takeaways):
"1/ [First insight - 280 characters]

[Visual: Screenshot from video or infographic]"

"2/ [Second insight - 280 characters]

[Supporting stat or example]"

[Continue for 3-5 key points...]

Final Tweet (CTA):
"That's the breakdown. For the full deep-dive with examples and tools:

📹 Watch here: [YouTube link]

🔔 Subscribe if you want more [niche] insights every [frequency].

What's your take on [topic]? Let me know below! 👇"

FORMAT:
├─ Numbered list (1/, 2/, 3/...)
├─ Visual every 2-3 tweets (screenshots, graphs)
├─ Emojis sparingly (not excessive)
└─ Reply to own thread (engagement boost)
```

**YouTube → LinkedIn (Professional Adaptation):**

```
POST STRUCTURE:

"[Professional angle on topic]

After analyzing [X sources / Y hours of research / Z case studies], here's what the data reveals about [topic]:

🔹 Insight 1 (Business impact)
🔹 Insight 2 (Professional application)
🔹 Insight 3 (Industry trend)

[Optional: Personal anecdote or case study - 2-3 sentences]

I put together a comprehensive breakdown (video below) covering:
• [Key point 1]
• [Key point 2]
• [Key point 3]

[Embed YouTube video link - LinkedIn auto-generates preview]

What's your experience with [topic]? Drop your thoughts in the comments.

#IndustryTag #ProfessionalTag #TopicTag"

TONE: More formal, data-driven, less casual than YouTube/TikTok
FREQUENCY: 1-2x per week (less spammy than daily)
```

### 4.3 Cross-Platform Traffic Funnel

**Funnel Architecture:**

```
┌─────────────────────────────────────────────────────────────────┐
│                   TRAFFIC FUNNEL STRATEGY                        │
└─────────────────────────────────────────────────────────────────┘

DISCOVERY LAYER (Top of Funnel):
├─ TikTok: Viral short clips (60s hooks)
├─ Instagram Reels: Viral short clips (90s hooks)
├─ Twitter: Trending threads (text-based)
└─ LinkedIn: Professional summaries

     ↓ (CTA: "Full video on YouTube")

ENGAGEMENT LAYER (Middle of Funnel):
└─ YouTube: Full-length video (5-15 minutes)
    ├─ Delivers on promise from short clips
    ├─ Provides depth and value
    └─ CTA: Subscribe + watch related videos

     ↓ (End screens, cards, pinned comments)

LOYALTY LAYER (Bottom of Funnel):
├─ YouTube Subscriptions: Consistent weekly viewers
├─ Newsletter: Email list (owned audience)
├─ Community Tab: Direct engagement
└─ Twitch (if applicable): Live interaction

     ↓ (Monetization opportunities)

MONETIZATION LAYER:
├─ YouTube AdSense (passive)
├─ Sponsorships (video integrations)
├─ Affiliate products (pinned comments, description)
├─ Digital products (courses, templates)
└─ Twitch subs/donations (if applicable)
```

**Conversion Optimization:**

| Funnel Stage | Platform | CTA | Conversion Target |
|--------------|----------|-----|-------------------|
| **Discovery** | TikTok/IG Reels | "Full video on YouTube 🔗" | 2-5% CTR to YouTube |
| **Discovery** | Twitter Thread | "[YouTube link]" | 3-7% CTR to YouTube |
| **Engagement** | YouTube Video | "Subscribe + Watch next" | 1-2% sub conversion |
| **Loyalty** | YouTube Community | "Join newsletter for..." | 5-10% email signup |
| **Monetization** | YouTube Video | "Check out [affiliate product]" | 0.5-2% product CTR |

---

## 5. TOOL STACK & DECISION MATRICES

### 5.1 Complete Tool Ecosystem

**TIER 1: ESSENTIAL (Required for all production)**

| Tool | Category | Purpose | Cost | Priority |
|------|----------|---------|------|----------|
| **Perplexity Pro** | Research | Source-backed research briefs | $20/mo | CRITICAL |
| **Claude** | AI Assistant | Script drafting + refinement | $20/mo | CRITICAL |
| **DaVinci Resolve** | Video Editing | Complete post-production | FREE | CRITICAL |
| **ElevenLabs** | AI Voice | Voiceover generation | $22/mo | CRITICAL |
| **Canva Pro** | Design | Thumbnail + graphics | $13/mo | HIGH |
| **Epidemic Sound** | Music | Royalty-free music | $15/mo | HIGH |

**TIER 1 TOTAL:** $90/mo (Solo creator minimum viable stack)

---

**TIER 2: OPTIMIZATION (Quality & efficiency boost)**

| Tool | Category | Purpose | Cost | Priority |
|------|----------|---------|------|----------|
| **Originality.ai** | Fact-Checking | Claim verification | $14.95/mo | HIGH |
| **VidIQ / TubeLab** | Analytics | Niche validation + keyword research | $19-39/mo | HIGH |
| **Trinka AI** | Consistency | Series script consistency | $20/mo | MEDIUM |
| **ChatGPT Plus** | AI Assistant | Rapid iteration alternative to Claude | $20/mo | MEDIUM |
| **Reaper / Audition** | Audio DAW | Professional audio mixing | FREE / $20/mo | MEDIUM |
| **After Effects** | Animation | Professional motion graphics | $20/mo | MEDIUM |

**TIER 2 TOTAL:** $94-134/mo (Professional quality threshold)

---

**TIER 3: SCALE & EXPANSION (Multi-platform, high-volume production)**

| Tool | Category | Purpose | Cost | Priority |
|------|----------|---------|------|----------|
| **Artlist** | Music (Alternative) | Cinematic music library | $14.99/mo | LOW |
| **Storyblocks** | Stock Video | Premium b-roll library | $30/mo | LOW |
| **MotionElements** | Templates | Pre-made animation templates | $16.50/mo | LOW |
| **TubeBuddy** | YouTube Tools | Metadata optimization | $9-50/mo | LOW |
| **Runway Gen-2** | AI Video | Custom b-roll generation | $12-76/mo | LOW |
| **Fabric CLI** | AI Patterns | Content analysis automation | FREE | LOW |
| **OBS Studio** | Screen Recording | Software demos, live streaming | FREE | LOW |

**TIER 3 TOTAL:** $82-166/mo (Production team scale)

---

**FULL STACK TOTAL:** $266-390/mo (Complete production capability)

### 5.2 Tool Selection Decision Trees

**DECISION TREE 1: Research Tool Selection**

```
┌─────────────────────────────────────────────────────────────────┐
│           WHEN TO USE WHICH RESEARCH TOOL?                       │
└─────────────────────────────────────────────────────────────────┘

START: Need to research topic for video

Q1: Is topic time-sensitive (news, trends, 2025-2026 data)?
├─ YES → Use Perplexity (real-time web search, current sources)
└─ NO → Continue to Q2

Q2: Do you need competitor content analysis (YouTube videos)?
├─ YES → Use Fabric (extract_wisdom pattern)
└─ NO → Continue to Q3

Q3: Do you need structured brainstorming (idea generation)?
├─ YES → Use Claude (creative ideation prompts)
└─ NO → Continue to Q4

Q4: Do you need niche validation (search volume, competition)?
├─ YES → Use VidIQ or TubeLab (keyword research tools)
└─ NO → Default to Perplexity (general research)

COMBINATIONS (Common workflows):
├─ NEW TOPIC: Perplexity (research) → VidIQ (validation) → Claude (outline)
├─ COMPETITOR ANALYSIS: Fabric (extract) → Perplexity (verify) → Claude (synthesize)
└─ TRENDING CONTENT: Perplexity (trends) → Fabric (top videos) → Claude (angle development)
```

**DECISION TREE 2: AI Voice Tool Selection**

```
START: Need AI voiceover for video

Q1: What is your budget?
├─ FREE: Use Murf.ai free tier (limited minutes) or Natural Readers
├─ <$10/mo: ElevenLabs Starter ($5/mo, 30K chars)
├─ $10-30/mo: Continue to Q2
└─ $30+/mo: ElevenLabs Creator+ ($99/mo, unlimited)

Q2: Do you need voice cloning (custom voice)?
├─ YES → ElevenLabs ($22/mo, instant cloning) or Descript Overdub ($24/mo)
└─ NO → Continue to Q3

Q3: Do you need ultra-realistic quality (indistinguishable from human)?
├─ YES → ElevenLabs (9.5/10 quality rating)
└─ NO → Continue to Q4

Q4: Do you need multi-language support (10+ languages)?
├─ YES → Play.ht (900+ voices, 142 languages)
└─ NO → Continue to Q5

Q5: Do you need team collaboration (multiple editors)?
├─ YES → Murf.ai ($19/mo, team features)
└─ NO → ElevenLabs (best solo creator value)

RECOMMENDATION MATRIX:
├─ SOLO CREATOR, QUALITY FOCUS: ElevenLabs Creator ($22/mo)
├─ TEAM, COLLABORATION: Murf.ai Professional ($75/mo)
├─ BUDGET, ACCEPTABLE QUALITY: Speechify ($139/yr = $11.58/mo)
└─ VOICE CLONING SPECIALIST: Descript Overdub ($24/mo, editing integration)
```

**DECISION TREE 3: Video Editing Software Selection**

```
START: Need video editing software

Q1: What is your budget?
├─ FREE: Continue to Q2
├─ <$50/mo: Continue to Q3
└─ >$50/mo: Adobe Premiere Pro ($54.99/mo, industry standard)

Q2: (FREE OPTIONS) What is your skill level?
├─ BEGINNER: CapCut (free, mobile-first, templates)
├─ INTERMEDIATE: DaVinci Resolve (free, professional features)
├─ ADVANCED: DaVinci Resolve (free) + Blender (free, VFX/3D)
└─ Proceed to Q4

Q3: (<$50/mo) What is your primary need?
├─ COLOR GRADING: DaVinci Resolve Studio ($295 one-time)
├─ MOTION GRAPHICS: After Effects ($20/mo)
├─ ALL-IN-ONE: Final Cut Pro ($299 one-time, Mac only)
└─ Proceed to Q4

Q4: Do you need advanced color grading (Hollywood-level)?
├─ YES → DaVinci Resolve (free) or Studio ($295)
└─ NO → Continue to Q5

Q5: Do you need motion graphics / VFX integration?
├─ YES → After Effects ($20/mo) or Resolve Fusion (free, built-in)
└─ NO → Continue to Q6

Q6: What is your operating system?
├─ MAC: Final Cut Pro ($299) or DaVinci Resolve (free)
├─ WINDOWS: DaVinci Resolve (free) or Adobe Premiere ($55/mo)
└─ LINUX: DaVinci Resolve (free) or Kdenlive (free, limited)

DEADMANAI RECOMMENDATION:
└─ DaVinci Resolve (FREE version)
    ├─ Rationale: Professional features, zero cost, color grading excellence
    ├─ Fusion built-in (motion graphics)
    ├─ Fairlight audio (professional DAW)
    └─ Upgrade to Studio ($295) only if rendering >4K or using AI tools
```

**DECISION TREE 4: Music Licensing Selection**

```
START: Need music for video

Q1: What is your budget?
├─ FREE: Continue to Q2
├─ <$20/mo: Continue to Q3
└─ >$20/mo: Artlist ($299/yr = $24.92/mo, unlimited cinematic)

Q2: (FREE OPTIONS) What is acceptable quality trade-off?
├─ ACCEPTABLE: YouTube Audio Library (1,000+ tracks, decent quality)
├─ REQUIRES ATTRIBUTION: Uppbeat (1,500+ tracks, credit in description)
└─ VERY LIMITED: Free Music Archive (hit-or-miss quality)

Q3: (<$20/mo) What is your production volume?
├─ 1-5 videos/month: AudioJungle ($1-50 per track, pay-per-use)
├─ 5-15 videos/month: Epidemic Sound ($15/mo, unlimited)
└─ 15+ videos/month: Artlist ($24.92/mo, unlimited + SFX)

Q4: Do you need sound effects (SFX) in addition to music?
├─ YES → Artlist ($24.92/mo, includes SFX library)
└─ NO → Epidemic Sound ($15/mo, music only)

Q5: Do you need cinematic/emotional music (film-quality)?
├─ YES → Artlist (curated for emotion, high production value)
└─ NO → Epidemic Sound (broader variety, upbeat/electronic strong)

DEADMANAI RECOMMENDATION:
├─ STARTING OUT (1-2 videos/week): Epidemic Sound ($15/mo)
│   └─ Rationale: Best value, 40K+ tracks, YouTube license included
└─ SCALING UP (3+ videos/week): Artlist ($24.92/mo)
    └─ Rationale: Cinematic quality, SFX included, unlimited downloads
```

### 5.3 Cost Optimization Strategies

**Budget Tier Recommendations:**

**BOOTSTRAP BUDGET ($0-50/mo):**
```
ESSENTIAL SPEND:
├─ Perplexity Pro: $20/mo (research)
├─ Claude: $20/mo (scripting)
└─ ElevenLabs Starter: $5/mo (voice, 30K chars)

FREE ALTERNATIVES:
├─ DaVinci Resolve: FREE (editing)
├─ Canva Free: FREE (thumbnails, limited templates)
├─ YouTube Audio Library: FREE (music)
├─ Pexels/Pixabay: FREE (stock b-roll)
├─ Audacity: FREE (audio mixing)

TOTAL: $45/mo
PRODUCTION CAPABILITY: 1-2 videos/week, acceptable quality
```

**PROFESSIONAL BUDGET ($100-200/mo):**
```
CORE STACK:
├─ Perplexity Pro: $20/mo
├─ Claude: $20/mo
├─ ElevenLabs Creator: $22/mo
├─ Canva Pro: $13/mo
├─ Epidemic Sound: $15/mo
├─ Originality.ai: $14.95/mo
├─ VidIQ: $19/mo

FREE TOOLS:
├─ DaVinci Resolve: FREE
├─ Reaper: FREE (audio)
├─ Pexels: FREE (b-roll)

TOTAL: $123.95/mo
PRODUCTION CAPABILITY: 3-4 videos/week, professional quality
```

**PRODUCTION TEAM BUDGET ($300-500/mo):**
```
FULL STACK:
├─ Perplexity Pro: $20/mo
├─ Claude: $20/mo
├─ ChatGPT Team: $30/user/mo (2 users = $60)
├─ ElevenLabs Professional: $99/mo (unlimited)
├─ Canva Pro: $13/mo
├─ Artlist: $24.92/mo (music + SFX)
├─ Originality.ai: $14.95/mo
├─ VidIQ Pro: $39/mo
├─ Trinka AI: $20/mo
├─ Storyblocks: $30/mo (premium b-roll)
├─ Adobe Creative Cloud: $54.99/mo (After Effects, Audition)

FREE TOOLS:
├─ DaVinci Resolve Studio: $295 (one-time, amortized)

TOTAL: $395.86/mo + $295 one-time
PRODUCTION CAPABILITY: 5-7 videos/week, broadcast quality
```

**ROI Calculation (Monetization Breakeven):**

```
SCENARIO: Professional Budget ($124/mo)

YOUTUBE REVENUE REQUIREMENTS (to break even):
├─ CPM: $10 (average educational/tech content)
├─ RPM: $4 (40% of CPM after YouTube cut)
├─ Views needed: 31,000 views/month (124 ÷ $4 per 1,000 views)
├─ Per video (4 videos/mo): 7,750 views/video

TIMEFRAME TO BREAKEVEN:
├─ Month 1-3: Unlikely (building audience)
├─ Month 4-6: Possible (if viral hit or strong niche)
├─ Month 7-12: Probable (consistent quality + SEO)
└─ Month 12+: Expected (compound growth, evergreen library)

ADDITIONAL REVENUE STREAMS (Accelerate breakeven):
├─ Sponsorships: $200-1,000/video (at 10K+ subs)
├─ Affiliate commissions: $50-500/month (depending on niche)
├─ Digital products: $100-2,000/month (courses, templates)
└─ Twitch subs/donations: $50-500/month (if applicable)

INVESTMENT MINDSET:
"First 6-12 months = R&D investment, not profit expectation.
Quality content compounds. Build library, growth follows."
```

---

## 6. QUALITY GATES & VERIFICATION SYSTEM

### 6.1 Four-Gate Quality Control Framework

**Gate Architecture (NASA NPR 8735.2C Adapted):**

```
┌─────────────────────────────────────────────────────────────────┐
│                   4-GATE QUALITY SYSTEM                          │
│              (Mandatory Checkpoints for All Content)             │
└─────────────────────────────────────────────────────────────────┘

PHASE 1: IDEATION & VALIDATION
      ↓
  GATE 1: STRATEGIC VALIDATION
  ├─ Strategic alignment verified
  ├─ Viral potential assessed (STEPPS ≥18/30)
  ├─ Search demand validated (Ratio ≥2.0x OR trending)
  └─ Series potential confirmed (≥5 related videos possible)
      ↓ PASS → Proceed to Phase 2
      ↓ FAIL → Return to topic selection

PHASE 2: RESEARCH & SCRIPTING (Outline)
      ↓
  GATE 2: COVERAGE CHECK
  ├─ All sections have research (3+ sources per claim)
  ├─ Structure matches retention pattern (hook→body→CTA)
  ├─ Timing estimates within ±10% of target
  └─ Hook, body, CTA sections clearly defined
      ↓ PASS → Proceed to draft generation
      ↓ FAIL → Return to research (insufficient depth)

PHASE 2: RESEARCH & SCRIPTING (Draft)
      ↓
  GATE 3: COMPLETENESS CHECK
  ├─ All outline beats developed into dialogue
  ├─ Visual cues present for 80%+ of content
  ├─ Timing within ±10% of target
  └─ Voice/tone consistent (Trinka AI for series)
      ↓ PASS → Proceed to verification
      ↓ FAIL → Generate alternative draft

PHASE 3: VERIFICATION & REFINEMENT
      ↓
  GATE 4: FACT INTEGRITY & READINESS
  ├─ All claims cited (>95% coverage)
  ├─ No contradicting sources (red flags resolved)
  ├─ Hook strength ≥18/25 on rubric
  ├─ Pacing consistent (variance <10%)
  ├─ CTA clear and compelling
  └─ Brand voice matches channel identity
      ↓ PASS → APPROVED FOR PRODUCTION
      ↓ FAIL → Return to refinement or fact-checking

CONTINUOUS: POST-PRODUCTION QA CHECKPOINTS
├─ Visual QA (Phase 4): Thumbnail legibility, b-roll alignment
├─ Audio QA (Phase 5): LUFS -14 to -16, no clipping
├─ Edit QA (Phase 6): Pacing 15-25 cuts/min, pattern interrupts
└─ Publish QA (Phase 7): Metadata optimized, end screens configured
```

### 6.2 Gate-Specific Verification Checklists

**GATE 1: STRATEGIC VALIDATION (Phase 1 → Phase 2)**

```markdown
## GATE 1 CHECKLIST: STRATEGIC VALIDATION

**Topic:** [Topic Title]
**Date:** [YYYY-MM-DD]
**Reviewer:** [Human name]

### 1. AUDIENCE DEMAND
- [ ] Search volume ≥1,000 monthly searches (VidIQ/TubeLab data)
- [ ] Search Demand Ratio ≥2.0x (searches ÷ active channels)
  - Ratio: _____ (Calculate: [X searches] ÷ [Y channels])
- [ ] OR: Trending signal present (Google Trends upward, Twitter buzz)

### 2. VIRAL POTENTIAL (STEPPS Framework)
- [ ] STEPPS Score ≥18/30 (see viral scorecard in notes.md)
  - Score: ___/30
- [ ] High-arousal emotion present (awe, excitement, anger, anxiety)
- [ ] Practical value clear (viewers can apply insights)

### 3. STRATEGIC ALIGNMENT
- [ ] Aligns with channel niche (not random pivot)
- [ ] Sustainable topic (can generate 5+ related videos)
- [ ] List 5 related video ideas:
  1. _______________________________
  2. _______________________________
  3. _______________________________
  4. _______________________________
  5. _______________________________
- [ ] Matches audience persona (see R36 Audience Persona)
- [ ] Fits 70/20/10 content mix (Evergreen/Trending/Experimental)
  - Classification: [Evergreen / Trending / Experimental]
- [ ] CPM potential acceptable (≥$4 for sustainability)
  - Estimated CPM: $_____
- [ ] Human creator passion/interest present (burnout check)

### 4. DECISION
- [ ] **PASS:** All critical criteria met → Proceed to Phase 2
- [ ] **CONDITIONAL PASS:** Minor gaps, document mitigation plan
- [ ] **FAIL:** Return to topic selection → Document reason

**Approval Signature:** _________________ **Date:** __________
```

---

**GATE 2: COVERAGE CHECK (Outline → Draft)**

```markdown
## GATE 2 CHECKLIST: COVERAGE CHECK

**Video:** [Title]
**Script Outline:** script_outline.md
**Date:** [YYYY-MM-DD]
**Reviewer:** [Human name]

### 1. RESEARCH DEPTH
- [ ] All major sections have supporting research
- [ ] Each claim supported by 3+ authoritative sources
  - Claims without sources: _____ (Target: 0)
- [ ] Research documented in research_brief.md
- [ ] Sources diverse (not all from single origin)

### 2. STRUCTURE VALIDATION
- [ ] Hook section present (0-15 seconds)
  - Hook type: [Stat / Question / Promise / Cold Open]
- [ ] Body sections logical (3-5 main points)
  - Number of sections: _____
- [ ] CTA section present (final 5-20 seconds)
  - CTA ask: [Subscribe / Comment / Watch Next / Other: _____]
- [ ] Structure matches retention pattern (see R64)

### 3. TIMING ACCURACY
- [ ] Total estimated duration: _____ seconds (Target: _____ seconds)
- [ ] Deviation from target: _____% (Acceptable: ±10%)
- [ ] Section breakdowns:
  - Hook: ___s (Target: 10-15s)
  - Body: ___s (Target: 60-80% of video)
  - CTA: ___s (Target: 5-20s)

### 4. COMPLETENESS
- [ ] Hook clearly defined (curiosity gap + value signal)
- [ ] Body beats numbered and sequenced
- [ ] Transition hooks between sections ("But here's the thing...")
- [ ] Pattern interrupt opportunities marked (every 60-90s)
- [ ] CTA specific and singular (not multiple asks)

### 5. DECISION
- [ ] **PASS:** All sections researched, structure sound → Proceed to draft
- [ ] **CONDITIONAL PASS:** Minor research gaps, proceed with flags
- [ ] **FAIL:** Insufficient research depth → Return to Phase 1

**Approval Signature:** _________________ **Date:** __________
```

---

**GATE 3: COMPLETENESS CHECK (Draft → Verification)**

```markdown
## GATE 3 CHECKLIST: COMPLETENESS CHECK

**Video:** [Title]
**Script Draft:** script_draft_v1.md
**Date:** [YYYY-MM-DD]
**Reviewer:** [Human name]

### 1. OUTLINE FIDELITY
- [ ] All outline beats developed into full dialogue
  - Underdeveloped beats: _____ (Target: 0)
- [ ] No placeholder text (e.g., "[INSERT FACT HERE]")
- [ ] Narrative flow coherent (reads smoothly)

### 2. VISUAL/AUDIO CUES
- [ ] Visual cues present for 80%+ of content
  - [VISUAL CUE] count: _____ (Check against script length)
- [ ] Audio cues marked ([BREATH], [MUSIC SHIFT], etc.)
- [ ] Text overlays indicated for key points
- [ ] All cues actionable (editor can execute without guessing)

### 3. TIMING VALIDATION
- [ ] Word count: _____ words (150 words ≈ 1 minute spoken)
- [ ] Estimated duration: _____ minutes (Word count ÷ 150)
- [ ] Deviation from target: _____% (Acceptable: ±10%)
- [ ] Pacing variance: <10% (no sections too slow/fast)

### 4. CONSISTENCY (Series Only)
- [ ] Tone matches STYLE_GUIDE.md (if series)
- [ ] Terminology consistent (Trinka AI check run)
  - Inconsistencies found: _____ (Target: <5)
- [ ] Character voices consistent (if applicable)
- [ ] Brand voice present (matches channel identity)

### 5. ENGAGEMENT MECHANISMS
- [ ] Hook strength (0-15s): Strong enough to retain 75%+?
  - Preliminary score: ___/25 (will refine in Gate 4)
- [ ] Mid-roll hooks present (section transitions)
- [ ] Questions to engage viewer ("Have you ever wondered...")
- [ ] Cliffhangers before potential drop-offs

### 6. DECISION
- [ ] **PASS:** Complete, consistent, engaging → Proceed to verification
- [ ] **CONDITIONAL PASS:** Minor polish needed, flag for refinement
- [ ] **FAIL:** Incomplete or inconsistent → Generate alternative draft

**Approval Signature:** _________________ **Date:** __________
```

---

**GATE 4: FACT INTEGRITY & READINESS (Verification → Production)**

```markdown
## GATE 4 CHECKLIST: FACT INTEGRITY & READINESS

**Video:** [Title]
**Script Version:** script_final.md
**Date:** [YYYY-MM-DD]
**Reviewer:** [Human name]

### 1. FACT-CHECKING
- [ ] Originality.ai check run (if available)
  - Flagged claims: _____ (Green / Yellow / Red breakdown)
- [ ] All YELLOW flags resolved (sources added)
- [ ] All RED flags resolved (claims verified or removed)
- [ ] Citation coverage: _____% (Target: >95%)
- [ ] All statistics traceable to original source
- [ ] No contradicting sources (conflicts resolved)

### 2. CITATION INTEGRATION
- [ ] All claims have inline citations
  - Format: "[CITATION: Source, Year]"
- [ ] Sources documented in sources.md
- [ ] Sources authoritative (peer-reviewed > news > blog)
- [ ] Sources recent (2025-2026 preferred for time-sensitive topics)

### 3. HOOK STRENGTH
- [ ] Hook Scorecard completed (see Phase 3, Task 3.4)
  - **Curiosity Gap:** ___/5
  - **Emotional Spike:** ___/5
  - **Specificity:** ___/5
  - **Relevance:** ___/5
  - **Uniqueness:** ___/5
  - **TOTAL:** ___/25 (Target: ≥18)
- [ ] First 15 seconds tested (read aloud, compelling?)
- [ ] Hook revised if score <18 (mandatory)

### 4. PACING & FLOW
- [ ] Pacing variance <10% throughout
  - Slowest section: _____ WPM
  - Fastest section: _____ WPM
  - Variance: _____% (Calculate: (Max-Min)/Avg × 100)
- [ ] Transitions smooth (no jarring section changes)
- [ ] Pattern interrupts confirmed (every 60-90s)
- [ ] Reading aloud test passed (no tongue-twisters)

### 5. CALL-TO-ACTION
- [ ] CTA clear and singular (one ask, not multiple)
- [ ] CTA compelling (value reinforcement: "If you want more...")
- [ ] CTA placement: Final 5-20 seconds
- [ ] CTA aligns with video goal (Subscribe / Comment / Watch Next)

### 6. BRAND VOICE
- [ ] Matches channel personality (see STYLE_GUIDE.md)
- [ ] Tone consistent with previous videos (if established channel)
- [ ] Terminology aligns with audience (8th-grade reading level check)
- [ ] No off-brand language or tangents

### 7. FINAL READINESS
- [ ] Script ready for voiceover generation (no further edits needed)
- [ ] All sections complete (no placeholders)
- [ ] Human editorial review completed (this checklist)
- [ ] Approval to proceed to production granted

### 8. DECISION
- [ ] **APPROVED:** All criteria met → Proceed to Phase 4 (Visual Production)
- [ ] **CONDITIONAL APPROVAL:** Minor issues, proceed with monitoring
- [ ] **REJECTED:** Return to Phase 3 (Refinement) or Phase 2 (Fact-checking)
  - Reason for rejection: _________________________________

**Approval Signature:** _________________ **Date:** __________
```

### 6.3 Continuous QA Checkpoints (Post-Production)

**POST-PRODUCTION QA CHECKLIST (Phases 4-7)**

```markdown
## POST-PRODUCTION QA CHECKLIST

**Video:** [Title]
**Export File:** exports/[FILENAME].mp4
**Date:** [YYYY-MM-DD]
**QA Reviewer:** [Human name]

---

### PHASE 4: VISUAL PRODUCTION QA

**Thumbnail:**
- [ ] Custom thumbnail uploaded (not auto-generated)
- [ ] 3-second legibility test passed (resize to 240×180px, readable?)
- [ ] Contrast ratios meet standards (4.5:1 text, 7:1 primary element)
- [ ] Mobile tested (legible on phone screen)
- [ ] Text: 3-7 words maximum
- [ ] Brand consistency (colors, fonts match channel)

**B-roll & Assets:**
- [ ] All [VISUAL CUE] requirements from script have sourced assets
- [ ] B-roll quality acceptable (not pixelated, relevant to narration)
- [ ] Asset library organized (clear naming convention)
- [ ] No copyright violations (all stock/AI/original)

**Animation:**
- [ ] Animation templates saved for reuse (if created)
- [ ] Timing appropriate (0.3-0.5s for text, 2-3s on-screen)
- [ ] No stuttering or lag
- [ ] Brand elements consistent (logo, colors)

---

### PHASE 5: AUDIO PRODUCTION QA

**Voiceover:**
- [ ] Clarity: All words clearly intelligible
- [ ] Pronunciation: No errors (re-generated if issues)
- [ ] Pacing: 130-160 WPM (appropriate to content)
- [ ] Emotional tone: Matches script cues
- [ ] No robotic artifacts (sounds natural)

**Processing:**
- [ ] Background noise removed (Noise Gate working)
- [ ] Volume consistent (Compression applied)
- [ ] No harsh sibilance (De-esser applied)
- [ ] Breath sounds natural (reduced, not eliminated)

**Mixing:**
- [ ] Voice loudest element (-12 to -6 dBFS)
- [ ] Music 12-18 dB below voice (ducking working)
- [ ] SFX appropriate level (not overpowering)
- [ ] No audio clipping (red peaks in meter)

**Loudness Standards:**
- [ ] Integrated LUFS: -14 to -16 (YouTube spec)
  - Measured LUFS: _____ (Use Youlean or built-in meter)
- [ ] True Peak: -1 dBTP (prevents clipping)
  - Measured True Peak: _____ dBTP
- [ ] Loudness Range (LRA): 4-9
  - Measured LRA: _____

---

### PHASE 6: EDITING & POST-PRODUCTION QA

**Visual Elements:**
- [ ] No black frames or gaps in timeline
- [ ] All b-roll clips aligned with voiceover
- [ ] Text overlays readable (3-second rule, mobile tested)
- [ ] Animations smooth (no stuttering)
- [ ] Color grading consistent across all clips
- [ ] No jarring visual shifts

**Pacing:**
- [ ] Cut frequency: 15-25 cuts/min (educational/entertainment)
  - Measured cuts/min: _____ (Count cuts ÷ duration)
- [ ] Pattern interrupts: Every 60-90 seconds
  - Interrupt count: _____ (Check timing marks)
- [ ] Scene duration: 4-8 seconds average (no scenes >15s)
- [ ] No dead air (silence >3 seconds without purpose)

**Technical:**
- [ ] Timeline framerate consistent (24/30/60 fps, no mixed)
- [ ] Resolution: 1920×1080 minimum (or 3840×2160 for 4K)
- [ ] Aspect ratio: 16:9 (YouTube standard)
- [ ] Total duration matches target (±10% acceptable)
  - Target: _____ min | Actual: _____ min | Variance: _____%

---

### PHASE 7: PUBLISHING & DISTRIBUTION QA

**Metadata:**
- [ ] Title: 50-60 characters, front-loaded, power words
  - Character count: _____ (Target: 50-60)
- [ ] Description: First 2 lines compelling, timestamps present
- [ ] Tags: 15-20 tags, brand tag first, hierarchy followed
  - Tag count: _____
- [ ] Primary keyword in title + first sentence of description

**YouTube Configuration:**
- [ ] Custom thumbnail uploaded (thumbnail_A.png or variant)
- [ ] End screen configured (5-20s, 4 elements max)
  - Elements: [Video / Subscribe / Playlist / Website]
- [ ] Cards placed (2-3 cards, strategic timing)
  - Card count: _____
- [ ] Playlist assignment (video added to relevant playlist)
- [ ] Captions: Auto-generated or .srt uploaded

**Multi-Platform (if applicable):**
- [ ] TikTok adaptation uploaded (60s vertical)
- [ ] Instagram Reel adaptation uploaded (90s vertical)
- [ ] Twitter thread posted (with YouTube link)
- [ ] LinkedIn post (if professional content)

**Publishing:**
- [ ] Visibility: Public or scheduled for optimal time
  - Publish time: [Day, Time EST]
- [ ] Monetization enabled (if eligible)
- [ ] Comments enabled (engagement)
- [ ] Embedding allowed (reach expansion)

---

### FINAL SIGN-OFF

**Overall QA Status:**
- [ ] **APPROVED:** All checkpoints passed → Publish immediately
- [ ] **APPROVED WITH NOTES:** Minor issues documented, monitor post-publish
- [ ] **REJECTED:** Critical issues found → Fix before publishing
  - Critical issues: _________________________________

**QA Reviewer Signature:** _________________ **Date:** __________
**Final Approval (Human):** _________________ **Date:** __________
```

---

## 7. HUMAN-IN-LOOP ENFORCEMENT

### 7.1 Human Decision Authority Matrix

**Decision Classification System:**

```
┌─────────────────────────────────────────────────────────────────┐
│              HUMAN-IN-LOOP DECISION MATRIX                       │
│         (AI Suggests, Human Decides, AI Executes)                │
└─────────────────────────────────────────────────────────────────┘

CRITICALITY LEVELS:

[CRITICAL] - Human MUST decide, AI cannot proceed without approval
├─ Strategic: Niche selection, channel direction, brand positioning
├─ Creative: Final script approval, thumbnail concept, voice selection
├─ Editorial: Fact dispute resolution, controversial claims, tone shifts
└─ Financial: Tool purchases, sponsorship deals, monetization strategy

[HIGH] - Human should decide, AI can suggest but not finalize
├─ Tactical: Content calendar, publishing schedule, series planning
├─ Quality: Hook strength assessment, engagement mechanism approval
├─ Optimization: A/B test interpretation, analytics-driven pivots
└─ Collaboration: Team workflows, handoff protocols

[MEDIUM] - Human reviews AI decision, veto power retained
├─ Execution: B-roll selection, animation timing, color grading
├─ Technical: Export settings, compression ratios, file formats
├─ Metadata: Tag variations, description wording, hashtag selection
└─ Iteration: Refinement passes, polish edits, minor adjustments

[LOW] - AI decides autonomously, human informed post-facto
├─ Automated: File naming, folder organization, backup execution
├─ Standardized: Audio processing chain (if template established)
├─ Repetitive: Batch operations, template applications
└─ Data: Analytics aggregation, metric calculations

---

ENFORCEMENT MECHANISM:

At each CRITICAL decision point:
1. AI presents 2-5 options with rationale
2. AI recommends preferred option (with reasoning)
3. Human reviews, selects, or requests additional options
4. AI documents decision in notes.md (rationale + timestamp)
5. AI executes based on human selection
```

### 7.2 Decision Point Examples (Phase-by-Phase)

**PHASE 1: IDEATION & VALIDATION**

| Decision Point | Criticality | AI Role | Human Role |
|----------------|-------------|---------|------------|
| Niche selection | [CRITICAL] | Research data (search volume, competition, CPM), present 3-5 options with pros/cons | Final selection based on passion + data |
| STEPPS scoring | [HIGH] | Calculate scores, highlight viral potential | Validate score (gut check: "Would I share this?") |
| Topic prioritization | [CRITICAL] | Rank by viral potential + demand | Choose based on strategic fit + interest |

**Example Workflow:**
```
AI: "I've analyzed 10 topic candidates. Here are the top 3:

1. '5 AI Tools Replacing Jobs in 2026'
   - Search volume: 8,200/mo
   - Competition: 23 channels (Ratio: 356x - UNTAPPED)
   - STEPPS: 24/30 (High viral potential)
   - CPM: $12-18 (Tech/Business)
   - Your passion fit: Medium (interested but not expert)

2. 'How I Automate 90% of My Content Creation'
   - Search volume: 2,400/mo
   - Competition: 67 channels (Ratio: 36x - MODERATE)
   - STEPPS: 21/30 (Good practical value)
   - CPM: $8-12 (Marketing/Tools)
   - Your passion fit: High (personal experience)

3. 'AI Ethics: The Dark Side Nobody Talks About'
   - Search volume: 1,800/mo
   - Competition: 12 channels (Ratio: 150x - UNTAPPED)
   - STEPPS: 26/30 (High emotion + controversy)
   - CPM: $6-10 (Broad appeal)
   - Your passion fit: High (personal values)

RECOMMENDATION: Option 3 (Ethics) - Highest STEPPS, untapped niche, strong passion alignment. Caveat: Lower CPM, but sustainability likely higher.

Which topic do you want to pursue?"
HUMAN RESPONSE: [Selects option, provides rationale]

AI: "Confirmed. Proceeding with Option [X]. Documenting in notes.md and task_plan.md."
```

**PHASE 2-3: RESEARCH & SCRIPTING**

| Decision Point | Criticality | AI Role | Human Role |
|----------------|-------------|---------|------------|
| Script structure selection | [CRITICAL] | Present template options (HBC/PAS/Listicle), recommend based on topic | Select structure that matches creative vision |
| Tone & voice | [CRITICAL] | Suggest tone based on audience persona, provide examples | Finalize tone (conversational/professional/energetic) |
| Source credibility (disputed claims) | [CRITICAL] | Flag contradicting sources, present evidence from both sides | Resolve dispute (choose source or remove claim) |
| Hook strength approval | [HIGH] | Score hook (0-25 rubric), suggest improvements | Approve or request revision (minimum 18/25) |

**Example Workflow (Source Dispute):**
```
AI: "Fact-checking flagged a RED issue:

CLAIM: 'AI will replace 80% of content creation jobs by 2027'

CONFLICTING SOURCES:
├─ Source A (Goldman Sachs, 2023): '300 million jobs affected globally, 18% of work automated'
├─ Source B (McKinsey, 2024): 'Generative AI could automate 60-70% of tasks in content/marketing'
├─ Source C (MIT, 2025): '15-25% job displacement, augmentation more likely than replacement'

ANALYSIS:
- Sources A & C: Conservative estimates (15-25% displacement)
- Source B: Task automation ≠ job elimination
- Original claim (80% jobs replaced): UNSUPPORTED

RECOMMENDATION: Revise to: 'AI could automate 60-70% of content tasks by 2027, but augmentation is more likely than full replacement (MIT, 2025)'

Do you approve this revision, or would you prefer to:
1. Remove the claim entirely
2. Hedge further ('Some estimates suggest...')
3. Research additional sources"

HUMAN RESPONSE: [Selects option 1, 2, 3, or provides alternative]
```

**PHASE 4-6: PRODUCTION**

| Decision Point | Criticality | AI Role | Human Role |
|----------------|-------------|---------|------------|
| Thumbnail concept | [CRITICAL] | Generate 3 design concepts, analyze competitor thumbnails | Select winning concept (aesthetic + brand fit) |
| Voice selection (first video) | [CRITICAL] | Generate samples with 3-5 voices, analyze tone/clarity | Choose voice that matches channel personality |
| Music mood | [HIGH] | Recommend 3-5 tracks matching emotional arc | Select track that resonates emotionally |
| B-roll clip selection | [MEDIUM] | Source clips matching [VISUAL CUE], filter by quality | Veto inappropriate clips, approve selection |
| Color grading style | [HIGH] | Suggest LUT based on channel vibe (vibrant/cinematic/neutral) | Approve or request adjustment |

### 7.3 AI Autonomy Boundaries

**What AI CAN Do Autonomously (No human approval needed):**

```
TIER 1: AUTOMATED EXECUTION (Post-decision)
├─ File organization (naming, folder structure)
├─ Template application (audio chain, video project)
├─ Batch processing (applying settings to multiple files)
├─ Data aggregation (analytics compilation)
├─ Backup execution (scheduled saves)
└─ Export rendering (once settings approved)

TIER 2: STANDARDIZED OPERATIONS (If template exists)
├─ Audio processing chain (using saved preset)
├─ Color grading (applying approved LUT)
├─ Text animation (using brand template)
├─ Metadata formatting (following established pattern)
└─ End screen configuration (using channel template)

TIER 3: RESEARCH & SUGGESTION (Informational, not decisional)
├─ Competitor analysis (presenting data, not interpreting)
├─ Trend identification (flagging opportunities)
├─ Performance reporting (metrics without recommendations)
└─ Tool research (comparing options, not purchasing)
```

**What AI CANNOT Do (Always requires human approval):**

```
FORBIDDEN AUTONOMY:
├─ Strategic pivots (niche changes, channel direction)
├─ Financial commitments (tool purchases, sponsorship acceptance)
├─ Publishing (uploading without human final review)
├─ Controversial claims (ethical/political/sensitive topics)
├─ Brand voice changes (tone shifts, terminology changes)
├─ Legal decisions (copyright disputes, licensing)
└─ Team delegation (assigning work to humans without approval)

RATIONALE: These decisions define channel identity, financial health, and legal standing. AI augments, never replaces, human creative and strategic authority.
```

---

**Document continues with Sections 8-15 as previously written...**
**[Sections 8-15 already exist in file - see full document above]**

---

**END OF PRODUCTION_WORKFLOW_ARCHITECTURE.md**
