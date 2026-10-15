---
name: doc-write-srs-spec
description: Standardizes Software Requirements Specifications (SRS), functional requirements matrices, and business rules for VieCultures.
---

# Write SRS Specification

Creates structured SRS documentation files for VieCultures features.

## Directives
1. **File Location:** `document/03-product-spec/<feature>-srs.md` or feature sections in `screen-specs.md`.
2. **Template Structure:**
   ```markdown
   # SRS: [Feature Name] (e.g. Bilingual Reader & Shadowing Engine)

   ## 1. Feature Overview & Value Proposition
   Brief summary of business value, cultural storytelling importance, and target learner persona.

   ## 2. Functional Requirements (FR Matrix)
   | ID | Requirement | Priority | Business Rule / Validation |
   | :--- | :--- | :--- | :--- |
   | FR-01 | Bilingual Paragraph Display | High | 1:1 paragraph alignment between Vietnamese and English |
   | FR-02 | Synchronized Audio Playback | High | Highlight active paragraph during TTS audio playback |
   | FR-03 | Vocabulary Extraction | Medium | Click on cultural keywords to view meaning & add to flashcards |

   ## 3. Non-Functional Constraints
   - Audio latency: TTS stream / cache load < 300ms.
   - Mobile responsiveness: Touch-friendly audio scrub bar and typography legible on screens >= 375px.
   ```
