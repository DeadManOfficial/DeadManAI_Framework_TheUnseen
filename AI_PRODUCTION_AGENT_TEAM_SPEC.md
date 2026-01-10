# AI PRODUCTION AGENT TEAM SPECIFICATION

**Document ID:** AI-AGENT-TEAM-DeadManAI-2026
**Date Compiled:** 2026-01-10
**Category:** Production Automation Architecture
**Status:** PRODUCTION READY
**Applicability:** HIGH (Core automation infrastructure)
**Dependency:** PRODUCTION_RESEARCH_SYNTHESIS.md, PRODUCTION_WORKFLOW_ARCHITECTURE.md

---

## 1. EXECUTIVE SUMMARY

### 1.1 Purpose

This document specifies the complete AI agent team for automating and augmenting DeadManAI faceless YouTube content production. All agents comply with the **3-Factor Ruling**:
- ✅ **Human-in-Loop**: All agents require human approval at critical decision points
- ✅ **Retention Velocity**: All agents optimize for audience retention and content quality
- ✅ **Asset Reusability**: All agents create reusable assets (templates, libraries, documentation)

### 1.2 Agent Architecture

```
PRODUCTION AGENT TEAM (5 Categories, 16 Specialized Agents)
═══════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ RESEARCH AGENTS (4)                                     │
├─────────────────────────────────────────────────────────┤
│ → Trend Scanner                                         │
│ → Deep Research Agent (NEW)                             │
│ → Keyword Researcher                                    │
│ → Audience Analyst                                      │
└─────────────────────────────────────────────────────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────┐
│ SCRIPTWRITING AGENTS (3)                                │
├─────────────────────────────────────────────────────────┤
│ → Hook Generator                                        │
│ → Structure Optimizer                                   │
│ → Fact Checker                                          │
└─────────────────────────────────────────────────────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────┐
│ PRODUCTION AGENTS (3)                                   │
├─────────────────────────────────────────────────────────┤
│ → B-roll Curator                                        │
│ → Music Selector                                        │
│ → QC Inspector                                          │
└─────────────────────────────────────────────────────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────┐
│ PUBLISHING AGENTS (3)                                   │
├─────────────────────────────────────────────────────────┤
│ → Metadata Optimizer                                    │
│ → Thumbnail A/B Tester                                  │
│ → Multi-Platform Distributor                            │
└─────────────────────────────────────────────────────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────┐
│ ANALYTICS AGENTS (3)                                    │
├─────────────────────────────────────────────────────────┤
│ → Retention Analyzer                                    │
│ → Competitor Monitor                                    │
│ → Growth Strategist                                     │
└─────────────────────────────────────────────────────────┘
```

### 1.3 Integration Architecture

**Core Systems:**
- **Claude Agent SDK**: Custom agent deployment framework
- **DeadMan Intelligence Bridge**: Offline scraping & deep research integration
- **Fabric Patterns**: 234+ production-ready AI patterns
- **Planning Files**: YouTube Planning Files integration for project management
- **Session Continuity**: 5-minute checkpoint protocol for disconnection recovery

---

## 2. RESEARCH AGENTS

### 2.1 AGENT: Trend Scanner

**Primary Function**: Monitor YouTube, TikTok, Instagram for emerging trends and high-potential topics

**Scope**:
- Platform monitoring (YouTube, TikTok, Instagram, X)
- Trend detection (search volume surges, hashtag velocity)
- **Deep Intelligence Integration** (Recursive LM findings, Archive data)
- Viral mechanic identification (STEPPS framework analysis)
- Opportunity scoring (Search Demand Ratio calculation)

**Input/Output Interface**:
```yaml
INPUT:
  - Niche specification (content pillars from R63)
  - Geographic targeting (US/CA/UK priority per CPM analysis)
  - DeadMan Bridge Reports (Offline/Technical Intel)
  - Update frequency (daily scan recommended)

OUTPUT:
  - trend_report_YYYY_MM_DD.md:
      - Top 10 trending topics in niche
      - Deep Research opportunities (from Bridge)
      - Search volume data (Google Trends, VidIQ)
      - Viral coefficient estimates (K-factor)
      - STEPPS scores (0-30 scale)
      - Recommended action (CREATE/MONITOR/SKIP)
```

**Tool Access Requirements**:
- DeadMan Intelligence Bridge (local script execution)
- VidIQ API (trend analytics)
- Google Trends API (search volume)
- YouTube Data API v3 (video performance)
- TikTok Creative Center (trending sounds, hashtags)
- WebSearch capability (supplementary research)

**Human Approval Gates**:
- **Gate 1**: Topic selection (human approves which trends to pursue)
- **Bypass Criteria**: None - all topics require human approval

**Integration Points**:
- → Keyword Researcher (passes selected trends for SEO analysis)
- → Deep Research Agent (handoff for technical deep dives)
- → Hook Generator (provides trending hooks/angles)
- → Growth Strategist (feeds competitive intelligence)

**Success Metrics**:
- Topic suggestion acceptance rate >40%
- Suggested videos achieving 2x avg channel CTR
- Trend detection lead time >24 hours before saturation

**Error Handling**:
```python
# Trend Scanner error protocols
if bridge_connection_failed:
    log_event("Offline intelligence unavailable")
    proceed_with_live_api_data_only()

if api_rate_limit_exceeded:
    fallback_to_manual_scraping()
    log_event(priority='medium')

if trend_detection_confidence < 70%:
    flag_for_human_review()
    include_raw_data_for_manual_analysis()
```

---

### 2.2 AGENT: Deep Research Agent (NEW)

**Primary Function**: Execute recursive deep dives on complex topics using the Intelligence Bridge

**Scope**:
- **Recursive Language Model (RLM) Operations**: Handling unbounded context (10M+ tokens) via Python REPL
- **Offline Archive Analysis**: Processing Wikipedia, BlackHatWorld, and historical archives (e.g., Stewart Cheifet)
- **Technical Synthesis**: Converting raw scraped data into structured content pillars
- **Trend Validation**: Cross-referencing viral trends with deep technical reality

**Input/Output Interface**:
```yaml
INPUT:
  - Topic/Keyword (from Trend Scanner)
  - Bridge Data Sources (recursive_lm_intel.json, etc.)
  - Depth Level (Surface, Technical, Academic, Underground)

OUTPUT:
  - deep_dive_brief_[TOPIC].md:
      - Historical Context (Timeline/Origins)
      - Technical Mechanics (How it works)
      - Key Figures (Biographical data)
      - Underground/Niche Angles (BlackHatWorld insights)
      - Content Opportunities (Uncovered angles)
```

**Tool Access Requirements**:
- `deadman_intelligence_bridge.py`
- Local `Data/` repository access
- Python REPL environment (for RLM execution)
- NLP Summarization (Claude/Fabric)

**Human Approval Gates**:
- **Gate 1**: Insight Validation (human confirms technical accuracy of synthesized findings)

**Integration Points**:
- ← Trend Scanner (receives broad topics)
- → Fact Checker (provides primary source data)
- → Structure Optimizer (provides dense information blocks)

**Success Metrics**:
- Unique angle discovery: >1 per brief (finding what others missed)
- Technical accuracy: >95% (verified by human expert)
- Data utilization: 100% of relevant bridge data incorporated

---

### 2.3 AGENT: Keyword Researcher

**Primary Function**: SEO and keyword strategy optimization for video discoverability

**Scope**:
- Keyword demand analysis (search volume, competition)
- Search intent classification (informational, tutorial, comparison)
- Related keyword discovery (semantic search, LSI keywords)
- Competitor keyword gap analysis

**Input/Output Interface**:
```yaml
INPUT:
  - Video topic (from Trend Scanner or human)
  - Target geography (US/CA/UK for CPM optimization)
  - Competitive channels (for gap analysis)

OUTPUT:
  - keyword_research_[TOPIC].md:
      - Primary keyword (search volume, difficulty, intent)
      - Secondary keywords (5-10 variants)
      - LSI keywords (semantic relevance)
      - Title/description templates optimized for keywords
      - Tag recommendations (15-20 tags per R64)
```

**Tool Access Requirements**:
- VidIQ (keyword analytics, competition scoring)
- TubeBuddy API (search score, weighted score)
- Ahrefs API (optional - keyword difficulty, SERP analysis)
- Google Keyword Planner (search volume validation)

**Human Approval Gates**:
- **Gate 1**: Keyword selection (human chooses primary keyword from top 3 options)
- **Bypass Criteria**: If Search Demand Ratio >4.0x AND competition score <30/100

**Integration Points**:
- ← Trend Scanner (receives trending topics)
- → Metadata Optimizer (provides optimized keyword sets)
- → Competitor Monitor (feeds competitive keyword data)

**Success Metrics**:
- Keyword recommendations leading to top 10 search ranking: >60%
- Avg views from search traffic: >35% of total views
- Search Demand Ratio of selected keywords: >2.0x

**Error Handling**:
```python
# Keyword Researcher error protocols
if search_volume_data_unavailable:
    use_proxy_metrics(youtube_autocomplete_frequency)
    flag_for_manual_validation()

if competition_too_high (ratio < 1.0):
    suggest_long_tail_alternatives()
    recommend_pivot_angle()

if zero_search_volume:
    classify_as_trending_only()
    recommend_viral_strategy_instead_of_SEO()
```

---

### 2.4 AGENT: Audience Analyst

**Primary Function**: Analyze audience behavior, engagement patterns, and persona development

**Scope**:
- Comment sentiment analysis (pain points, questions, requests)
- Engagement pattern identification (repeat viewers, superfans)
- Persona development (demographics, psychographics, content preferences)
- Retention trigger analysis (what keeps viewers watching)

**Input/Output Interface**:
```yaml
INPUT:
  - Channel ID (DeadManAI channel)
  - Competitor channel IDs (2-5 comparison channels)
  - Analysis period (30/60/90 days)

OUTPUT:
  - audience_analysis_[PERIOD].md:
      - Top 20 audience questions (from comments)
      - Persona profiles (3-5 distinct audience segments)
      - Engagement triggers (topics/formats driving comments)
      - Content gap analysis (what audience wants but doesn't exist)
      - Retention insights (viewer drop-off patterns)
```

