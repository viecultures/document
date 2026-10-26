---
id: TASK-009
title: Community Reflections REST API and PostgreSQL Persistence
flow: FLOW-BACKEND-PERSISTENCE
step_in_flow: Step 1 of 2 (Community UGC Persistence)
assigned_to: backend-dev
reviewer: tech-lead
status: DONE
created_at: 2026-10-26
updated_at: 2026-10-26
inputs:
  - document/06_domain_community/interface_community.md
  - document/06_domain_community/reflections_moderation.md
  - backend/src/main/java/com/viecultures/backend/entity/UserReflection.java
outputs:
  - backend/src/main/java/com/viecultures/backend/controller/UserReflectionController.java
  - backend/src/main/java/com/viecultures/backend/service/UserReflectionService.java
  - backend/src/main/java/com/viecultures/backend/entity/UserReflectionReaction.java
dependencies:
  - FLOW-COMMUNITY
---

# Task: [TASK-009] Community Reflections REST API and PostgreSQL Persistence

## 1. Flow Context
- **Target Flow**: FLOW-BACKEND-PERSISTENCE (Milestone 2 Priority #1)
- **Position in Flow**: Step 1 of 2
- **Previous Flow**: FLOW-COMMUNITY (TASK-008)

## 2. Acceptance Criteria (Product Owner)
- [x] Implement `UserReflectionController` with REST endpoints:
  - `GET /api/reflections?postId={postId}`: Query reflections by post ID (Strict Auth - Bearer JWT).
  - `POST /api/reflections`: Create a reflection linked to authenticated `user_id` and `post_id`.
  - `POST /api/reflections/{id}/react`: Idempotent like/unlike toggle via `user_reflection_reactions` relation table.
  - `POST /api/reflections/{id}/report`: Flag inappropriate reflection for passive moderation.
- [x] Enforce Strict Auth: Require valid JWT token in Authorization header for all reflection endpoints.
- [x] Enforce No-Judgment Policy: Backend never scores or rejects grammar/spelling errors.

## 3. Technical Constraints (Tech Lead)
- [x] Use `UserReflectionReaction` entity with unique composite constraint on `(user_id, reflection_id)`.
- [x] Synchronize `reactions_count` atomically on the parent `UserReflection` record.
- [x] Return standardized ApiResponse envelope.
