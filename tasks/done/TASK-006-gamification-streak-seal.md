---
id: TASK-006
title: Daily Streak Tracking and Red Seal (Mộc Son) Activation Ritual
flow: FLOW-GAMIFICATION
step_in_flow: Step 1 of 1 (Retention & Habit Loop)
assigned_to: frontend-dev
reviewer: tech-lead
status: DONE
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/05_domain_gamification/interface_gamification.md
  - docs/05_domain_gamification/habit_tracking.md
  - docs/00_core/interface_learning_loop.md
outputs:
  - frontend/src/features/gamification/components/MocSonSealModal.tsx
  - frontend/src/features/gamification/components/StreakBadge.tsx
dependencies:
  - FLOW-VOCAB-FLASHCARD
---

# Task: [TASK-006] Daily Streak Tracking and Red Seal (Mộc Son) Activation Ritual

## 1. Flow Context
- **Target Flow**: FLOW-GAMIFICATION (Main Experience Phase 2 - Conversion Gateway)
- **Position in Flow**: Post-flashcard completion ritual.
- **Previous Flow**: FLOW-VOCAB-FLASHCARD.

## 2. Acceptance Criteria (Product Owner)
- [x] Upon completing reader or flashcard study, trigger the cultural Red Seal ("Mộc Son Đỏ") stamping animation.
- [x] Increment and display continuous Daily Streak counter (Day 1, Day 2...).
- [x] Non-authenticated users are prompted to register/login to preserve their seal and streak history.

## 3. Technical Constraints (Tech Lead)
- High-fidelity cultural visual styling matching the Warm Heritage aesthetic.