**Tool Access Requirements**:
- YouTube Data API v3 (comment extraction, engagement metrics)
- YouTube Analytics API (retention curves, traffic sources)
- NLP sentiment analysis (Claude API for comment processing)
- Demographic data (YouTube Studio exports)

**Human Approval Gates**:
- **Gate 1**: Persona validation (human confirms accuracy of audience profiles)
- **Gate 2**: Content recommendations (human decides which suggestions to prioritize)

**Integration Points**:
- → Structure Optimizer (provides retention insights for script pacing)
- → Growth Strategist (feeds audience growth patterns)
- → Trend Scanner (identifies audience-specific trend preferences)

**Success Metrics**:
- Persona accuracy validation: >85% human agreement
- Content suggestions leading to above-avg retention: >70%
- Audience question coverage in content: >50% of top 20 questions addressed/quarter

**Error Handling**:
```python
# Audience Analyst error protocols
if insufficient_comment_data (< 50 comments):
    fallback_to_competitor_audience_analysis()
    flag_low_engagement_warning()

if demographic_data_missing:
    use_niche_benchmarks()
    note_assumption_in_report()

if retention_curve_anomaly:
    flag_for_manual_investigation()
    check_for_technical_issues(buffering, ads)
```

---

## 3. SCRIPTWRITING AGENTS

### 3.1 AGENT: Hook Generator

**Primary Function**: Generate viral hooks optimized for CTR and first-15-second retention

**Scope**:
- Hook template application (6 viral formulas from R64)
- Curiosity gap engineering (information gap theory)
- Pattern recognition (analyze top-performing hooks in niche)
- A/B testing recommendations (2-3 hook variants per video)

**Input/Output Interface**:
```yaml
INPUT:
  - Video topic
  - Target emotion (awe, excitement, curiosity per STEPPS)
  - Script outline (optional context)

OUTPUT:
  - hooks_[TOPIC].md:
      - 3-5 hook variants (0-15 second scripts)
      - Hook strength scores (0-25 rubric from R64)
      - Predicted CTR range (based on pattern analysis)
      - Thumbnail pairing recommendations
      - A/B testing strategy
```

**Hook Formulas (R64 Framework)**:
```
FORMULA 1: STAT SHOCK
"[Surprising statistic] + [Common belief challenged] + [Promise of explanation]"
Example: "87% of YouTubers fail within 6 months - but this one trick..."

FORMULA 2: FORBIDDEN KNOWLEDGE
"[Authority figure] doesn't want you to know + [Exclusive insight]"
Example: "YouTube doesn't tell you this about the algorithm..."

FORMULA 3: TRANSFORMATION PROMISE
"How I went from [undesirable state] to [desirable state] in [timeframe]"
Example: "0 to 100K subscribers in 90 days using this framework..."

FORMULA 4: CONTRARIAN TAKE
"Everything you know about [X] is wrong + [Bold claim]"
Example: "Stop doing keyword research - here's what actually works..."

FORMULA 5: URGENCY/SCARCITY
"[Time-sensitive opportunity] + [Consequence of missing out]"
Example: "This YouTube strategy works NOW - but won't in 30 days..."

FORMULA 6: STORY HOOK
"[Relatable struggle] + [Unexpected twist] + [Promise of resolution]"
Example: "I was about to quit YouTube when I discovered..."
```

**Tool Access Requirements**:
- Claude API (hook generation, variant creation)
- Pattern library (top-performing hooks from niche)
- Sentiment analysis (emotion scoring)
- Historical performance data (CTR benchmarks)

**Human Approval Gates**:
- **Gate 1**: Hook selection (human chooses 1-2 hooks from 5 variants)
- **Gate 2**: Brand voice alignment (human validates tone matches channel)

**Integration Points**:
- ← Trend Scanner (receives trending angles)
- → Structure Optimizer (hook feeds into script opening)
- → Thumbnail A/B Tester (hook-thumbnail pairing optimization)

**Success Metrics**:
- Generated hooks achieving >5% CTR: >60% of videos
- Hook strength scores matching actual CTR (correlation >0.7)
- First-15-second retention >70%

**Error Handling**:
```python
# Hook Generator error protocols
if all_hooks_score_below_threshold (< 15/25):
    request_topic_pivot()
    suggest_alternative_angles()

if hook_too_long (> 20 seconds):
    auto_compress()
    flag_pacing_issue()

if brand_voice_mismatch_detected:
    regenerate_with_style_guide()
    escalate_to_human_review()
```

---

### 3.2 AGENT: Structure Optimizer

**Primary Function**: Optimize script structure for retention, pacing, and engagement

**Scope**:
- Retention curve prediction (5 critical zones from R64)
- Pacing optimization (concept density: 1.5/min target)
- Pattern interrupt placement (every 60-90 seconds)
- Tension-release cycle design (3-5 cycles per video)

**Input/Output Interface**:
```yaml
INPUT:
  - Script draft (from human or AI generation)
  - Target video length (6-12 min typical)
  - Retention benchmarks (channel avg or niche avg)

OUTPUT:
  - structure_analysis_[SCRIPT].md:
      - Retention curve prediction (5 zones scored)
      - Pacing analysis (concepts/min, variance)
      - Pattern interrupt recommendations (timing, type)
      - Structural issues (low-density sections, pacing drops)
      - Optimized script outline (reordered beats)
```

**Retention Zone Analysis**:
```
ZONE 1: HOOK WINDOW (0-15s)
├─ Target Retention: 75-85%
├─ Mechanism: Immediate value signal
├─ Check: Is payoff delivered within 15 seconds?
└─ Action: If no → compress opening, front-load value

ZONE 2: FIRST HALF (0-50%)
├─ Target Retention: 65-75%
├─ Mechanism: Structure quality
├─ Check: Is each beat building on previous?
└─ Action: Remove tangents, tighten transitions

ZONE 3: MID-VIDEO VALLEY (35-65%)
├─ Target Retention: 55-65% (natural drop)
├─ Mechanism: Pattern interrupts
├─ Check: Is there a narrative pivot or reveal?
└─ Action: Add visual shift, story turn, or controversy

ZONE 4: CLIMAX ZONE (75-95%)
├─ Target Retention: 60-70%
├─ Mechanism: Emotional payoff
├─ Check: Does video build to peak insight?
└─ Action: Ensure biggest revelation comes here

ZONE 5: OUTRO (95-100%)
├─ Target Retention: 40-50%
├─ Mechanism: CTA and end screen
├─ Check: Is CTA clear and compelling?
└─ Action: Reinforce value, tease next video
```

**Tool Access Requirements**:
- Claude API (script analysis, restructuring)
- Retention prediction model (trained on channel + niche data)
- NLP pacing analyzer (concept density calculation)
- Pattern interrupt library (visual, narrative, audio, pacing)

**Human Approval Gates**:
- **Gate 1**: Structure changes (human approves reordering of major beats)
- **Bypass Criteria**: If predicted retention improvement >15% AND no narrative breaks

**Integration Points**:
- ← Hook Generator (receives optimized hook)
- ← Audience Analyst (receives retention insights)
- → Fact Checker (passes structured script for verification)
- → B-roll Curator (provides timing for visual elements)

**Success Metrics**:
- Predicted retention curves matching actual: ±10% accuracy
- Videos following optimized structure achieving >45% AVD
- Pattern interrupt effectiveness: +12-18% retention at placement points

**Error Handling**:
```python
# Structure Optimizer error protocols
if pacing_variance_too_high (> 1.0 concepts/min swing):
    flag_inconsistent_information_density()
    suggest_smoothing_techniques()

if no_natural_climax_detected:
    recommend_narrative_restructuring()
    escalate_to_human_creative_input()

if predicted_retention < 35%:
    recommend_topic_abandonment()
    suggest_alternative_angle_or_format()
```

---

### 3.3 AGENT: Fact Checker

**Primary Function**: Automated fact verification and citation sourcing

**Scope**:
- Claim extraction (identify factual assertions in script)
- Automated verification (Originality.ai, Perplexity cross-reference)
- Source compilation (primary sources, data tables, studies)
- Citation formatting (inline citations, source list generation)

**Input/Output Interface**:
```yaml
INPUT:
  - Script (final draft with factual claims)
  - Claim sensitivity (high/medium/low - determines verification depth)

OUTPUT:
  - fact_check_report_[SCRIPT].md:
      - Verified claims (GREEN - high confidence)
      - Flagged claims (YELLOW - conflicting sources)
      - Rejected claims (RED - incorrect/unverifiable)
      - Source list (formatted citations)
      - Citation coverage score (target: >95%)
      - Recommended script edits (for flagged/rejected claims)
```

**Verification Process**:
```
STEP 1: CLAIM EXTRACTION
├─ NLP parsing (identify factual assertions)
├─ Claim categorization (stat, historical, technical, opinion)
└─ Priority scoring (high-risk claims verified first)

STEP 2: AUTOMATED VERIFICATION
├─ Originality.ai fact-check (86.69% accuracy baseline)
├─ Perplexity cross-reference (3+ independent sources)
├─ Data table validation (check original studies)
└─ Confidence scoring (0-100%)

STEP 3: HUMAN REVIEW (for flagged claims)
├─ Present conflicting sources
├─ Recommendation (keep/modify/remove)
└─ Human decision logged

STEP 4: CITATION COMPILATION
├─ Format primary sources (author, date, publication)
├─ Include URLs/DOIs
├─ Generate inline citation markers
└─ Create source list for description
```

**Tool Access Requirements**:
- Originality.ai API (fact-checking)
- Perplexity API (source cross-referencing)
- Claude API (claim extraction, NLP parsing)
- Citation formatting library (APA/MLA/Chicago)

**Human Approval Gates**:
- **Gate 1**: Flagged claim resolution (human reviews YELLOW/RED claims)
- **Gate 2**: Source credibility (human validates source quality for high-stakes claims)

**Integration Points**:
- ← Structure Optimizer (receives structured script)
- → Metadata Optimizer (provides citation list for description)
- → QC Inspector (fact integrity verification)

**Success Metrics**:
- Citation coverage: >95% of claims sourced
- Fact-check accuracy: >90% alignment with post-publish verification
- Claim rejection rate reducing over time (AI learning from human decisions)

