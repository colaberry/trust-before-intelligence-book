# GitHub Chapter Cleaning Codex

**Book:** Trust Before Intelligence  
**Purpose:** Standardized rules for converting draft chapters to GitHub-ready format  
**Version:** 1.0  
**Date:** December 2025

---

## Overview

This codex defines the consistent rules for cleaning chapter drafts before publishing to GitHub. These rules ensure uniformity across all chapters while maintaining GitHub compatibility and reader accessibility.

---

## Elements to REMOVE

| Element | Description | Reason |
|---------|-------------|--------|
| **Metadata block** | Book/Subtitle/Author/Publisher/Version/Date info at top of chapter | Belongs in front matter, not repeated in each chapter |
| **Reading time** | "Reading Time: X minutes" | Digital reader guidance, not needed for GitHub |
| **Target audience line** | "Target Audience: CDOs, CTOs..." | Front matter content |
| **Prerequisites line** | "Prerequisites: None" or similar | Front matter content |
| **HTML comments** | `<!-- COMMENT -->` markers | Invisible editing markers, not reader-facing |
| **Document classification footer** | "Document Classification: Final Draft" | Internal tracking metadata |
| **Word count tracking** | "Word Count: X,XXX words" | Internal tracking metadata |
| **Target/Status lines** | "Target: 5,000 words (±10%)" / "Status: ✅" | Internal tracking metadata |
| **End of chapter markers** | "END OF CHAPTER X" | Not standard in published books |

---

## Elements to KEEP

### Required Elements (Every Chapter)

| Element | Description | Reason |
|---------|-------------|--------|
| **Chapter title** | `# Chapter X: Title` | Primary heading |
| **Key Takeaway line** | Opening summary of chapter value | Reader orientation |
| **All narrative prose** | Body content | Core content |
| **References section** | Numbered citations with URLs | Academic credibility; links work on GitHub |
| **Acronyms section** | List of acronyms used in chapter | Standalone chapter readability |
| **Copyright/trademark notice** | "© 2025 Colaberry Inc..." | Legal protection |

### Optional Elements (If Present in Chapter)

| Element | Description | Reason |
|---------|-------------|--------|
| **Figure captions** | "Figure X.X: Description" | Image/diagram context |
| **Block quotes** | `> Quote text` | Emphasis and callouts |
| **Call-to-action URLs** | Assessment links, resources, tools | Will have QR codes in print; functional on GitHub |
| **Mermaid code blocks** | ````mermaid ... ``` | Renders natively on GitHub |
| **Disclaimer notes** | "Note: [Case study] is fictional..." | Reader transparency; include where case studies are introduced |
| **Tables** | Data presentation | Renders correctly on GitHub |
| **Code examples** | Technical demonstrations | Renders correctly on GitHub |
| **Checkpoint sections** | Progress markers with summaries, reading time, quick checks | Reader navigation and engagement |

---

## Elements to TRANSFORM

| Element | Action |
|---------|--------|
| **Horizontal rules (`---`)** | Keep as-is; provides section breaks |
| **Bold/italic formatting** | Keep as-is; renders correctly on GitHub |
| **Numbered lists** | Keep as-is |
| **Bullet lists** | Keep as-is |
| **Code blocks** | Keep as-is |
| **Tables** | Keep as-is; GitHub renders markdown tables |

---

## File Naming Convention

| Type | Pattern | Example |
|------|---------|---------|
| Front matter | `00_front_matter.md` | `00_front_matter.md` |
| Chapters | `XX_chapter_Y_short_title.md` | `01_chapter_0_trust_before_intelligence.md` |
| Back matter | `15_back_matter.md` | `15_back_matter.md` |
| Glossary | `16_glossary.md` | `16_glossary.md` |

**Numbering notes:**
- File prefix (`XX_`) determines sort order in GitHub
- Chapter number (`Y`) matches book chapter number
- Use underscores, not spaces or hyphens
- Use lowercase for file names

---

## Chapter Structure Template

```markdown
# Chapter X: Chapter Title

**Key Takeaway:** One-sentence summary of chapter value

---

<!-- OPTIONAL: Opening graphic/diagram if applicable -->

<!-- OPTIONAL: Opening quote or hook -->
> **Key Takeaway:** "Quote text" — Attribution

## First Major Section

[Content...]

---

## Second Major Section

[Content...]

<!-- OPTIONAL: Additional sections as needed -->

---

## References

[1] Citation...

[2] Citation...

---

## Acronyms

- **ABC:** Full Name
- **DEF:** Full Name

---

**© 2025 Colaberry Inc. All Rights Reserved.**  
INPACT™ and GOALS™ are trademarks of Colaberry Inc.
```

**Template Notes:**
- Items marked `<!-- OPTIONAL -->` should be included only if present in the source chapter
- Not all chapters will have diagrams, quotes, or CTAs
- Acronyms section should only include acronyms actually used in that chapter
- References should only include sources actually cited in that chapter

---

## Quality Checklist

Before finalizing a chapter for GitHub, verify:

### Removals (All Chapters)
- [ ] Metadata block removed (except Key Takeaway)
- [ ] HTML comments removed
- [ ] Document classification footer removed
- [ ] Word count/target/status lines removed
- [ ] "END OF CHAPTER" marker removed

### Required Elements (All Chapters)
- [ ] Chapter title present (`# Chapter X: Title`)
- [ ] Key Takeaway line retained
- [ ] References section complete with working URLs
- [ ] Acronyms section present (only acronyms used in this chapter)
- [ ] Copyright/trademark notice at end
- [ ] File named according to convention

### Optional Elements (If Present in Source)
- [ ] Mermaid diagrams intact and properly formatted
- [ ] Figure captions retained
- [ ] Call-to-action URLs retained
- [ ] Block quotes retained
- [ ] Disclaimer notes retained (for case study introductions)
- [ ] Tables properly formatted
- [ ] Checkpoint sections retained (progress markers, reading time, quick checks)

### Final Checks
- [ ] No trailing whitespace or extra blank lines at end
- [ ] All internal links working (if any)
- [ ] Consistent heading hierarchy (##, ###, etc.)

---

## Glossary Integration

Each chapter's Acronyms section should be:

1. **Kept in the chapter** — For standalone readability on GitHub
2. **Consolidated into `16_glossary.md`** — With expanded definitions for the complete book

When adding new acronyms:
- Add to the chapter's Acronyms section (brief format: `- **ABC:** Full Name`)
- Add to Glossary (expanded format with definition paragraph)

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.1 | December 2025 | Added Checkpoint sections to optional elements to keep |
| 1.0 | December 2025 | Initial codex based on Chapter 0 cleanup decisions |

---

**© 2025 Colaberry Inc. All Rights Reserved.**
