---
name: doc-write-use-cases
description: Formats Use Case specifications with actor matrices, preconditions, main flows, and alternative/exception flows for VieCultures.
---

# Write Use Case Specifications

Creates granular Use Case specifications for VieCultures modules (Learner Portal, Admin CMS, Playground).

## Directives
1. **File Location:** `document/03-product-spec/<feature>-use-cases.md` or within `02-business-rules/`.
2. **Template Structure:**
   ```markdown
   # Use Case: UC-[ID] [Use Case Title] (e.g. UC-01 Study Reading Post with Synchronized Audio)

   * **Primary Actor:** Learner (Registered / Guest)
   * **Preconditions:** Reading post is published and active; audio tracks generated.
   * **Postconditions:** Reading progress tracked; new vocabulary items recorded in study session.

   ### Main Success Scenario
   1. User navigates to `/reader/:id`.
   2. System loads bilingual paragraphs and pre-fetches Azure/Gemini TTS audio track.
   3. User presses Play button.
   4. Audio plays while current paragraph is highlighted in real-time.
   5. User clicks on a bold cultural vocabulary item.
   6. System opens vocabulary modal showing definition, IPA, example sentence, and cultural context.
   7. User clicks "Add to Flashcards".
   8. System persists card into user's spaced repetition deck.

   ### Alternative & Exception Flows
   * **3a. Audio Unavailable / Network Error:** System displays a fallback badge and offers native Web Speech API synthesis.
   * **6a. Offline Mode:** System loads cached definition from IndexedDB/localStorage.
   ```