**Error Handling**:
```python
# Fact Checker error protocols
if claim_verification_confidence < 70%:
    escalate_to_human_review()
    provide_all_source_data()

if conflicting_sources_detected:
    present_source_credibility_comparison()
    recommend_claim_modification_or_removal()

if citation_coverage < 80%:
    flag_as_high_risk()
    require_human_editorial_review_before_production()
```

---

## 4. PRODUCTION AGENTS

### 4.1 AGENT: B-roll Curator

**Primary Function**: Source, select, and organize B-roll footage matching script timing and emotional beats

**Scope**:
- Stock footage search (Pexels, Pixabay, Storyblocks)
- AI video generation (Runway, Pika for custom clips)
- Scene matching (visual alignment with script narrative)
- Timing coordination (B-roll placement per retention curve)

**Input/Output Interface**:
```yaml
INPUT:
  - Finalized script with timing (WPM-based duration)
  - Visual cue annotations (scene descriptions)
  - Emotional beats (tension, release, climax)

OUTPUT:
  - broll_package_[VIDEO]/
      - footage_list.md (sources, licenses, timing)
      - assets/ (downloaded clips organized by scene)
      - davinci_resolve_import.xml (timeline markers)
      - visual_script.md (scene-by-scene visual plan)
```

**B-roll Selection Criteria**:
```
RELEVANCE (40%):
├─ Direct visual match (if discussing "editing", show editing)
├─ Metaphorical alignment (if discussing "growth", show nature timelapse)
└─ Avoidance of cliché stock footage (overused clips)

EMOTIONAL ALIGNMENT (30%):
├─ Color palette matching mood (warm/cool, saturated/muted)
├─ Movement matching energy (slow pans = calm, quick cuts = excitement)
└─ Lighting matching tone (bright = optimistic, dark = serious)

TECHNICAL QUALITY (20%):
├─ Resolution (1080p minimum, 4K preferred)
├─ Frame rate (24/30/60fps matching project settings)
├─ Color grading compatibility (flat profiles preferred)

LICENSING (10%):
├─ Commercial use allowed
├─ Attribution requirements noted
└─ License type logged (CC0, Pexels License, Storyblocks)
```

**Tool Access Requirements**:
- Pexels API (free stock footage)
- Pixabay API (free stock footage)
- Storyblocks API (premium stock footage, $45/mo tier)
- Runway/Pika API (AI video generation for custom clips)
- DaVinci Resolve scripting (timeline XML generation)

**Human Approval Gates**:
- **Gate 1**: Visual style approval (human confirms aesthetic matches brand)
- **Gate 2**: Final clip selection (human reviews curated package before download)

**Integration Points**:
- ← Structure Optimizer (receives script timing and emotional beats)
- → QC Inspector (visual consistency verification)
- → Multi-Platform Distributor (aspect ratio variants for TikTok/Instagram)

**Success Metrics**:
- B-roll relevance score (human rating >8/10): >80% of clips
- Licensing compliance: 100% (zero copyright strikes)
- Scene coverage: >85% of script has matching B-roll

**Error Handling**:
```python
# B-roll Curator error protocols
if no_suitable_footage_found:
    generate_ai_video_clip()
    flag_for_custom_footage_consideration()

if licensing_unclear:
    exclude_clip()
    escalate_for_manual_license_verification()

if aesthetic_mismatch_detected (color, mood):
    suggest_color_grading_adjustments()
    provide_alternative_clips()
```

---

### 4.2 AGENT: Music Selector

**Primary Function**: Select background music and sound effects matching video mood and platform requirements

**Scope**:
- Mood mapping (emotional beats → music characteristics)
- Licensing verification (copyright-safe music only)
- Audio ducking recommendations (voice clarity preservation)
- Platform compliance (TikTok trending sounds, YouTube Content ID)

**Input/Output Interface**:
```yaml
INPUT:
  - Script emotional arc (tension/release cycles)
  - Video duration (for music loop matching)
  - Platform targets (YouTube, TikTok, Instagram)

OUTPUT:
  - music_package_[VIDEO]/
      - music_selection.md (tracks, timing, reasoning)
      - assets/ (downloaded music files)
      - davinci_resolve_audio_markers.xml (ducking points)
      - licensing_proof/ (license certificates)
```

**Mood Mapping Framework**:
```
EMOTIONAL ARC → MUSIC CHARACTERISTICS

CURIOSITY/INTRIGUE:
├─ Tempo: 80-110 BPM (moderate)
├─ Instrumentation: Minimal (piano, strings, synth pads)
├─ Dynamics: Gradual build
└─ Examples: "Thoughtful Piano", "Mystery Ambient"

EXCITEMENT/AWE:
├─ Tempo: 120-140 BPM (upbeat)
├─ Instrumentation: Full (drums, bass, melodic leads)
├─ Dynamics: High energy, driving
└─ Examples: "Epic Motivation", "Uplifting Corporate"

CALM/EDUCATIONAL:
├─ Tempo: 60-90 BPM (slow to moderate)
├─ Instrumentation: Acoustic (guitar, light percussion)
├─ Dynamics: Consistent, non-intrusive
└─ Examples: "Soft Background", "Calm Tutorial"

TENSION/DRAMA:
├─ Tempo: Variable (accelerando for build)
├─ Instrumentation: Strings, bass, percussion
├─ Dynamics: Crescendo from quiet to loud
└─ Examples: "Cinematic Tension", "Dark Suspense"
```

**Licensing Sources**:
| Source | Cost | Tracks | Best For |
|--------|------|--------|----------|
| Epidemic Sound | $15/mo | 40K+ | YouTube (whitelisting) |
| Artlist | $15/mo | 20K+ | All platforms |
| YouTube Audio Library | Free | 1K+ | Budget tier |
| Uppbeat | Free | 500+ | Small channels |

**Tool Access Requirements**:
- Epidemic Sound API / Artlist API (music search)
- Audio analysis library (BPM detection, mood classification)
- YouTube Content ID checker (copyright strike prevention)
- TikTok trending sounds API (viral audio integration)

**Human Approval Gates**:
- **Gate 1**: Music selection (human approves 2-3 finalists, chooses 1)
- **Bypass Criteria**: If reusing music from brand library (established safe tracks)

**Integration Points**:
- ← Structure Optimizer (receives emotional arc, timing)
- → QC Inspector (audio level verification, ducking effectiveness)
- → Multi-Platform Distributor (TikTok trending sound variants)

**Success Metrics**:
- Licensing compliance: 100% (zero Content ID claims)
- Music-mood alignment (human rating >8/10): >85%
- Audio ducking effectiveness (voice clarity maintained): >95% clarity score

**Error Handling**:
```python
# Music Selector error protocols
if content_id_match_detected:
    exclude_track()
    escalate_for_manual_license_verification()

if music_duration_mismatch (video 8min, track 3min):
    create_looping_strategy()
    suggest_extended_version_or_alternative()

if mood_mismatch_detected:
    re_query_with_refined_parameters()
    provide_3_alternative_suggestions()
```

---

### 4.3 AGENT: QC Inspector

**Primary Function**: Quality control verification before publishing (audio, visual, caption, brand consistency)

**Scope**:
- Audio level verification (LUFS -14 to -16 per R64)
- Visual consistency (color grading, resolution, aspect ratio)
- Caption accuracy (subtitle timing, spelling, readability)
- Brand compliance (intro/outro, watermarks, CTAs)

**Input/Output Interface**:
```yaml
INPUT:
  - Final export video file (MP4)
  - Production checklist (from workflow architecture)

OUTPUT:
  - qc_report_[VIDEO].md:
      - PASS/FAIL per category (audio, visual, captions, brand)
      - Issues detected (timestamped, severity scored)
      - Recommended fixes (specific corrections needed)
      - Approval status (APPROVED / REVISION REQUIRED)
```

**QC Checklist (Per NPR 8735.2C Standards)**:
```
AUDIO QC (25%):
□ LUFS level: -14 to -16 (YouTube standard)
□ Peak levels: < -1 dB (no clipping)
□ Dialogue clarity: Intelligible without captions
□ Music ducking: -6 to -12 dB during speech
□ No audio pops, clicks, or distortion
□ Consistent volume throughout video

VISUAL QC (25%):
□ Resolution: 1920×1080 minimum
□ Frame rate: 24/30fps consistent
□ No visual artifacts (compression, banding)
□ Color grading: Matches house style
□ B-roll transitions smooth (no jarring cuts)
□ Text overlays readable (contrast 4.5:1)

CAPTION QC (20%):
□ Subtitle timing: ±0.5s accuracy
□ Spelling/grammar: Zero errors
□ Readability: <60 characters per line
□ Positioning: Bottom 20% of frame
□ Speaker identification (if multi-voice)
□ No profanity/sensitive content uncensored

BRAND QC (20%):
□ Intro: Branded intro (0-5s) present
□ Outro: CTA + end screen (final 20s)
□ Watermark: Channel logo (bottom right)
□ Visual style: Matches brand guidelines
□ Tone consistency: Matches channel voice

TECHNICAL QC (10%):
□ File format: H.264, MP4 container
□ Codec: YouTube recommended settings
□ Bitrate: 8-12 Mbps for 1080p
□ Metadata: Title, description embedded
□ Aspect ratio: 16:9 (YouTube) or variants (TikTok 9:16)
```

**Tool Access Requirements**:
- FFmpeg (audio level analysis, metadata extraction)
- DaVinci Resolve API (color grading verification)
- Subtitle validation library (timing, spelling, readability)
- Brand asset library (intro/outro templates for comparison)

**Human Approval Gates**:
- **Gate 1**: FAIL status (human reviews all failed QC items, decides fix or override)
- **Bypass Criteria**: None - all QC failures require human review

**Integration Points**:
- ← B-roll Curator (visual asset verification)
- ← Music Selector (audio level verification)
- → Publishing Agents (approval required before metadata optimization)

**Success Metrics**:
- QC pass rate (first submission): >80%
- Issue detection accuracy: >95% (vs human post-review)
- Time to QC completion: <15 minutes per video

