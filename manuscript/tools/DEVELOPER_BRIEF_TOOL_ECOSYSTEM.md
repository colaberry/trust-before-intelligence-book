# Trust Before Intelligence: Digital Companion Tool Ecosystem
## Developer Brief

**Document Purpose:** Comprehensive overview of how all 7 digital companion tools work together, their data flows, and implementation guidance.
**Website:** trustbeforeintelligence.ai
**Last Updated:** March 2026

---

## The Big Picture

The digital companion is a suite of 7 interconnected tools that guide enterprise leaders through assessing, planning, building, and sustaining AI agent infrastructure. They follow a natural journey:

```
ASSESS → PLAN → BUILD → SUSTAIN
```

```
┌─────────────────────────────────────────────────────────────────────┐
│                        USER JOURNEY                                 │
│                                                                     │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────────────┐  │
│  │   PHASE 1     │    │   PHASE 2     │    │      PHASE 3         │  │
│  │   ASSESS      │    │   PLAN        │    │   BUILD & SUSTAIN    │  │
│  │              │    │              │    │                      │  │
│  │ 1. INPACT    │───>│ 3. Stack     │───>│ 5. 90-Day Tracker   │  │
│  │    Assessment │    │    Builder    │    │                      │  │
│  │              │    │              │    │ 6. Compliance        │  │
│  │ 2. GOALS     │    │ 4. Vendor    │    │    Navigator         │  │
│  │    Readiness  │    │    Advisor    │    │                      │  │
│  │    Checker    │    │              │    │ 7. Trust Guide       │  │
│  └──────────────┘    └──────────────┘    └──────────────────────┘  │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Tool 1: INPACT Assessment

**URL:** trustbeforeintelligence.ai/assessment
**Purpose:** "Can we support AI agents?" — Measures infrastructure capability.
**Book Reference:** Chapter 2 (framework), Chapter 9 (methodology)

### What It Does
A 36-question assessment that scores an organization's infrastructure readiness for AI agents across 6 dimensions:

| Dimension | What It Measures |
|-----------|-----------------|
| **I** - Instant | Can your infrastructure respond fast enough? (sub-2-second target) |
| **N** - Natural | Can it understand business language? |
| **P** - Permitted | Are access controls and audit trails in place? |
| **A** - Adaptive | Can it learn and improve over time? |
| **C** - Contextual | Can it pull data from multiple systems? |
| **T** - Transparent | Can it explain its decisions? |

### Scoring
- 6 questions per dimension, each scored 1-6
- Dimension score = average of 6 questions (1-6)
- Total INPACT score = sum of 6 dimension averages (6-36)
- Percentage = (Total / 36) x 100

### Trust Bands
| Score | Percentage | Band |
|-------|-----------|------|
| 31-36 | 86-100% | High Trust — Production-ready |
| 24-30 | 67-85% | Good Trust — Pilot-ready |
| 18-23 | 50-66% | Moderate Trust — Significant work needed |
| 12-17 | 33-49% | Low Trust — Major transformation required |
| 6-11 | <33% | Very Low Trust — Complete rebuild required |

### User Flow
1. Lead capture (email, name, company, role)
2. Context selection (industry, company size, current AI stage)
3. 36 questions across 6 sections (scored 1-6 each via slider or radio)
4. Real-time score calculation
5. PDF report with radar chart, gap analysis, Echo Health comparison, recommended next steps

### Key Data Files
- **Questions & Rubrics:** `tools/gpt_knowledge_bases/kb_INPACT_assessment_36_questions.md`
- **Scoring Rubrics (summary):** `tools/gpt_knowledge_bases/kb_INPACT_scoring_rubrics.md`
- **Web Form Spec:** `tools/web_tools/web_form_inpact_assessment.md`

### Output
- INPACT score (X/36 = Y%)
- Dimension breakdown (radar chart)
- Gap identification (which dimensions are below threshold)
- Comparison to Echo Health baseline (10/36 at Week 0)
- Recommended starting phase based on lowest dimensions

### Feeds Into
- **Stack Builder** (gaps tell you what layers to build)
- **90-Day Tracker** (baseline INPACT score for Week 0)
- **Vendor Advisor** (INPACT thresholds filter product recommendations)

---

## Tool 2: GOALS Readiness Checker

**URL:** trustbeforeintelligence.ai/goals-assessment
**Purpose:** "Can we sustain AI agent operations?" — Measures operational sustainability.
**Book Reference:** Chapter 7

### What It Does
A 30-question Yes/No assessment that scores operational readiness across 5 dimensions:

| Dimension | What It Measures |
|-----------|-----------------|
| **G** - Governance | Access controls, audit logging, compliance, security |
| **O** - Observability | Monitoring, tracing, cost tracking, drift detection |
| **A** - Availability | Response time, data freshness, uptime, load capacity |
| **L** - Lexicon | Entity resolution, business glossary, disambiguation, learning |
| **S** - Solid | Data accuracy, completeness, consistency, quality gates |

### Key Difference from INPACT
| | INPACT | GOALS |
|---|--------|-------|
| **Measures** | Infrastructure capability | Operational sustainability |
| **When** | BEFORE transformation | DURING/AFTER transformation |
| **Question** | "Can we support agents?" | "Can we sustain agents?" |
| **Format** | 36 questions, scored 1-6 | 30 questions, Yes/No |
| **Scale** | 6-36 (percentage of 36) | 5-25 (percentage of 25) |

### Scoring
- 6 Yes/No questions per dimension (NOTE: considering reducing to 5 per dimension for cleaner 1:1 mapping)
- Current conversion: 0-2 Yes = 2/5, 3 Yes = 3/5, 4-5 Yes = 4/5, 6 Yes = 5/5
- Total GOALS score = sum of 5 dimension scores (5-25)
- Healthcare threshold: 21/25 (84%) with all dimensions meeting minimums

### Readiness Bands
| Score | Percentage | Band |
|-------|-----------|------|
| 23-25 | 92-100% | Excellent — Production-ready |
| 21-22 | 84-88% | Healthcare Ready — Meets healthcare threshold |
| 18-20 | 72-80% | Good — Minor gaps |
| 14-17 | 56-68% | Moderate — Not production-ready |
| 10-13 | 40-52% | Low — Major operational gaps |
| 5-9 | 20-36% | Critical — Operational foundation missing |

### Key Data Files
- **Questions:** `tools/web_tools/web_form_goals_readiness_checker.md`
- **Web Form Spec:** Same file as above

### Feeds Into
- **90-Day Tracker** (baseline GOALS score)
- **Compliance Navigator** (deep dive on regulatory gaps)
- **Vendor Advisor** (GOALS thresholds filter product recommendations)

---

## Tool 3: Stack Builder

**URL:** trustbeforeintelligence.ai/stack-builder
**Purpose:** "What's missing and what should we build next?" — Gap analysis across the 7-Layer Architecture.
**Book Reference:** Chapters 4-6 (architecture), Chapter 10 (implementation)

### What It Does
An interactive inventory tool where users select what technologies they already have, and the system identifies what's missing across the book's 7-Layer Architecture.

### The 7 Layers

| Layer | Name | Purpose | Example Technologies |
|-------|------|---------|---------------------|
| L1 | Multi-Modal Storage | Store vectors, graphs, documents | Pinecone, Neo4j, Snowflake |
| L2 | Real-Time Data Fabric | Stream changes, keep data fresh | Kafka, Debezium, Flink |
| L3 | Universal Semantic Layer | Define business meaning | Cube, Atlan, Collibra |
| L4 | Intelligence Orchestration | RAG, embeddings, retrieval | LangChain, OpenAI, LlamaIndex |
| L5 | Agent-Aware Governance | ABAC, audit, secrets | OPA, HashiCorp Vault |
| L6 | Observability & Feedback | Monitor, learn, improve | LangSmith, Datadog |
| L7 | Self-Service Data Products | Orchestration, APIs, HITL | Airflow, Temporal, Kong |

### User Flow
1. Lead capture
2. For each of the 7 layers, user selects technologies they currently have (multi-select from known products, or "None")
3. System runs gap analysis logic per layer (CRITICAL / HIGH / MEDIUM gaps)
4. Prioritized build order recommended (3 sequences: Default, Healthcare, Fast MVP)
5. Budget estimation by tier ($30K Starter / $150K Growth / $300K+ Enterprise)
6. Handoff to Vendor Advisor for specific product selection

### Gap Classification
- **CRITICAL:** Missing component that blocks agent deployment entirely (e.g., no vector database, no ABAC)
- **HIGH:** Missing component that severely limits capability (e.g., no data quality, no audit logging)
- **MEDIUM:** Missing component that reduces effectiveness (e.g., no graph database, no A/B testing)

### Key Data Files
- **Knowledge Base:** `tools/gpt_knowledge_bases/kb_stack_builder.md`
- **Web Form Spec:** `tools/web_tools/web_form_stack_builder.md`

### Feeds Into
- **Vendor Advisor** (gaps become product selection queries)
- **90-Day Tracker** (build plan maps to weekly milestones)

---

## Tool 4: Vendor Advisor

**URL:** trustbeforeintelligence.ai/vendors
**Purpose:** "Which specific products should we buy?" — Product recommendations scored against both INPACT and GOALS.
**Book Reference:** Chapter 11 (Technology Selection Guide)

### What It Does
A product recommendation engine with 90+ technology products evaluated against both the INPACT framework (agent needs) and GOALS framework (operational sustainability).

### Dual-Threshold Selection
Every product must pass BOTH framework thresholds independently:

| Context | INPACT Minimum | GOALS Minimum |
|---------|---------------|---------------|
| Healthcare | 28/36 | 20/25 |
| Enterprise | 24/36 | 18/25 |
| Internal Tools | 18/36 | 14/25 |

This prevents two failure modes:
- High INPACT + Low GOALS = impressive tech your team can't sustain
- High GOALS + Low INPACT = easy to operate but can't meet agent needs

### Filtering Dimensions
1. **Layer** — Which of the 7 layers (from Stack Builder gap)
2. **Budget Tier** — $30K Starter, $150K Growth, $300K+ Enterprise
3. **Industry** — Healthcare (HIPAA/BAA required), Financial Services (PCI-DSS/SOX), Manufacturing, Retail, Public Sector
4. **Cloud Platform** — AWS, Azure, GCP preference

### Additional Decision Frameworks
- Build vs. Buy analysis
- Open-Source vs. Commercial trade-offs
- Cloud platform selection matrix
- Technology maturity assessment

### Key Data Files
- **Knowledge Base (90+ products):** `tools/gpt_knowledge_bases/kb_vendor_advisor.md`
- **Web Form Spec:** `tools/web_tools/web_form_vendor_advisor.md`

### Feeds Into
- **90-Day Tracker** (selected products populate the implementation plan)

---

## Tool 5: 90-Day Tracker

**URL:** trustbeforeintelligence.ai/tracker
**Purpose:** "Track your transformation week by week." — Implementation tracking from Day Zero through Week 12.
**Book Reference:** Chapter 10 (Implementation Roadmap)

### What It Does
A cloud-based project tracking tool that guides teams through the complete 90-day transformation, starting with a Day Zero readiness gate.

### Structure

**Day Zero Readiness (GATE)**
Before Week 1 begins, teams must complete a readiness checklist:

| Org Size | Checklist Items | Timeline |
|----------|----------------|----------|
| Small (<1,000) | 15 items | -2 weeks |
| Mid-size (1,000-15,000) | 25 items | Baseline (12 weeks) |
| Enterprise (15,000+) | 35 items | +2 to +4 weeks |

Gate logic: Must achieve 90%+ readiness with no critical blockers to unlock Week 1.

**Weekly Tracking (Weeks 1-12)**

| Phase | Weeks | Focus | Layers Built |
|-------|-------|-------|-------------|
| Phase 1: Foundation | 1-4 | Storage, streaming, data fabric | L1, L2 |
| Phase 2: Intelligence | 5-7 | Semantic layer, RAG, embeddings | L3, L4 |
| Phase 3: Trust | 8-10 | Governance, observability | L5, L6 |
| Phase 4: Production | 11-12 | Orchestration, HITL, go-live | L7 |

### Tabs / Views
1. **Day Zero Checklist** — Readiness items with completion tracking
2. **Weekly Progress** — Week-by-week milestones and status
3. **INPACT Score Tracking** — Visualize INPACT score improvement over 12 weeks
4. **GOALS Score Tracking** — Visualize GOALS score improvement
5. **7-Layer Build Status** — Which layers are complete/in-progress/not-started
6. **Budget Tracking** — Spend vs. plan by layer
7. **Team Dashboard** — Shareable view for stakeholders

### Key Data Files
- **Web Form Spec:** `tools/web_tools/web_form_90day_tracker.md`

### Receives Data From
- **INPACT Assessment** (baseline score for Week 0)
- **GOALS Readiness Checker** (baseline score)
- **Stack Builder** (gap priorities determine phase focus)
- **Vendor Advisor** (selected products populate build plan)

---

## Tool 6: Compliance Navigator

**URL:** trustbeforeintelligence.ai/compliance
**Purpose:** "What regulations apply to our AI agents?" — Regulatory compliance assessment.
**Book Reference:** Chapter 7 (Governance)

### What It Does
An interactive compliance assessment covering 30 regulatory categories and 200+ frameworks globally. Users select their industry and geography, and the tool identifies which regulations apply and maps gaps to the 7-Layer Architecture for remediation.

### Coverage
- **30 compliance categories** (HIPAA, GDPR, PCI-DSS, EU AI Act, SOX, FedRAMP, etc.)
- **Industry profiles:** Healthcare, Financial Services, Education, Government, Manufacturing, Retail, Technology
- **Geographic filtering:** US (Federal + state), EU, UK, APAC, etc.
- **7-Layer remediation mapping:** Each compliance gap maps to specific architecture layers

### User Flow
1. Lead capture
2. Geographic scope selection (multi-select regions)
3. Industry and data type selection
4. Automated compliance profile generation
5. Gap analysis with remediation guidance tied to architecture layers
6. PDF report with compliance checklist

### Key Data Files
- **Knowledge Base (200+ frameworks):** `tools/gpt_knowledge_bases/kb_compliance_navigator.md`
- **Web Form Spec:** `tools/web_tools/web_form_compliance_navigator.md`

### Feeds Into
- **90-Day Tracker** (compliance requirements inform Phase 3 priorities)
- **Vendor Advisor** (compliance requirements filter product recommendations)

---

## Tool 7: Trust Guide

**Purpose:** Conversational AI assistant that answers questions about the book's frameworks.
**Book Reference:** All chapters

### What It Does
A ChatGPT-style conversational tool (or embedded chat widget) that can answer questions about INPACT, GOALS, the 7-Layer Architecture, implementation guidance, and trust patterns. It uses the book's knowledge bases to provide contextual answers.

### Key Data Files
- **Trust Guide KB:** `tools/gpt_knowledge_bases/kb_trust_guide.md`
- **Trust Patterns KB:** `tools/gpt_knowledge_bases/kb_trust_patterns.md`
- **Context Types KB:** `tools/gpt_knowledge_bases/kb_context_types.md`

---

## Data Flow Between Tools

```
USER STARTS HERE
       │
       ▼
