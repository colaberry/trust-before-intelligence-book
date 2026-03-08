# GOALS Readiness Checker
## Tool Specification

**Purpose:** Interactive 30-question assessment to evaluate organization's operational readiness for sustaining AI agent deployments.
**URL:** trustbeforeintelligence.ai/goals-assessment
**Source:** Chapter 7 Self-Assessment Checklist (lines 1734-1788)
---

## Relationship to INPACT Assessment

| Aspect | INPACT Assessment | GOALS Readiness Checker |
|--------|-------------------|--------------------------|
| **Measures** | Infrastructure capability | Operational sustainability |
| **When Used** | BEFORE transformation | DURING/AFTER transformation |
| **Question** | "Can we support agents?" | "Can we sustain agent operations?" |
| **Score Range** | 0-100% (6-36 raw) | 0-100% (5-25 raw) |
| **Threshold** | 86% for production | 84% (21/25) for healthcare |
| **Chapter** | Chapter 2 (+ Chapter 9) | Chapter 7 |

**Key Insight:** INPACT measures whether you CAN deploy agents. GOALS measures whether you can SUSTAIN them.

---

## User Flow

1. **Landing page** with value proposition:
   - "Evaluate your operational readiness in 10 minutes"
   - "Complement your INPACT score with operational sustainability assessment"

2. **Lead capture:** User enters email, name, company, role

3. **Context selection:**
   - Industry (healthcare, financial services, manufacturing, other)
   - Current stage (pre-deployment, pilot, production)
   - If healthcare: additional compliance context

4. **30 questions** (6 per GOALS dimension) - Yes/No format

5. **Real-time score calculation**

6. **PDF report generation** with:
   - Overall GOALS score (X/25 = X%)
   - Dimension breakdown radar chart
   - Readiness band classification
   - Gap analysis with recommended actions
   - Comparison to Echo Health (15/25 → 21/25)
   - Healthcare threshold compliance check
   - Next steps based on score

---

## Questions (Synced with Chapter 7, Lines 1740-1781)

### G - Governance (6 Questions)

| # | Question | Book Reference |
|---|----------|----------------|
| G1 | Do your AI agents have context-aware access controls that consider factors like user role, time, and purpose when deciding what data the agent can access? (ABAC = Attribute-Based Access Control, evaluated in under 10ms) | Line 1741 |
| G2 | Is every piece of data your AI agents access fully logged, including why it was accessed and by whom? | Line 1742 |
| G3 | Are Human-in-the-Loop (HITL) workflows defined so that a human reviews high-risk agent decisions before they take effect? | Line 1743 |
| G4 | Can you track which version of an AI model is running and quickly revert to a previous version if something goes wrong? | Line 1744 |
| G5 | Have you assessed AI-specific security threats, such as attempts to manipulate agent behavior through malicious inputs or corrupted training data? | Line 1745 |
| G6 | Is your compliance mapping documented for applicable regulations (e.g., HIPAA, EU AI Act, SOX, GDPR)? | Line 1746 |

### O - Observability (6 Questions)

| # | Question | Book Reference |
|---|----------|----------------|
| O1 | Can you monitor the performance and health of all services that support your AI agents in real time? (APM = Application Performance Monitoring) | Line 1750 |
| O2 | Can you follow an agent's request end-to-end across all systems to see exactly what happened at each step? (using unique trace IDs that link all related events) | Line 1751 |
| O3 | Can you track how much each AI query costs and attribute those costs to specific users, departments, or use cases? (LLM = Large Language Model) | Line 1752 |
| O4 | When something goes wrong with your AI agents, how quickly is it detected? Is your Mean Time to Detection (MTTD) under 10 minutes? | Line 1753 |
| O5 | Is drift detection automated, so you're alerted when AI model accuracy degrades because the real world has changed but the model hasn't been updated? | Line 1754 |
| O6 | Can your AI agents explain their reasoning for high-risk decisions in terms that business users and regulators understand? | Line 1755 |

### A - Availability (6 Questions)