**Error Handling**:
```python
# QC Inspector error protocols
if audio_level_out_of_spec:
    flag_severity(CRITICAL if > 2dB deviation, MINOR if < 0.5dB)
    recommend_audio_normalization()

if caption_timing_error_detected:
    suggest_auto_retime()
    flag_for_manual_verification_if_complex_dialogue()

if brand_element_missing (intro/outro):
    flag_as_CRITICAL()
    halt_publishing_workflow()
```

---

## 5. PUBLISHING AGENTS

### 5.1 AGENT: Metadata Optimizer

**Primary Function**: Generate optimized titles, descriptions, and tags for maximum discoverability

**Scope**:
- Title engineering (Hook + Specificity + Curiosity formula)
- Description optimization (first 2 lines, keyword density, CTAs)
- Tag strategy (15-20 tags, brand tag first, LSI keywords)
- Multi-platform adaptation (YouTube, TikTok, Instagram variants)

**Input/Output Interface**:
```yaml
INPUT:
  - Video content summary
  - Keyword research (from Keyword Researcher agent)
  - Platform targets (YouTube primary, TikTok/Instagram secondary)

OUTPUT:
  - metadata_package_[VIDEO]/
      - youtube_metadata.md (title, description, tags)
      - tiktok_metadata.md (caption, hashtags)
      - instagram_metadata.md (caption, hashtags)
      - pinterest_metadata.md (title, description)
      - metadata_performance_predictions.md (CTR estimate, search rank estimate)
```

**Title Engineering Formula**:
```
TITLE = [HOOK] + [SPECIFICITY] + [CURIOSITY]

HOOK (30% weight):
├─ Number ("7 Ways", "Top 10")
├─ Power word ("Secret", "Ultimate", "Proven")
├─ Timeframe ("in 30 Days", "2025 Update")

SPECIFICITY (40% weight):
├─ Exact topic ("YouTube SEO", not "Video Marketing")
├─ Audience target ("for Beginners", "Advanced Guide")
├─ Use case ("for Small Channels", "to Get 100K Subs")

CURIOSITY (30% weight):
├─ Open loop ("...But Here's the Catch")
├─ Controversy ("Why Everyone's Wrong About X")
├─ Mystery ("The Hidden Truth About X")

LENGTH: 60-70 characters (mobile truncation point)
```

**Description Template**:
```markdown
[LINE 1-2: Value proposition + Primary keyword]
This video reveals [specific benefit] using [method/framework].

[PARAGRAPH 1: Expand on value]
You'll learn [specific takeaway 1], [takeaway 2], and [takeaway 3].

[TIMESTAMPS - Critical for retention]
0:00 - Introduction
0:45 - [Section 1 title]
2:15 - [Section 2 title]
...

[CTA]
🔔 Subscribe for [specific value]: [channel URL]

[RESOURCES]
🔗 [Tool mentioned]: [affiliate link]
📄 Free template: [lead magnet]

[SOURCES - Fact Checker integration]
[1] [Citation]
[2] [Citation]

[HASHTAGS - Secondary discovery]
#Keyword1 #Keyword2 #Keyword3

[LEGAL]
Affiliate disclosure, sponsor mention (if applicable)
```

**Tag Strategy (Per R64)**:
```
TAG ORDER (15-20 tags total):

POSITION 1: Brand tag
"DeadManAI" or "TheUnseen"

POSITIONS 2-5: Exact keyword variations
"youtube seo 2026"
"youtube seo tips"
"youtube seo for beginners"
"youtube seo strategy"

POSITIONS 6-10: LSI (Latent Semantic Indexing) keywords
"video optimization"
"youtube algorithm"
"get more views on youtube"
"youtube growth"

POSITIONS 11-15: Broad topic tags
"youtube tips"
"content creation"
"faceless youtube"

POSITIONS 16-20: Competitor/trending tags (optional)
"mr beast seo"
"viral video formula"
```

**Tool Access Requirements**:
- VidIQ API (tag suggestions, search score)
- TubeBuddy API (weighted score, competition analysis)
- Claude API (title/description generation)
- Keyword library (from Keyword Researcher agent)

**Human Approval Gates**:
- **Gate 1**: Title selection (human chooses from 3-5 variants)
- **Gate 2**: Description review (human validates CTAs, links, tone)

**Integration Points**:
- ← Keyword Researcher (receives optimized keyword sets)
- ← Fact Checker (receives citation list for description)
- → Thumbnail A/B Tester (title-thumbnail pairing optimization)
- → Multi-Platform Distributor (metadata variants per platform)

**Success Metrics**:
- Suggested titles achieving >5% CTR: >70%
- Search ranking in top 10 for primary keyword: >60%
- Tag coverage (video appearing in recommended for tagged terms): >80%

**Error Handling**:
```python
# Metadata Optimizer error protocols
if title_too_long (> 70 characters):
    auto_compress()
    maintain_hook_specificity_curiosity_balance()

if keyword_density_too_high (> 3% in description):
    flag_as_spam_risk()
    recommend_natural_language_rewording()

if tag_competition_too_high (all tags > 80/100 difficulty):
    suggest_long_tail_alternatives()
    recommend_niche_down_strategy()
```

---

### 5.2 AGENT: Thumbnail A/B Tester

**Primary Function**: Generate thumbnail variations and recommend A/B testing strategy

**Scope**:
- Thumbnail design generation (3-5 variants per video)
- A/B testing strategy (testing schedule, metrics tracking)
- Performance prediction (CTR estimate based on design elements)
- Iteration recommendations (design improvements based on test results)

**Input/Output Interface**:
```yaml
INPUT:
  - Video topic and title
  - Hook emotional tone (curiosity, excitement, controversy)
  - Brand style guide (colors, fonts, composition rules)

OUTPUT:
  - thumbnail_package_[VIDEO]/
      - variant_A.png (1280×720, design 1)
      - variant_B.png (1280×720, design 2)
      - variant_C.png (optional, design 3)
      - ab_testing_strategy.md (testing schedule, swap timing)
      - design_rationale.md (why each variant, predicted performance)
      - performance_tracking_template.md (metrics to monitor)
```

**Thumbnail Design Principles (R64)**:
```
VISUAL HIERARCHY (40%):
├─ Focal point: Face or key object (rule of thirds)
├─ Contrast: 4.5:1 minimum (WCAG AA)
├─ Size: Large enough for mobile (3-5 major elements max)
└─ Depth: Foreground/background separation (blur, color)

TEXT OVERLAY (30%):
├─ Max 3-5 words (readable at small size)
├─ Font: Bold, sans-serif (Impact, Montserrat)
├─ Outline: 2-3px contrasting color
├─ Placement: Top third or bottom third (avoid center)

EMOTION (20%):
├─ Facial expression: Exaggerated (surprise, excitement)
├─ Color psychology: Red/yellow (urgency), blue/green (trust)
├─ Action: Movement, pointing, gesture
└─ Eyes: Direct gaze at camera (engagement)

BRAND CONSISTENCY (10%):
├─ Color palette: 2-3 brand colors
├─ Logo: Small watermark (bottom right)
├─ Style: Matches channel aesthetic
└─ Template: Reusable framework for series
```

**A/B Testing Strategy**:
```
TEST SCHEDULE:

HOUR 1-24: Variant A (baseline)
├─ Monitor: CTR, impressions, views
├─ Benchmark: CTR at 24h mark
└─ Decision threshold: If CTR < 3%, proceed to swap

HOUR 24-48: Variant B (challenger)
├─ Monitor: CTR delta vs Variant A
├─ Statistical significance: >100 impressions
└─ Winner: Higher CTR by ≥0.5 percentage points

HOUR 48+: Winning variant (permanent)
├─ Document: Performance data
├─ Learn: Design elements that worked
└─ Iterate: Apply learnings to future thumbnails

CONFIDENCE REQUIREMENTS:
- Minimum 200 impressions per variant
- CTR difference ≥0.5 percentage points
- Test duration ≥24 hours
```

**Tool Access Requirements**:
- Canva Pro API (thumbnail generation)
- Photoshop API / Photopea (advanced editing)
- YouTube Data API (thumbnail upload, CTR tracking)
- Image analysis library (contrast checking, text readability)

**Human Approval Gates**:
- **Gate 1**: Design approval (human selects 2-3 variants from 5 options for testing)
- **Gate 2**: Winner confirmation (human reviews test results, approves final thumbnail)

**Integration Points**:
- ← Hook Generator (receives hook for text overlay)
- ← Metadata Optimizer (title-thumbnail pairing optimization)
- → Analytics Agents (CTR performance tracking)

**Success Metrics**:
- Thumbnail CTR (channel avg or better): >70% of videos
- A/B test winner improvement over baseline: >10% CTR increase
- Design consistency (brand recognition): >85% human validation

**Error Handling**:
```python
# Thumbnail A/B Tester error protocols
if contrast_too_low (< 3:1):
    flag_readability_issue()
    auto_adjust_text_outline_thickness()

if text_overlay_too_long (> 6 words):
    recommend_compression()
    suggest_visual_substitution_for_words()

if ab_test_inconclusive (CTR difference < 0.3%):
    extend_test_duration()
    consider_third_variant()
```

---

### 5.3 AGENT: Multi-Platform Distributor

**Primary Function**: Adapt and distribute content across YouTube, TikTok, Instagram, X, Facebook

**Scope**:
- Content repurposing (16:9 → 9:16, long-form → short-form)
- Platform-specific optimization (caption styles, hashtag strategies)
- Upload scheduling (optimal posting times per platform)
- Cross-promotion coordination (YouTube → TikTok funnel)

**Input/Output Interface**:
```yaml
INPUT:
  - Master video file (YouTube 16:9 long-form)
  - Script and metadata (from prior agents)
  - Platform targets (YouTube + 2-3 secondary platforms)

OUTPUT:
  - distribution_package_[VIDEO]/
      - youtube/ (1920×1080, full video, metadata)
      - tiktok/ (1080×1920, 60s clips, captions)
      - instagram/ (1080×1920, 90s reels, hashtags)
      - twitter/ (1280×720, 2min clips, thread copy)
      - facebook/ (1920×1080, full video, caption)
      - distribution_schedule.md (posting times, cross-promo strategy)
```