┌──────────────┐     Score + gaps      ┌──────────────┐
│   INPACT     │─────────────────────>│   Stack      │
│   Assessment │                       │   Builder    │
│   (36 Qs)    │──┐                    │   (7 Layers) │
└──────────────┘  │                    └──────┬───────┘
                  │                           │
                  │  Baseline                 │ Gap list
                  │  scores                   │
                  │                           ▼
┌──────────────┐  │                    ┌──────────────┐
│   GOALS      │  │                    │   Vendor     │
│   Readiness  │──┤                    │   Advisor    │
│   (30 Qs)    │  │                    │   (90+ prods)│
└──────────────┘  │                    └──────┬───────┘
                  │                           │
                  │                           │ Selected
                  │                           │ products
                  ▼                           ▼
           ┌─────────────────────────────────────┐
           │         90-Day Tracker               │
           │  Day Zero → Week 1-4 → 5-7 → 8-12  │
           │  INPACT tracking | GOALS tracking    │
           │  7-Layer build status | Budget       │
           └─────────────┬───────────────────────┘
                         │
                         │ Compliance needs
                         ▼
                  ┌──────────────┐
                  │  Compliance  │
                  │  Navigator   │
                  │  (200+ regs) │
                  └──────────────┘

        ┌──────────────┐
        │  Trust Guide │  ← Available at any stage for Q&A
        │  (Chat)      │
        └──────────────┘
