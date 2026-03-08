# Chapter Cleaning Codex v1.1

**Standard Operating Procedure for Book Chapter Cleanup**

---

## Purpose

This codex provides a systematic approach to cleaning book chapters for publication. It ensures consistency across all chapters, removes draft artifacts, and validates required elements are present and properly formatted.

---

## Pre-Cleanup Checklist

Before making any changes, analyze the chapter for:

1. **Metadata to remove** (version numbers, draft markers, HTML comments)
2. **Figure numbering** (chapter-prefixed format: Figure X.0, X.1, X.2...)
3. **Required sections** (checkpoints, acronyms, references, copyright)
4. **Unicode issues** (control characters, encoding problems)
5. **Formatting issues** (duplicate horizontal rules, spacing)

---

## Elements to REMOVE

### 1. Version Metadata
Remove any version/draft markers from the chapter header:
```
❌ **Version 1.3 — Corrected December 2025**
❌ **Draft v2.1 — November 2025**
❌ v1.0, v1.1, v2.0 in title area
```

### 2. HTML Comments
Remove all HTML comments:
```
❌ <!-- CHAPTER OPENING GRAPHIC -->
❌ <!-- END CHAPTER OPENING GRAPHIC -->
❌ <!-- TODO: Add diagram -->
❌ <!-- REVIEW: Check this section -->
```

### 3. End-of-Chapter Markers
Remove working markers not intended for publication:
```
❌ <!-- END OF CHAPTER -->
❌ **END OF CHAPTER 10**
❌ [END]
```

### 4. Word Count Metadata
Remove working word counts:
```
❌ **END OF PART 6** (~1,400 words)
❌ Word count: 8,500
❌ (~500 words)
```

### 5. Duplicate Horizontal Rules
Remove consecutive `---` markers:
```
❌ ---
  
  ---
  
✅ ---
```

---

## Elements to KEEP (Required)

### 1. Chapter Header Structure
```markdown
# Chapter X: [Title]

**[Subtitle — Description]**

---
```

### 2. Opening Figure with Key Takeaway
Every chapter should have an opening figure followed by a Key Takeaway:
```markdown
**Figure X.0: [Descriptive Title]**

\`\`\`mermaid
[diagram code]
\`\`\`

> **Key Takeaway:** [One-sentence summary]
```

### 3. Introduction Paragraph
Italicized paragraph after the opening figure providing chapter context:
```markdown
*[Introduction text explaining what the chapter covers and how it connects to previous chapters...]*
```

### 4. Checkpoint Sections
Use the 🔍 CHECKPOINT format consistently:
```markdown
**🔍 CHECKPOINT: What We've Covered So Far**

✅ [Point 1]  
✅ [Point 2]  
✅ [Point 3]  
⭐️ **Next:** [Preview of next section]

**Reading Time Remaining:** ~XX minutes

**Your Framework Quick Check:** [Engagement question]
```

### 5. Chapter Summary Table
Near the end of each chapter:
```markdown
## Chapter Summary

| Part | Content | Key Takeaway |
|------|---------|--------------|
| **Part 1** | [Topic] | [Key point] |
| **Part 2** | [Topic] | [Key point] |
...
```

### 6. References Section (if applicable)
```markdown
## References

[1] Author. (Year). "Title." Source. URL (Accessed Month Year)

[2] ...
```

### 7. Acronym Reference Section
```markdown
## Acronyms

| Acronym | Definition |
|---------|------------|
| ABAC | Attribute-Based Access Control |
| CDC | Change Data Capture |
...
```

**Or bullet format:**
```markdown
## Acronyms

- **ABAC**: Attribute-Based Access Control
- **CDC**: Change Data Capture
...
```

### 8. Copyright Notice (Final Element)
```markdown
---

**© 2025 Colaberry Inc. All Rights Reserved.**  
INPACT™ and GOALS™ are trademarks of Colaberry Inc.
```

---

## Figure Numbering Rules

### Chapter-Prefixed Numbering (Figure X.Y Format)

All figures use chapter-prefixed numbering for cross-reference clarity:

```
✅ Figure 0.0, Figure 0.1, Figure 0.2 (Chapter 0)
✅ Figure 1.0, Figure 1.1, Figure 1.2 (Chapter 1)
✅ Figure 5.0, Figure 5.1, Figure 5.2 (Chapter 5)
...

❌ Diagram 1, Diagram 2, Diagram 3 (no chapter prefix)
❌ Figure 1, Figure 2, Figure 3 (no chapter prefix)
❌ Figure 5.1, Figure 5.3, Figure 5.2 (out of order)
❌ Figure 5a, Figure 5b (sub-letters)
❌ Figure: [Title] (missing number)
```

**Why Figure X.Y format?**
- **Chapter differentiation** — "Figure 3.2" immediately identifies Chapter 3
- **Cross-referencing** — Readers can locate figures across chapters unambiguously
- **Professional standard** — Matches technical and business book conventions
- **Future-proofing** — References from other chapters remain clear

### Figure Label Format
```markdown
**Figure X.Y: [Descriptive Title]**

\`\`\`mermaid
[diagram code]
\`\`\`
```

### Opening Graphic
The opening chapter graphic is Figure X.0 and should be labeled:
```markdown
**Figure X.0: [Value Proposition Title] — From [Before State] to [After State]**
```

**Examples by chapter:**
- Chapter 0: `**Figure 0.0: Echo Health Transformation—From Failed Pilots to Production Success**`
- Chapter 1: `**Figure 1.0: The Infrastructure Gap—Why 95% of Agent Projects Fail**`
- Chapter 5: `**Figure 5.0: Layer 4 Intelligence—From Raw Data to Grounded Responses**`

