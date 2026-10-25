---
id: TASK-005
title: 1-Click Save with Context Sentence and Leitner Binary Flashcards
flow: FLOW-VOCAB-FLASHCARD
step_in_flow: Step 1 of 1 (Vocabulary Retention Slice)
assigned_to: frontend-dev
reviewer: tech-lead
status: BACKLOG
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/02_domain_vocab_flashcards/interface_vocab.md
  - docs/02_domain_vocab_flashcards/context_extraction.md
  - docs/02_domain_vocab_flashcards/spaced_repetition.md
outputs:
  - frontend/src/features/flashcards/pages/FlashcardsPage.tsx
  - frontend/src/features/reader/components/WordTooltip.tsx
dependencies:
  - FLOW-READER
---

# Task: [TASK-005] 1-Click Save with Context Sentence and Leitner Binary Flashcards

## 1. Flow Context
- **Target Flow**: FLOW-VOCAB-FLASHCARD (Main Experience Phase 1)
- **Position in Flow**: Direct follow-up to reader experience.
- **Previous Flow**: FLOW-READER.

## 2. Acceptance Criteria (Product Owner)
- [ ] 1-Click save on unfamiliar word inside reader automatically attaches the exact `context_sentence` from the current paragraph.
- [ ] 2-sided flashcard study view (Front: Word + Context sentence with blank; Back: Definition + IPA + Example).
- [ ] Binary self-evaluation buttons: Remembered (🟢) and Forgot (🔴) updating spaced repetition interval.

## 3. Technical Constraints (Tech Lead)
- Persist state to `user_vocab_progress` API and fallback gracefully to localStorage when offline.