```

---

## Shared Data Model

### Lead / User Record
Every tool captures the same core lead data:
- Email (primary key across all tools)
- Name
- Company
- Role (optional)
- Industry
- Current AI deployment stage

**Implementation Note:** Use a shared user/lead table so a user who completes the INPACT Assessment doesn't have to re-enter info for the Stack Builder. Single sign-on or email-based session linking recommended.

### Score Records
| Score Type | Range | Source Tool | Consumed By |
|-----------|-------|-------------|-------------|
| INPACT (total) | 6-36 | INPACT Assessment | Tracker, Vendor Advisor |
| INPACT (per dimension) | 1-6 each | INPACT Assessment | Stack Builder, Tracker |
| GOALS (total) | 5-25 | GOALS Readiness | Tracker, Vendor Advisor |
| GOALS (per dimension) | 1-5 each | GOALS Readiness | Tracker |
| Layer gaps | CRITICAL/HIGH/MEDIUM per layer | Stack Builder | Vendor Advisor, Tracker |

### Industry Context
Selected once, propagated to all tools:
- Determines compliance requirements (Compliance Navigator)
- Filters vendor recommendations (Vendor Advisor)
- Sets thresholds (GOALS healthcare threshold = 21/25)
- Adjusts build priority (Stack Builder healthcare sequence)

---

## Key Knowledge Base Files

| File | Content | Used By |
|------|---------|---------|
| `kb_INPACT_assessment_36_questions.md` | 36 questions with scoring rubrics, evidence sources, Echo baselines | INPACT Assessment |
| `kb_INPACT_scoring_rubrics.md` | Condensed scoring reference | INPACT Assessment, Trust Guide |
| `kb_stack_builder.md` | 7-layer gap analysis logic, budget estimates, build sequences | Stack Builder |
| `kb_vendor_advisor.md` | 90+ products with INPACT/GOALS scores, budget tiers, industry filters | Vendor Advisor |
| `kb_compliance_navigator.md` | 200+ regulatory frameworks, 30 categories, geographic mapping | Compliance Navigator |
| `kb_trust_guide.md` | Conversational knowledge base for framework Q&A | Trust Guide |
| `kb_trust_patterns.md` | Common trust patterns and anti-patterns | Trust Guide |
| `kb_context_types.md` | Seven context types for agent architecture | Trust Guide |

All knowledge base files are in: `tools/gpt_knowledge_bases/`
All web form specs are in: `tools/web_tools/`

---

## Implementation Priority

Recommended build order for the developer:

| Priority | Tool | Reason |
|----------|------|--------|
| 1 | **INPACT Assessment** | Entry point for most users, generates leads, provides baseline data |
| 2 | **GOALS Readiness Checker** | Complements INPACT, simple Yes/No format, quick to build |
| 3 | **Stack Builder** | Consumes INPACT gaps, visual and interactive |
| 4 | **Vendor Advisor** | Requires Stack Builder gaps as input, product database intensive |
| 5 | **90-Day Tracker** | Most complex (persistent state, team collaboration), consumes all other tool outputs |
| 6 | **Compliance Navigator** | Specialized, can be built in parallel |
| 7 | **Trust Guide** | Can be a ChatGPT custom GPT or embedded chat, lowest build effort |

---

## Open Items / Decisions Pending

1. **GOALS question reduction:** Considering reducing from 6 to 5 questions per dimension for cleaner 1:1 scoring (each Yes = 1 point). Would simplify scoring and make it more intuitive. Impact on Chapter 7 needs evaluation.

2. **Shared authentication:** Need to decide on user session management across tools (email-based linking vs. full auth system).

3. **Data persistence:** 90-Day Tracker requires cloud storage for ongoing tracking. Other tools can be stateless with PDF output.

4. **Mobile responsiveness:** All forms should work on tablet/mobile for workshop use.