---

## Unicode Validation

### Acceptable Characters
- Standard ASCII (U+0000 to U+007F)
- Em dash: — (U+2014)
- Trademark: ™ (U+2122)
- Copyright: © (U+00A9)
- Arrows: → ← ↓ ↑ (U+2190-U+2193)
- Check marks: ✅ (U+2705)
- Stars: ⭐ (U+2B50)
- Circles: 🔴 🟡 🟢 ⚫ (U+1F534, U+1F7E1, U+1F7E2, U+26AB)
- Magnifying glass: 🔍 (U+1F50D)
- Math symbols: × ÷ ± ≥ ≤ (U+00D7, U+00F7, U+00B1, U+2265, U+2264)
- Box drawing: ─ │ └ ├ (U+2500, U+2502, U+2514, U+251C)

### Characters to Fix
- Mojibake (encoding errors): â€" â€™ â€œ → Replace with correct characters
- Control characters (U+0080-U+009F): Remove or replace
- Curly quotes if inconsistent: Standardize to straight quotes or curly throughout

---

## Acronym Management

### Chapter-Level Acronyms
Each chapter should have an Acronym Reference section listing all acronyms used in that chapter.

### Master Glossary Updates
After cleaning each chapter, verify all chapter acronyms exist in the master glossary (16_glossary.md). Add any missing acronyms in alphabetical order.

### Acronym Definition Format
```markdown
- **ACRONYM:** Full Name — Description explaining what it is and why it matters.
```

---

## Quality Validation Checklist

Run these checks after cleanup:

### Structure Checks
- [ ] Chapter title present (# Chapter X: Title)
- [ ] Subtitle present (**The [Description] Chapter**)
- [ ] Opening figure labeled as Figure X.0
- [ ] Key Takeaway present after opening figure
- [ ] Introduction paragraph (italicized) present
- [ ] All figures numbered sequentially (X.0, X.1, X.2...)
- [ ] Checkpoint sections use 🔍 CHECKPOINT format
- [ ] Chapter Summary table present
- [ ] Acronym Reference section present
- [ ] Copyright notice is final element

### Removal Checks
- [ ] No version metadata in header
- [ ] No HTML comments remaining
- [ ] No end-of-chapter markers
- [ ] No duplicate horizontal rules
- [ ] No word count annotations

### Formatting Checks
- [ ] Single blank line before lists
- [ ] Single blank line after headings
- [ ] Consistent table formatting
- [ ] No trailing whitespace on lines

### Cross-Reference Checks
- [ ] All chapter acronyms in master glossary
- [ ] Figure numbers use chapter prefix (Figure X.Y format)
- [ ] Budget numbers consistent with canonical values (if applicable)

---

## Canonical Budget Values

For chapters referencing Echo Health Systems transformation costs:

| Phase | Weeks | Budgeted | Actual |
|-------|-------|----------|--------|
| Phase 1: Foundation | 1-4 | $470K | $468K |
| Phase 2: Intelligence | 5-7 | $380K | $392K |
| Phase 3: Trust | 8-10 | $380K | $82K |
| Phase 4: Operations | 11-12 | — | $50K |
| **Total** | **12** | **$1.23M** | **$992K** |

**Key narrative points:**
- 19% under budget ($238K buffer preserved)
- Phase 3 savings from open-source OPA, infrastructure reuse, agent retrofitting
- INPACT™ journey: 28 → 89 (+61 points)

---

## Command Reference

### Find HTML Comments
```bash
grep -n "<!--" [filename].md
```

### Find Figure Labels
```bash
grep -n "^\*\*Figure" [filename].md
```

### Find Duplicate Horizontal Rules
```bash
grep -n "^\-\-\-$" [filename].md | tail -10
```

### Check Unicode Characters
```python
python3 -c "
import re
with open('[filename].md', 'r', encoding='utf-8') as f:
    content = f.read()
    non_ascii = set(re.findall(r'[^\x00-\x7F]', content))
    print('Non-ASCII characters:')
    for char in sorted(non_ascii, key=ord):
        print(f'  {repr(char)} (U+{ord(char):04X}): {char}')
"
```

### Count Acronyms in Glossary
```bash
grep -c "^\- \*\*" 16_glossary.md
```

### Verify Acronym in Glossary
```bash
grep "^\- \*\*ACRONYM" 16_glossary.md
```

---

## Cleanup Workflow

### Step 1: Analysis
1. View chapter beginning (lines 1-50)
2. Search for metadata, HTML comments, figures
3. View chapter ending (last 50 lines)
4. Check unicode characters
5. Document all findings

### Step 2: Present Plan
Create a cleanup plan table for approval:

| # | Location | Change |
|---|----------|--------|
| 1 | Line X | Remove [element] |
| 2 | Line Y | Rename Figure N to Figure X.Y |
| ... | ... | ... |

### Step 3: Execute (After Approval)
1. Copy file to working directory
2. Apply changes using str_replace
3. Verify each change
4. Run quality validation checks

### Step 4: Finalize
1. Copy to outputs directory
2. Present file to user
3. Update master glossary if needed
4. Document changes made

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | December 2025 | Initial codex based on Chapters 5-12 cleanup patterns |
| 1.1 | December 2025 | Changed from "Diagram 1, 2, 3" to "Figure X.Y" chapter-prefixed format for cross-reference clarity |

---

**© 2025 Colaberry Inc. All Rights Reserved.**  
INPACT™ and GOALS™ are trademarks of Colaberry Inc.