| # | Question | Book Reference |
|---|----------|----------------|
| A1 | Do 95% of AI agent responses complete in under 2 seconds? (p95 = the response time that 95% of requests complete within) | Line 1759 |
| A2 | Is the data your agents use updated within 30 seconds of changes occurring in source systems, for at least 95% of critical data? | Line 1760 |
| A3 | Are at least 60% of agent queries served from cache (previously computed results) rather than recomputed from scratch? | Line 1761 |
| A4 | Is your AI agent infrastructure available 99.9%+ of the time (less than 9 hours of downtime per year)? | Line 1762 |
| A5 | Has your system been tested to handle 10 times your current workload without performance degradation? | Line 1763 |
| A6 | When an agent needs data from multiple systems, can it retrieve from all of them simultaneously (in parallel) rather than one at a time? | Line 1764 |

### L - Lexicon (6 Questions)

| # | Question | Book Reference |
|---|----------|----------------|
| L1 | Can your system correctly match the same entity (e.g., customer, product, employee) across different systems at least 95% of the time? | Line 1768 |
| L2 | Does your business glossary cover 80%+ of the terms used in your domain, so agents understand your organization's language? | Line 1769 |
| L3 | When the agent isn't confident it understood a question correctly (below 90% confidence), does it ask the user a clarifying question rather than guessing? | Line 1770 |
| L4 | Does your system learn and improve when users correct agent mistakes? | Line 1771 |
| L5 | Have you documented how the same concept is named differently across departments or systems? (e.g., "customer" in sales vs. "member" in support vs. "account holder" in billing) | Line 1772 |
| L6 | Does a human review a sample of at least 100 agent responses each week to check for quality and accuracy? | Line 1773 |

### S - Solid (6 Questions)

| # | Question | Book Reference |
|---|----------|----------------|
| S1 | Is the data your agents rely on accurate at least 95% of the time, based on regular validation? | Line 1777 |
| S2 | Are at least 98% of critical data fields filled in (not blank or missing) across your key systems? | Line 1778 |
| S3 | When the same data exists in multiple systems, does it match at least 95% of the time? | Line 1779 |
| S4 | Is data structure validation enforced so that all incoming data is checked for correct format before being accepted? | Line 1780 |
| S5 | Are data quality checks applied at three stages: when data enters the system, when it's processed, and before it reaches the AI agent? | Line 1781 |
| S6 | Does your system automatically detect and flag unusual data patterns that could indicate errors or quality issues? | Line 1782 |

---

## Score Calculation (Book-Consistent)

### Per-Dimension Scoring (from Chapter 7, Lines 1784-1788)

```
Yes answers per dimension → Dimension score:
- 0-2 Yes: Score 2/5
- 3 Yes:   Score 3/5
- 4-5 Yes: Score 4/5
- 6 Yes:   Score 5/5
```

### Total Score Calculation

```
Total GOALS Score = G + O + A + L + S (range: 5-25)
Percentage = (Total / 25) × 100 = 20-100%

PRIMARY DISPLAY: "Your GOALS Score: X/25 (Y%)"
```

### Readiness Bands

| Score | Percentage | Readiness Band | Interpretation |
|-------|------------|----------------|----------------|
| 23-25 | 92-100% | 🟢 **Excellent** | Production-ready, continuous improvement mode |
| 21-22 | 84-88% | 🟢 **Healthcare Ready** | Meets healthcare threshold (21/25) |
| 18-20 | 72-80% | 🟡 **Good** | Minor gaps, targeted improvements needed |
| 14-17 | 56-68% | 🟠 **Moderate** | Significant gaps, not production-ready |
| 10-13 | 40-52% | 🔴 **Low** | Major operational gaps |
| 5-9 | 20-36% | ⚫ **Critical** | Operational foundation missing |

---

## Healthcare Threshold Check (from Chapter 7, Lines 1714-1721)

For healthcare deployments, the report includes a specific threshold compliance check:

| Dimension | Minimum Required | User Score | Status |
|-----------|------------------|------------|--------|
| Governance | 5/5 | [calculated] | ✅/❌ |
| Observability | 4/5 | [calculated] | ✅/❌ |
| Availability | 4/5 | [calculated] | ✅/❌ |
| Lexicon | 4/5 | [calculated] | ✅/❌ |
| Solid | 4/5 | [calculated] | ✅/❌ |
| **Total** | **21/25** | [calculated] | ✅/❌ |

**Healthcare Production Gate:** All dimensions must meet minimums AND total must be ≥21/25.

---

## Echo Health Comparison (from Chapter 7, Lines 403-410)

PDF report includes comparison to Echo's journey:

| GOAL | Echo Week 10 (Baseline) | Echo Week 12 (Target) | Your Score |
|------|-------------------------|----------------------|------------|
| G - Governance | 3/5 | 5/5 | [calculated] |
| O - Observability | 3/5 | 4/5 | [calculated] |
| A - Availability | 4/5 | 4/5 | [calculated] |
| L - Lexicon | 2/5 | 4/5 | [calculated] |
| S - Solid | 3/5 | 4/5 | [calculated] |
| **Total** | **15/25 (60%)** | **21/25 (84%)** | [calculated] |

---

## PDF Report Sections

1. **Executive Summary**
   - Overall GOALS score with readiness band
   - Healthcare threshold compliance (if applicable)
   - One-sentence assessment

2. **Dimension Breakdown**
   - Radar chart (5 axes)
   - Score per dimension with interpretation
   - Gap identification (dimensions below 4/5)

3. **Healthcare Compliance Check** (if healthcare selected)
   - Threshold table with pass/fail per dimension
   - Specific gaps blocking production deployment

4. **Echo Health Comparison**
   - Side-by-side with Echo's Week 10 baseline
   - Side-by-side with Echo's Week 12 target
   - "You are X points ahead/behind Echo's baseline"

5. **Recommended Actions**
   - Priority improvements by dimension
   - Chapter references for each gap:
     - Governance gaps → Chapter 7, Part 3
     - Observability gaps → Chapter 7, Part 4
     - Availability gaps → Chapter 7, Part 5
     - Lexicon gaps → Chapter 7, Part 6
     - Solid gaps → Chapter 7, Part 7

6. **Next Steps**
   - Based on score band, recommend:
     - 🟢 Excellent/Healthcare Ready: "Focus on continuous improvement. Use 90-Day Tracker."
     - 🟡 Good: "Target specific gaps. Review Chapter 7 for improvement strategies."
     - 🟠 Moderate: "Address operational foundations before scaling. Start with lowest-scoring dimension."
     - 🔴/⚫ Low/Critical: "Operational infrastructure needs significant work. Review Chapter 7 comprehensively."

---

## Integration with Other Tools

| Tool | Integration |
|------|-------------|
| **INPACT Assessment** | "You've assessed capability (INPACT). Now assess sustainability (GOALS)." |
| **90-Day Tracker** | GOALS scores feed into Tab 3 (GOALS Tracking) |
| **Compliance Navigator** | Deep dive on regulatory requirements per dimension |

---

## Technical Implementation Notes

### Form Structure
- Single-page progressive form (similar to INPACT Assessment)
- 5 sections (one per GOALS dimension)
- Yes/No radio buttons for each question
- Progress indicator showing completion

### Lead Capture Fields
- Email (required)
- Name (required)
- Company (required)
- Role (optional)
- Industry (required - determines threshold display)
- Current deployment stage (optional)

### Output Formats
- Interactive results page (immediate)
- PDF download (generated)
- Email delivery (optional)

---

## Book Sync Verification Checklist

- [x] 30 questions match Chapter 7 Self-Assessment Checklist exactly
- [x] Scoring formula matches Chapter 7 (lines 1783-1787)
- [x] Healthcare thresholds match Chapter 7 (lines 1714-1721)
- [x] Echo comparison matches Chapter 7 (lines 403-410)
- [x] GOALS acronym consistent (Governance, Observability, Availability, Lexicon, Solid)
- [x] Chapter references accurate for gap remediation

---

## Changelog

| Date | Change | Author |
|------|--------|--------|
| Feb 4, 2026 | Initial specification created | Editorial session |