**Platform-Specific Adaptations**:
```
PRIMARY: YouTube (Long-Form 16:9)
├─ Format: 1920×1080, 6-12 minutes
├─ Optimization: SEO-driven metadata, timestamps, description links
├─ Goal: Evergreen discovery, monetization ($5-20 CPM)
├─ Success Metric: CTR >5%, AVD >40%, sub conversion >1%

SECONDARY: TikTok (Short-Form 9:16)
├─ Format: 1080×1920, 15-60 seconds
├─ Adaptation: Extract hook + climax, increase cut frequency (30-40/min)
├─ Optimization: Trending sounds, hashtags (#fyp, niche tags)
├─ Goal: Viral discovery, funnel to YouTube
├─ Success Metric: Views >10K, CTR to YouTube bio >2%

SECONDARY: Instagram Reels (Short-Form 9:16)
├─ Format: 1080×1920, 30-90 seconds
├─ Adaptation: Similar to TikTok, larger text overlays
├─ Optimization: Hashtags (15-30), location tags, audio trends
├─ Goal: Viral discovery, brand awareness
├─ Success Metric: Reach >5K, profile visits >3%

TERTIARY: X/Twitter (Clips + Threads)
├─ Format: 1280×720, 30-120 seconds (video limit)
├─ Adaptation: Key insight clips, controversial takes
├─ Optimization: Thread structure (hook → insights → CTA)
├─ Goal: Thought leadership, cross-promotion
├─ Success Metric: Impressions >10K, link clicks >1%

TERTIARY: Facebook (Long-Form + UGC Licensing)
├─ Format: 1920×1080, full video OR viral clips for UGC licensing
├─ Adaptation: Native upload (better reach than YouTube links)
├─ Optimization: Engaging first 3 seconds (auto-play feed)
├─ Goal: Older demographic reach, UGC license revenue
├─ Success Metric: 3-sec views >5K, shares >100
```

**Upload Scheduling (Per Platform Analytics)**:
```
YOUTUBE (Evergreen Focus):
├─ Best: Weekdays 2-4 PM EST (US after-work)
├─ Good: Weekends 10 AM - 12 PM EST
└─ Avoid: Late night (low initial engagement)

TIKTOK (Peak Activity):
├─ Best: 6-10 PM EST (evening scroll), 7-9 AM EST (morning commute)
├─ Good: 12-1 PM EST (lunch break)
└─ Strategy: Post 1-2x daily, stagger 12 hours apart

INSTAGRAM REELS:
├─ Best: 11 AM - 1 PM EST, 7-9 PM EST
├─ Good: Weekends 10 AM - 12 PM
└─ Strategy: Post 1x daily, consistent timing

X/TWITTER:
├─ Best: 8-10 AM EST (morning routine), 12-1 PM EST (lunch), 5-6 PM EST (commute)
├─ Strategy: Thread on Monday, clips throughout week
└─ Frequency: 3-5x weekly
```

**Tool Access Requirements**:
- FFmpeg (video format conversion, aspect ratio cropping)
- YouTube Data API (upload, scheduling)
- TikTok API (upload, analytics)
- Instagram Graph API (upload, insights)
- Twitter API v2 (media upload, thread posting)
- Facebook Graph API (upload, post scheduling)

**Human Approval Gates**:
- **Gate 1**: Platform selection (human decides which platforms for this video)
- **Gate 2**: Short-form clip selection (human approves which 60s segment for TikTok)

**Integration Points**:
- ← Metadata Optimizer (receives platform-specific metadata)
- ← QC Inspector (receives approved master video)
- → Analytics Agents (performance tracking across platforms)

**Success Metrics**:
- Multi-platform reach (total impressions across platforms): >50K per video
- Cross-platform funnel (TikTok/Instagram → YouTube subscribers): >2% conversion
- Platform-specific targets achieved: >80% of videos

**Error Handling**:
```python
# Multi-Platform Distributor error protocols
if aspect_ratio_conversion_error:
    use_smart_crop (face detection, focal point preservation)
    flag_for_manual_review_if_critical_content_at_edges()

if upload_api_error:
    retry_with_exponential_backoff()
    escalate_if_3_consecutive_failures()

if cross_promotion_link_broken:
    flag_as_critical()
    halt_publishing_until_corrected()
```

---

## 6. ANALYTICS AGENTS

### 6.1 AGENT: Retention Analyzer

**Primary Function**: Analyze retention curves, identify drop-off points, suggest improvements

**Scope**:
- Retention curve analysis (5 critical zones per R64)
- Drop-off point identification (timestamp, cause hypothesis)
- Pattern recognition (common failure modes across videos)
- Improvement recommendations (specific edits, structural changes)

**Input/Output Interface**:
```yaml
INPUT:
  - Published video URL (YouTube)
  - Retention curve data (from YouTube Analytics API)
  - Script and structure (for correlation analysis)

OUTPUT:
  - retention_analysis_[VIDEO].md:
      - Retention curve visualization (5 zones scored)
      - Drop-off points (timestamps, severity, hypothesized causes)
      - Pattern correlations (script elements → retention impact)
      - Improvement recommendations (prioritized by impact)
      - Comparison to channel/niche benchmarks
```

**Retention Analysis Framework**:
```
ZONE SCORING (0-100):

ZONE 1: HOOK WINDOW (0-15s)
├─ Target: 75-85% retention
├─ Actual: [X%]
├─ Score: (Actual / Target) × 100
├─ Drop-off causes:
│   ├─ Slow payoff (value signal delayed >15s)
│   ├─ Weak hook (curiosity gap insufficient)
│   └─ Bait-and-switch (thumbnail/title mismatch)
└─ Recommendations: [Specific fixes]

ZONE 2: FIRST HALF (0-50%)
├─ Target: 65-75% retention
├─ Actual: [X%]
├─ Score: (Actual / Target) × 100
├─ Drop-off causes:
│   ├─ Poor structure (illogical progression)
│   ├─ Low information density (<1 concept/min)
│   └─ Pacing issues (too slow/fast)
└─ Recommendations: [Specific fixes]

ZONE 3: MID-VIDEO VALLEY (35-65%)
├─ Target: 55-65% retention (natural drop)
├─ Actual: [X%]
├─ Score: (Actual / Target) × 100
├─ Drop-off causes:
│   ├─ Missing pattern interrupt
│   ├─ Narrative sag (no new information)
│   └─ Cognitive overload (too dense)
└─ Recommendations: [Specific fixes]

ZONE 4: CLIMAX ZONE (75-95%)
├─ Target: 60-70% retention
├─ Actual: [X%]
├─ Score: (Actual / Target) × 100
├─ Drop-off causes:
│   ├─ Weak climax (payoff insufficient)
│   ├─ Premature resolution (peak too early)
│   └─ Overstay (video too long)
└─ Recommendations: [Specific fixes]

ZONE 5: OUTRO (95-100%)
├─ Target: 40-50% retention
├─ Actual: [X%]
├─ Score: (Actual / Target) × 100
├─ Drop-off causes:
│   ├─ Weak CTA (not compelling)
│   ├─ Missing end screen setup
│   └─ Outro too long (>20s)
└─ Recommendations: [Specific fixes]
```

**Pattern Recognition (Across Channel)**:
```
COMMON FAILURE MODES:

PATTERN: "The Slow Hook"
├─ Signature: >30% drop in first 30 seconds
├─ Cause: Value signal delayed beyond 15 seconds
├─ Fix: Front-load key insight, compress opening
├─ Frequency: [X% of videos]

PATTERN: "The Mid-Video Sag"
├─ Signature: Sharp drop at 40-50% mark
├─ Cause: Missing pattern interrupt, narrative lull
├─ Fix: Add visual shift, story pivot, or data reveal
├─ Frequency: [X% of videos]

PATTERN: "The Premature Peak"
├─ Signature: Retention peaks at 60%, drops after
├─ Cause: Biggest revelation too early
├─ Fix: Reorder beats, save best insight for 75-85%
├─ Frequency: [X% of videos]

PATTERN: "The Overstay"
├─ Signature: Gradual decline after 80%
├─ Cause: Video 1-2 minutes too long
├─ Fix: Tighten conclusion, move CTA earlier
├─ Frequency: [X% of videos]
```

**Tool Access Requirements**:
- YouTube Analytics API (retention curve data)
- Data visualization library (retention curve graphs)
- NLP script analysis (correlate script elements with retention)
- Channel benchmark database (historical retention curves)

**Human Approval Gates**:
- **Gate 1**: Improvement recommendations (human decides which fixes to implement)
- **Bypass Criteria**: None - all recommendations require human creative decision

**Integration Points**:
- → Structure Optimizer (retention insights feed into future scripts)
- → Growth Strategist (retention trends inform content strategy)
- ← QC Inspector (pre-publish retention prediction validation)

**Success Metrics**:
- Retention prediction accuracy (predicted vs actual): ±10%
- Improvement recommendation effectiveness: >60% of implemented fixes increase retention
- Pattern detection accuracy: >80% human validation

**Error Handling**:
```python
# Retention Analyzer error protocols
if retention_data_unavailable (< 100 views):
    wait_for_minimum_sample_size()
    flag_low_view_count_warning()

if anomalous_retention_curve (unusual spikes/drops):
    investigate_external_factors(ads, buffering, technical issues)
    flag_for_manual_investigation()

if all_zones_below_target:
    recommend_comprehensive_restructuring()
    suggest_topic_or_format_pivot()
```

---

### 6.2 AGENT: Competitor Monitor

**Primary Function**: Track competitor channels, identify successful strategies, detect market shifts

