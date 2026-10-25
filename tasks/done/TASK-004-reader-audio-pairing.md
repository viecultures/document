---
id: TASK-004
title: Bilingual Reader Paragraph Pairing and Sticky Audio Player Speeds
flow: FLOW-READER
step_in_flow: Step 1 of 1 (Core Reader Experience)
assigned_to: frontend-dev
reviewer: tech-lead
status: DONE
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/01_domain_reader/interface_reader.md
  - docs/01_domain_reader/paragraph_pairing.md
  - docs/00_core/system_constants.md
outputs:
  - frontend/src/features/reader/components/StickyAudioPlayer.tsx
  - frontend/src/features/reader/components/BilingualParagraphPairList.tsx
  - frontend/src/features/reader/pages/ReaderPage.tsx
dependencies:
  - FLOW-AI-COMPANION
---

# Task: [TASK-004] Bilingual Reader Paragraph Pairing and Sticky Audio Player Speeds

## 1. Flow Context
- **Target Flow**: FLOW-READER (Main Experience Phase 1)
- **Position in Flow**: Post-Chatbox core flow.
- **Previous Flow**: FLOW-AI-COMPANION (Completed).

## 2. Acceptance Criteria (Product Owner)
- [x] Render 1:1 bilingual paragraph pairing with English on left/primary and Vietnamese translation on right/accordion.
- [x] Sticky bottom audio player with speed controls: `1.0x`, `0.8x`, and `0.5x` as mandated by `system_constants.md`.
- [x] Active paragraph highlight syncing with current audio playback timestamp.

## 3. Technical Constraints (Tech Lead)
- Use standard HTML5 Audio element or Web Audio API without memory leaks.
- Ensure smooth mobile responsiveness and touch target compliance.

## 4. Verification Evidence (QA / Engineering)
- Build Verification: `npm run build` (`check:palette && tsc -b && vite build`) passed with exit code 0.
- Unit Tests: `tsx --test src/features/reader/constants.test.ts` passed (5/5 tests).
- Regression Suites: `test:learning`, `test:shadowing`, `test:integration`, `readerPractice.test.ts` all passed (73/73 tests).
- Branch Protection & Remote Sync: Committed (`feat(reader): add 1:1 bilingual paragraph pairing and sticky audio player with SSOT speeds`) and pushed to `origin cuong`.
