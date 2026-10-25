---
id: TASK-010
title: Gamification Streak and Cultural Red Seal REST API Persistence
flow: FLOW-BACKEND-PERSISTENCE
step_in_flow: Step 2 of 2 (Gamification & Habit Persistence)
assigned_to: backend-dev
reviewer: tech-lead
status: READY
created_at: 2026-10-26
updated_at: 2026-10-26
inputs:
  - document/05_domain_gamification/interface_gamification.md
  - document/05_domain_gamification/habit_tracking.md
  - frontend/src/features/gamification/services/streakService.ts
outputs:
  - backend/src/main/java/com/viecultures/backend/entity/UserStreak.java
  - backend/src/main/java/com/viecultures/backend/entity/UserSeal.java
  - backend/src/main/java/com/viecultures/backend/controller/StreakController.java
  - backend/src/main/java/com/viecultures/backend/service/StreakService.java
dependencies:
  - FLOW-GAMIFICATION
---

# Task: [TASK-010] Gamification Streak and Cultural Red Seal REST API Persistence

## 1. Flow Context
- **Target Flow**: FLOW-BACKEND-PERSISTENCE (Milestone 2 Priority #1)
- **Position in Flow**: Step 2 of 2
- **Previous Flow**: FLOW-GAMIFICATION (TASK-006)

## 2. Acceptance Criteria (Product Owner)
- [ ] Create `UserStreak` entity:
  - Fields: `id`, `user_id`, `streak_days`, `last_active_date` (LocalDate), `streak_protected`, `streak_freeze_count`, `updated_at`.
- [ ] Create `UserSeal` entity:
  - Fields: `id`, `user_id`, `reading_post_id`, `sealed_at` (LocalDateTime), `words_learned_count`, `source` (reader, flashcards).
- [ ] Implement `StreakController` endpoints (Strict Auth - Bearer JWT):
  - `GET /api/user/streak`: Fetch authenticated user's current streak state and available freeze protections.
  - `POST /api/user/streak/sync`: Evaluate and increment streak daily using calendar day difference logic.
  - `POST /api/user/streak/seal`: Persist Mộc Son Red Seal stamp for completed lesson and trigger streak activation.
- [ ] Enforce Strict Auth: All streak and seal mutations require authenticated user session.

## 3. Technical Constraints (Tech Lead)
- [ ] Prevent duplicate seal records for the same user, reading post, and calendar day.
- [ ] Streak calculation must match `streakService.ts` specification (habit_tracking.md).