**Scope**:
- Competitor video tracking (new uploads, performance)
- Strategy analysis (what's working for competitors)
- Content gap identification (untapped topics in niche)
- Market trend detection (audience preference shifts)

**Input/Output Interface**:
```yaml
INPUT:
  - Competitor channel list (5-10 channels)
  - Monitoring frequency (daily/weekly)
  - Competitive focus (content strategy, SEO, thumbnails, hooks)

OUTPUT:
  - competitor_report_[PERIOD].md:
      - Top-performing competitor videos (views, CTR, retention estimates)
      - Strategy analysis (what they're doing differently)
      - Content gaps (topics they haven't covered)
      - Threat assessment (rising competitors, format shifts)
      - Opportunity recommendations (untapped angles)
```

**Competitor Tracking Framework**:
```
PERFORMANCE METRICS:

VIDEO PERFORMANCE:
├─ Views (total, velocity, views/day)
├─ Estimated CTR (views/impressions proxy)
├─ Engagement rate (likes+comments/views)
├─ Upload frequency (videos/week, consistency)

CONTENT STRATEGY:
├─ Topic distribution (% evergreen vs trending)
├─ Format patterns (listicles, tutorials, commentary)
├─ Video length trends (average duration, range)
├─ Thumbnail style (text overlay %, facial expression %)

AUDIENCE GROWTH:
├─ Subscriber velocity (subs/week, acceleration)
├─ Subscriber conversion (subs/video published)
├─ Views/sub ratio (health metric: 4-8 healthy, <2 warning)
├─ Engagement trends (comments/video over time)

SEO STRATEGY:
├─ Keyword targeting (primary keywords per video)
├─ Title formulas (common patterns)
├─ Tag strategies (overlap, unique tags)
├─ Description structure (length, CTAs, links)
```

**Content Gap Analysis**:
```
COMPETITOR MATRIX:

Topic A: Covered by [3/5 competitors]
├─ Opportunity Score: MEDIUM (some saturation)
├─ Differentiation Angle: [Specific unique perspective]
└─ Recommendation: CREATE with differentiation

Topic B: Covered by [0/5 competitors]
├─ Opportunity Score: HIGH (untapped)
├─ Demand Validation: [Search volume: 5K/mo]
└─ Recommendation: CREATE immediately (first-mover advantage)

Topic C: Covered by [5/5 competitors]
├─ Opportunity Score: LOW (saturated)
├─ Best-Performing Video: [Competitor X, 100K views]
└─ Recommendation: SKIP or find radically different angle
```

**Threat Assessment**:
```
RISING COMPETITORS:

Channel X:
├─ Growth Rate: +5K subs/week (accelerating)
├─ Differentiator: [Higher production quality, better hooks]
├─ Threat Level: HIGH (in our niche, superior execution)
├─ Response: Analyze top 5 videos, adopt winning patterns

Channel Y:
├─ Growth Rate: +2K subs/week (steady)
├─ Differentiator: [Different audience segment]
├─ Threat Level: LOW (minimal overlap)
├─ Response: MONITOR, no immediate action
```

**Tool Access Requirements**:
- YouTube Data API v3 (competitor video data, analytics)
- VidIQ API (competitor tracking, keyword overlap)
- Social Blade API (subscriber growth trends)
- WebSearch (supplementary competitor research)

**Human Approval Gates**:
- **Gate 1**: Opportunity recommendations (human decides which content gaps to pursue)
- **Bypass Criteria**: None - all strategic decisions require human input

**Integration Points**:
- → Trend Scanner (competitive trends feed into topic discovery)
- → Growth Strategist (competitive intelligence informs strategy)
- ← Keyword Researcher (competitor keyword analysis)

**Success Metrics**:
- Content gap identification accuracy: >70% of suggested topics perform above channel avg
- Competitor strategy analysis: >80% human validation
- Threat detection (rising competitors identified ≥30 days before overtaking)

**Error Handling**:
```python
# Competitor Monitor error protocols
if competitor_data_unavailable:
    fallback_to_manual_scraping()
    log_api_access_issue()

if anomalous_competitor_growth (sudden spike):
    investigate_cause(viral video, algorithm boost, external traffic)
    flag_for_deeper_analysis()

if all_competitors_declining:
    flag_niche_saturation_warning()
    recommend_niche_pivot_or_expansion()
```

---

### 6.3 AGENT: Growth Strategist

**Primary Function**: Synthesize all analytics, recommend strategic priorities, forecast growth

**Scope**:
- Multi-source data synthesis (retention, competitor, audience, metadata)
- Strategic priority recommendations (content focus, format experiments)
- Growth forecasting (subscriber projections, monetization milestones)
- Resource allocation guidance (time/budget optimization)

**Input/Output Interface**:
```yaml
INPUT:
  - Retention analysis (from Retention Analyzer)
  - Competitor intelligence (from Competitor Monitor)
  - Audience insights (from Audience Analyst)
  - Metadata performance (from Metadata Optimizer)
  - Channel goals (subscriber targets, revenue goals)

OUTPUT:
  - growth_strategy_[PERIOD].md:
      - Strategic priorities (ranked by impact)
      - Content calendar recommendations (70/20/10 mix)
      - Format experiments (new approaches to test)
      - Growth forecast (subscriber projections, confidence intervals)
      - Resource allocation (time/budget per priority)
      - Risk assessment (market shifts, competitive threats)
```

**Strategic Framework**:
```
PRIORITY SCORING (Impact × Feasibility):

PRIORITY 1: [Specific initiative]
├─ Impact: HIGH (projected +20% subscriber growth)
├─ Feasibility: HIGH (existing resources sufficient)
├─ Time Investment: 5 hours/week
├─ Expected ROI: +500 subs/month
├─ Action: IMPLEMENT immediately

PRIORITY 2: [Specific initiative]
├─ Impact: HIGH (projected +15% retention improvement)
├─ Feasibility: MEDIUM (requires new tool: $15/mo)
├─ Time Investment: 3 hours/week
├─ Expected ROI: +8% AVD → higher watch time
├─ Action: APPROVE budget, implement

PRIORITY 3: [Specific initiative]
├─ Impact: MEDIUM (projected +10% CTR improvement)
├─ Feasibility: HIGH (process change only)
├─ Time Investment: 2 hours/week
├─ Expected ROI: +200 views/video
├─ Action: IMPLEMENT as bandwidth allows

PRIORITY 4: [Specific initiative]
├─ Impact: LOW (projected +5% engagement)
├─ Feasibility: LOW (requires external collaboration)
├─ Time Investment: 10 hours/week
├─ Expected ROI: Uncertain
├─ Action: DEFER until Priorities 1-3 complete
```

**Growth Forecasting Model**:
```
SUBSCRIBER PROJECTION (Next 90 Days):

Current State:
├─ Subscribers: [X]
├─ Upload frequency: [Y videos/week]
├─ Avg views/video: [Z]
├─ Subscriber conversion: [W%]

Baseline Scenario (No changes):
├─ Projected subs in 90 days: [X + (Y × 12 × Z × W/100)]
├─ Confidence: 80%

Optimized Scenario (Implement Priority 1-2):
├─ Upload frequency: +50% (Y → 1.5Y)
├─ Subscriber conversion: +30% (W → 1.3W)
├─ Projected subs in 90 days: [X + (1.5Y × 12 × Z × 1.3W/100)]
├─ Confidence: 60%
├─ Required investment: [Time/budget]

Aggressive Scenario (Implement All Priorities):
├─ Upload frequency: +100% (Y → 2Y)
├─ Subscriber conversion: +50% (W → 1.5W)
├─ Avg views/video: +30% (Z → 1.3Z)
├─ Projected subs in 90 days: [X + (2Y × 12 × 1.3Z × 1.5W/100)]
├─ Confidence: 40%
├─ Required investment: [Significantly higher time/budget]
├─ Risk: Burnout, quality degradation
```

**Content Calendar Strategy (70/20/10 Framework)**:
```
NEXT 30 DAYS (12 videos at 3/week):

EVERGREEN (70% = 8 videos):
├─ Video 1: [High-demand keyword topic]
├─ Video 2: [Series continuation from existing pillar]
├─ Video 3: [How-to tutorial addressing audience question]
├─ ...
├─ Video 8: [Comparison video (high search intent)]

TRENDING (20% = 3 videos):
├─ Video 9: [Current event commentary]
├─ Video 10: [Algorithm update reaction]
├─ Video 11: [Viral trend integration]

EXPERIMENTAL (10% = 1 video):
├─ Video 12: [New format test: short-form compilation]
└─ Success Metric: If >1.5× avg views → expand to 15% in next period
```

**Tool Access Requirements**:
- Data aggregation (consolidate from all analytics agents)
- Forecasting model (time series analysis, growth projections)
- Recommendation engine (priority scoring algorithm)
- Scenario planning library (what-if analysis)

**Human Approval Gates**:
- **Gate 1**: Strategic priorities (human approves top 3 priorities)
- **Gate 2**: Resource allocation (human confirms time/budget commitment)

**Integration Points**:
- ← Retention Analyzer (retention insights)
- ← Competitor Monitor (competitive intelligence)
- ← Audience Analyst (audience behavior patterns)
- → All agents (strategic direction informs all agent operations)

**Success Metrics**:
- Growth forecast accuracy: ±20% of actual results
- Strategic priority effectiveness: >70% of implemented priorities achieve projected impact
- Resource allocation optimization: >80% time/budget spent on high-impact activities

**Error Handling**:
```python
# Growth Strategist error protocols
if growth_projection_confidence < 50%:
    flag_high_uncertainty()
    provide_sensitivity_analysis(best/worst case scenarios)

if conflicting_priorities_detected:
    escalate_to_human_decision()
    provide_trade_off_analysis()

if all_priorities_low_impact:
    flag_strategic_inflection_point()
    recommend_fundamental_pivot(niche, format, audience)
```

---

## 7. AGENT DEPLOYMENT & ORCHESTRATION

### 7.1 Deployment Architecture

**Claude Agent SDK Integration**:
```python
from claude_agent_sdk import Agent, Workflow

# Example: Trend Scanner Agent Deployment
trend_scanner = Agent(
    name="TrendScanner",
    role="Monitor YouTube/TikTok/Instagram for emerging trends",
    tools=[
        "vidiq_api",
        "google_trends_api",
        "youtube_data_api",
        "tiktok_creative_center_api"
    ],
    approval_gates=[
        Gate(name="topic_selection", human_required=True)
    ],
    output_format="trend_report_YYYY_MM_DD.md",
    schedule="daily",
    integration_points={
        "downstream": ["KeywordResearcher", "HookGenerator", "GrowthStrategist"]
    }
)

# Workflow Orchestration
production_workflow = Workflow(
    name="DeadManAI_Production_Workflow",
    phases=[
        Phase("Research", agents=[
            trend_scanner, keyword_researcher, audience_analyst
        ]),
        Phase("Scriptwriting", agents=[
            hook_generator, structure_optimizer, fact_checker
        ]),
        Phase("Production", agents=[
            broll_curator, music_selector, qc_inspector
        ]),
        Phase("Publishing", agents=[
            metadata_optimizer, thumbnail_ab_tester, multi_platform_distributor
        ]),
        Phase("Analytics", agents=[
            retention_analyzer, competitor_monitor, growth_strategist
        ])
    ],
    human_checkpoints=[
        "topic_approval",
        "script_approval",
        "final_qc_approval",
        "metadata_approval"
    ]
)
```

### 7.2 Human-in-Loop Checkpoints

**Mandatory Approval Gates (3-Factor Compliance)**:
```
CHECKPOINT 1: Topic Selection (RESEARCH → SCRIPTWRITING)
├─ Agent: Trend Scanner
├─ Decision: Which 3 trends to pursue this week?
├─ Human Input: Select topics, approve angles
├─ Rationale: Ensures content aligns with channel strategy

CHECKPOINT 2: Script Approval (SCRIPTWRITING → PRODUCTION)
├─ Agent: Structure Optimizer
├─ Decision: Is optimized script ready for production?
├─ Human Input: Approve script, request revisions, or reject
├─ Rationale: Maintains brand voice, creative vision

CHECKPOINT 3: Final QC (PRODUCTION → PUBLISHING)
├─ Agent: QC Inspector
├─ Decision: Does video meet quality standards?
├─ Human Input: Approve for publishing or send for revisions
├─ Rationale: Final quality gate before public release

CHECKPOINT 4: Metadata Approval (PUBLISHING)
├─ Agent: Metadata Optimizer
├─ Decision: Are title/description/tags optimized?
├─ Human Input: Select title variant, approve metadata
├─ Rationale: Title/thumbnail have massive CTR impact

CHECKPOINT 5: Strategic Priorities (ANALYTICS → STRATEGY)
├─ Agent: Growth Strategist
├─ Decision: What should we focus on next?
├─ Human Input: Approve top 3 priorities, allocate resources
├─ Rationale: Ensures strategic direction stays human-led
```

### 7.3 Error Escalation Protocol

```
ERROR SEVERITY LEVELS:

LEVEL 1: INFO (Log only)
├─ Example: API rate limit approaching
├─ Action: Agent logs event, continues operation
└─ Human Notification: None

LEVEL 2: WARNING (Flag for review)
├─ Example: Metadata keyword density high (spam risk)
├─ Action: Agent flags issue, provides recommendation
└─ Human Notification: Daily digest

LEVEL 3: ERROR (Halt agent, request human input)
├─ Example: Fact-check confidence <70%, conflicting sources
├─ Action: Agent halts, escalates to human review
└─ Human Notification: Immediate (blocks workflow)

LEVEL 4: CRITICAL (Halt workflow, immediate escalation)
├─ Example: Copyright strike detected, QC critical failure
├─ Action: All agents halt, human review required
└─ Human Notification: Immediate + alert

ERROR HANDLING FLOW:

Agent detects issue
    │
    ▼
Classify severity (1-4)
    │
    ├─ LEVEL 1 → Log, continue
    ├─ LEVEL 2 → Flag, continue
    ├─ LEVEL 3 → Halt agent, request human input
    └─ LEVEL 4 → Halt workflow, alert human
```

---

## 8. INTEGRATION WITH EXISTING SYSTEMS

### 8.1 Fabric Patterns Integration

**234+ Fabric Patterns for Production Tasks**:
```bash
# Research Phase
fabric -y "youtube-url" --pattern extract_wisdom | save trend_research.md
fabric -sp "competitor-channel-id" --pattern analyze_claims

# Scriptwriting Phase
fabric --pattern create_video_chapters < script_draft.md
fabric --pattern improve_writing < script_v1.md | fabric --pattern humanize > script_v2.md

# Publishing Phase
fabric --pattern write_video_description < script_final.md
fabric --pattern create_tags < video_summary.md

# Analytics Phase
fabric --pattern analyze_youtube_comments < comments_export.csv
fabric --pattern summarize_feedback < retention_report.md
```

**Agent-Fabric Integration**:
| Agent | Fabric Pattern | Purpose |
|-------|----------------|---------|
| Trend Scanner | extract_wisdom | Extract key insights from trending videos |
| Audience Analyst | analyze_youtube_comments | Sentiment analysis on comments |
| Hook Generator | create_micro_summary | Condense hook essence for testing |
| Fact Checker | analyze_claims | Verify factual assertions |
| Metadata Optimizer | write_video_description | Generate optimized descriptions |

### 8.2 Planning Files Integration

**YouTube Planning Files Compatibility**:
```yaml
# planning_file_video_001.yaml (YouTube Planning Files format)
video:
  title: "{{ metadata_optimizer.output.title }}"
  description: "{{ metadata_optimizer.output.description }}"
  tags: "{{ metadata_optimizer.output.tags }}"

production:
  script: "{{ structure_optimizer.output.final_script }}"
  broll: "{{ broll_curator.output.footage_list }}"
  music: "{{ music_selector.output.track_selection }}"

publishing:
  youtube:
    scheduled_time: "{{ multi_platform_distributor.output.youtube_schedule }}"
    end_screen: "{{ metadata_optimizer.output.end_screen_config }}"
  tiktok:
    scheduled_time: "{{ multi_platform_distributor.output.tiktok_schedule }}"
    caption: "{{ metadata_optimizer.output.tiktok_caption }}"
```

**Session Continuity (5-Minute Checkpoints)**:
```markdown
# ACTIVE_SESSION.md (Per CLAUDE.md Spec)

## CURRENT GOAL
Complete production workflow for Video #47: "YouTube SEO 2026 Ultimate Guide"

## ACTIVE TASK
Phase 3: Production - B-roll curation (70% complete)
- ✅ Stock footage sourced (Pexels, Storyblocks)
- ⏳ AI-generated clips (Runway: 3/5 complete)
- ⏳ Timeline markers (DaVinci Resolve import pending)

## COMPLETED THIS SESSION
1. ✅ Research Phase (Trend Scanner + Keyword Researcher)
2. ✅ Scriptwriting Phase (Hook Generator + Structure Optimizer + Fact Checker)
3. ✅ Production Phase (B-roll Curator 70%, Music Selector 100%)

## PENDING TASKS
1. ⏳ Complete B-roll curation (Runway clips 4-5)
2. ⏳ QC inspection (audio, visual, captions, brand)
3. ⏳ Metadata optimization (title, description, tags)
4. ⏳ Thumbnail A/B testing (3 variants)
5. ⏳ Multi-platform distribution (YouTube + TikTok + Instagram)

## KEY FILES MODIFIED
| File | Status | Location |
|------|--------|----------|
| script_final.md | ✅ Complete | G:/Video_047/ |
| broll_package/ | ⏳ 70% | G:/Video_047/assets/ |
| music_track.mp3 | ✅ Licensed | G:/Video_047/assets/audio/ |

## CRITICAL CONTEXT
- B-roll Agent requested 5 AI-generated clips (Runway API)
- Clips 1-3 completed, clips 4-5 in progress (ETA: 10 minutes)
- Music selected: "Thoughtful Piano" (Epidemic Sound, license verified)
- Next checkpoint: QC inspection once B-roll complete

## RECOVERY INSTRUCTIONS
If disconnected:
1. Resume B-roll curation (check Runway API for clip 4-5 status)
2. Download completed clips to G:/Video_047/assets/broll/ai_generated/
3. Generate DaVinci Resolve timeline XML
4. Proceed to QC inspection phase
```

### 8.3 NASA Standards Compliance

**NPR 7120/7123/8735 Documentation Requirements**:
```
PRODUCTION LIFECYCLE PHASES:

FORMULATION PHASE:
├─ Pre-Phase A: Topic discovery (Trend Scanner)
├─ Phase A: Research & outline (Keyword Researcher, Audience Analyst)
└─ Phase B: Script draft (Hook Generator, Structure Optimizer)

IMPLEMENTATION PHASE:
├─ Phase C: Production (B-roll Curator, Music Selector)
├─ Phase D: Post-production (QC Inspector)
├─ Phase E: Publishing (Metadata Optimizer, Multi-Platform Distributor)
└─ Phase F: Analytics (Retention Analyzer, Competitor Monitor, Growth Strategist)

KEY DECISION POINTS (KDPs):
├─ KDP A: Approve topic (human checkpoint)
├─ KDP B: Approve script (human checkpoint)
├─ KDP C: Approve final edit (QC Inspector → human checkpoint)
└─ KDP D: Approve publishing (human checkpoint)
```

**Quality Assurance Checkpoints**:
```
QA CHECKPOINT 1: Research Coverage
□ All claims have 3+ sources (Fact Checker verification)
□ Keyword research complete (Search Demand Ratio >2.0x)
□ Audience alignment verified (Audience Analyst validation)

QA CHECKPOINT 2: Script Completeness
□ All outline beats developed into dialogue
□ Hook strength ≥18/25 (Hook Generator scoring)
□ Retention curve predicted >45% AVD (Structure Optimizer)

QA CHECKPOINT 3: Production Quality
□ Audio levels LUFS -14 to -16 (QC Inspector verification)
□ Visual consistency (color grading, resolution)
□ Caption accuracy (subtitle timing ±0.5s)

QA CHECKPOINT 4: Publishing Readiness
□ Metadata optimized (title CTR prediction >5%)
□ Thumbnail A/B variants prepared (2-3 designs)
□ Multi-platform adaptations complete
```

---

## 9. PERFORMANCE METRICS & KPIs

### 9.1 Agent-Level Metrics

**Per-Agent Success Criteria**:
| Agent | Primary KPI | Target | Measurement |
|-------|-------------|--------|-------------|
| Trend Scanner | Topic acceptance rate | >40% | Topics suggested → approved |
| Keyword Researcher | Top 10 search ranking | >60% | Videos ranking in top 10 for primary keyword |
| Audience Analyst | Persona accuracy | >85% | Human validation of audience profiles |
| Hook Generator | CTR achievement | >60% | Videos achieving >5% CTR |
| Structure Optimizer | AVD achievement | >70% | Videos achieving >45% AVD |
| Fact Checker | Citation coverage | >95% | Claims with sources |
| B-roll Curator | Relevance score | >80% | Human rating >8/10 |
| Music Selector | Licensing compliance | 100% | Zero Content ID claims |
| QC Inspector | Pass rate (first submission) | >80% | Videos passing QC first time |
| Metadata Optimizer | CTR achievement | >70% | Videos achieving >5% CTR |
| Thumbnail A/B Tester | CTR improvement | >10% | Winner vs baseline CTR increase |
| Multi-Platform Distributor | Multi-platform reach | >50K | Total impressions across platforms |
| Retention Analyzer | Prediction accuracy | ±10% | Predicted vs actual retention |
| Competitor Monitor | Opportunity accuracy | >70% | Suggested topics performing above avg |
| Growth Strategist | Forecast accuracy | ±20% | Projected vs actual growth |

### 9.2 Workflow-Level Metrics

**End-to-End Production Metrics**:
```
TIME EFFICIENCY:

Manual Workflow (Baseline):
├─ Research & outline: 4-5 hours
├─ Scriptwriting: 4-5 hours (290 min per R64)
├─ Production: 3-4 hours (B-roll, audio, editing)
├─ Publishing: 1-2 hours (metadata, thumbnails, upload)
├─ TOTAL: 12-16 hours per video

AI-Augmented Workflow (Target):
├─ Research & outline: 1-2 hours (agents automate 60%)
├─ Scriptwriting: 1.5-2 hours (80 min per R64)
├─ Production: 1.5-2 hours (automated B-roll curation, music selection)
├─ Publishing: 0.5-1 hour (automated metadata, thumbnail variants)
├─ TOTAL: 4.5-7 hours per video
├─ TIME SAVINGS: 60-70%

QUALITY IMPROVEMENTS:

Retention (AVD):
├─ Baseline: 35-40% (industry avg)
├─ Target: 45-50% (Structure Optimizer + Retention Analyzer)
├─ Improvement: +25-40%

CTR:
├─ Baseline: 3-4% (industry avg)
├─ Target: 5-7% (Hook Generator + Metadata Optimizer + Thumbnail A/B Tester)
├─ Improvement: +40-75%

Factual Accuracy:
├─ Baseline: 2.3 errors per script (manual)
├─ Target: <0.5 errors per script (Fact Checker)
├─ Improvement: -78%

PRODUCTION VELOCITY:

Solo Creator:
├─ Baseline: 1 video/week (12-16 hours)
├─ Target: 2-3 videos/week (4.5-7 hours each)
├─ Improvement: 2-3x output

Small Team (2-3 people):
├─ Baseline: 2-3 videos/week
├─ Target: 4-6 videos/week
├─ Improvement: 2x output

Production Team (5+ people):
├─ Baseline: 5-7 videos/week
├─ Target: 10-15 videos/week
├─ Improvement: 2x output
```

### 9.3 Business Impact Metrics

**Monetization & Growth**:
```
CHANNEL GROWTH:

Subscriber Velocity:
├─ Baseline: 100-200 subs/month (manual workflow)
├─ Target: 300-500 subs/month (AI-augmented workflow)
├─ Driver: Increased upload frequency + higher CTR/AVD

Views:
├─ Baseline: 10K-20K views/month
├─ Target: 30K-50K views/month
├─ Driver: Better SEO (Keyword Researcher) + multi-platform distribution

REVENUE:

AdSense Revenue (YPP):
├─ Baseline: $50-200/month (10-20K views, $5-10 CPM)
├─ Target: $150-500/month (30-50K views, $5-10 CPM)
├─ Driver: Increased views, maintained CPM

Affiliate Revenue (Secondary):
├─ Baseline: $0-50/month
├─ Target: $100-300/month
├─ Driver: Better CTAs (Structure Optimizer), more videos with affiliate links

UGC Licensing (Tertiary):
├─ Baseline: $0/month
├─ Target: $50-200/month
├─ Driver: Viral clips (Multi-Platform Distributor → Facebook UGC)

TOTAL MONTHLY REVENUE:
├─ Baseline: $50-250/month
├─ Target: $300-1,000/month
├─ Improvement: 4-6x revenue
```

---

## 10. DEPLOYMENT ROADMAP

### Phase 1: Core Agents (Weeks 1-2)

**Deploy Critical Path Agents**:
```
WEEK 1:
├─ Deploy Trend Scanner
├─ Deploy Keyword Researcher
├─ Deploy Hook Generator
├─ Deploy Structure Optimizer
└─ Test Research → Scriptwriting workflow

WEEK 2:
├─ Deploy Fact Checker
├─ Deploy Metadata Optimizer
├─ Deploy QC Inspector
└─ Test full Research → Scriptwriting → Publishing workflow
```

### Phase 2: Production Agents (Weeks 3-4)

**Deploy Asset Management Agents**:
```
WEEK 3:
├─ Deploy B-roll Curator
├─ Deploy Music Selector
└─ Test Production phase integration

WEEK 4:
├─ Deploy Thumbnail A/B Tester
├─ Deploy Multi-Platform Distributor
└─ Test Publishing phase integration
```

### Phase 3: Analytics Agents (Weeks 5-6)

**Deploy Performance Optimization Agents**:
```
WEEK 5:
├─ Deploy Retention Analyzer
├─ Deploy Competitor Monitor
└─ Collect baseline performance data

WEEK 6:
├─ Deploy Audience Analyst
├─ Deploy Growth Strategist
└─ Test full Analytics → Strategy feedback loop
```

### Phase 4: Optimization & Scale (Weeks 7-12)

**Refine, Optimize, Scale**:
```
WEEK 7-8: Agent Tuning
├─ Analyze agent performance vs KPIs
├─ Refine prompts, thresholds, decision logic
└─ A/B test agent variants

WEEK 9-10: Workflow Optimization
├─ Streamline approval gates (reduce friction)
├─ Automate repetitive human decisions
└─ Increase production velocity (2-3x target)

WEEK 11-12: Full Production Scale
├─ Ramp to target output (solo: 2-3 videos/week)
├─ Monitor quality metrics (maintain >80% targets)
└─ Document lessons learned, iterate
```

---

## 11. APPENDIX: AGENT PROMPTS

### A.1 Trend Scanner Prompt

```
You are the Trend Scanner agent for DeadManAI, a faceless YouTube content creation system.

OBJECTIVE: Monitor YouTube, TikTok, and Instagram to identify emerging trends and high-potential topics in the [NICHE] niche.

INPUTS:
- Niche specification: [NICHE]
- Geographic targeting: [US/CA/UK priority]
- Update frequency: [daily/weekly]

OUTPUTS:
Generate trend_report_YYYY_MM_DD.md with:
1. Top 10 trending topics in niche (with search volume data from Google Trends, VidIQ)
2. Viral coefficient estimates (K-factor calculation per R63 STEPPS framework)
3. STEPPS scores (0-30 scale: Social Currency, Triggers, Emotion, Public, Practical Value, Stories)
4. Recommended action (CREATE/MONITOR/SKIP) with reasoning

TOOLS AVAILABLE:
- VidIQ API (trend analytics)
- Google Trends API (search volume)
- YouTube Data API v3 (video performance)
- TikTok Creative Center (trending sounds, hashtags)
- WebSearch (supplementary research)

APPROVAL GATE:
Present top 3 trending topics to human for selection. Human will choose which to pursue.

SUCCESS CRITERIA:
- Topic suggestion acceptance rate >40%
- Suggested videos achieving 2x avg channel CTR
- Trend detection lead time >24 hours before saturation

Execute trend scan now for [DATE].
```

### A.2 Hook Generator Prompt

```
You are the Hook Generator agent for DeadManAI, a faceless YouTube content creation system.

OBJECTIVE: Generate viral hooks optimized for CTR and first-15-second retention.

INPUTS:
- Video topic: [TOPIC]
- Target emotion: [awe/excitement/curiosity per STEPPS]
- Script outline: [OPTIONAL CONTEXT]

OUTPUTS:
Generate hooks_[TOPIC].md with:
1. 5 hook variants (0-15 second scripts)
2. Hook strength scores (0-25 rubric from R64)
3. Predicted CTR range (based on pattern analysis)
4. Thumbnail pairing recommendations
5. A/B testing strategy

HOOK FORMULAS (Apply 6 viral formulas from R64):
1. STAT SHOCK: "[Surprising statistic] + [Common belief challenged] + [Promise of explanation]"
2. FORBIDDEN KNOWLEDGE: "[Authority figure] doesn't want you to know + [Exclusive insight]"
3. TRANSFORMATION PROMISE: "How I went from [undesirable state] to [desirable state] in [timeframe]"
4. CONTRARIAN TAKE: "Everything you know about [X] is wrong + [Bold claim]"
5. URGENCY/SCARCITY: "[Time-sensitive opportunity] + [Consequence of missing out]"
6. STORY HOOK: "[Relatable struggle] + [Unexpected twist] + [Promise of resolution]"

SCORING RUBRIC (0-25):
- Curiosity gap strength (0-10): How compelling is the information gap?
- Emotional activation (0-10): Does it trigger high-arousal emotion?
- Specificity (0-5): Is the promise concrete and specific?

APPROVAL GATE:
Present 5 hook variants to human. Human will choose 1-2 for production.

SUCCESS CRITERIA:
- Generated hooks achieving >5% CTR: >60% of videos
- Hook strength scores matching actual CTR (correlation >0.7)
- First-15-second retention >70%

Generate 5 hook variants now for topic: [TOPIC]
```

---

## 12. VERSION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 1.1.0 | 2026-01-10 | Added Deep Research Agent and Intelligence Bridge integration. Enhanced Trend Scanner with offline intelligence inputs. |
| 1.0.0 | 2026-01-03 | Initial AI Production Agent Team specification - 15 agents across 5 categories (Research, Scriptwriting, Production, Publishing, Analytics), full integration with CLAUDE.md 3-Factor Ruling, NASA NPR compliance, Fabric patterns, Planning Files, Session Continuity |

---

**Document Status:** PRODUCTION READY
**Next Review:** 2026-02-03 (30 days)
**Maintained By:** DeadManAI // The Unseen

---

```
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│   "AI augments, human directs."                                │
│   "Structure enables scale."                                   │
│   "Verification enables trust."                                │
│   "This is how we automate with integrity."                    │
│                                                                │
│                    // THE UNSEEN //                            │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```
