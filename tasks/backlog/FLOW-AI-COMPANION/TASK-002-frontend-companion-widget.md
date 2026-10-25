---
id: TASK-002
title: Build Frontend AI Companion Chat Widget and Client Service
flow: FLOW-AI-COMPANION
step_in_flow: Step 2 of 3 (Frontend Interactive Chat Drawer)
assigned_to: frontend-dev
reviewer: tech-lead
status: BLOCKED
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/03_domain_ai_companion/conversational_flows.md
  - docs/03_domain_ai_companion/context_retrieval_chat.md
  - docs/tasks/backlog/FLOW-AI-COMPANION/TASK-001-backend-companion-chat.md
outputs:
  - frontend/src/services/companionService.ts
  - frontend/src/types/companion.ts
  - frontend/src/features/companion/CompanionChatDrawer.tsx
  - frontend/src/features/companion/CompanionQuickPrompts.tsx
  - frontend/src/features/companion/CompanionFloatingButton.tsx
  - frontend/src/features/companion/index.ts
dependencies:
  - TASK-001
---

# Task: [TASK-002] Build Frontend AI Companion Chat Widget and Client Service

## 1. Flow Context
- **Target Flow**: FLOW-AI-COMPANION
- **Position in Flow**: Step 2 of 3.
- **Previous Step**: TASK-001 (Backend API & Gemini Service).
- **Next Step Triggered**: TASK-003 (QA Verification & Acceptance Testing).

## 2. Acceptance Criteria (Product Owner)
- [ ] Implement strongly typed `companionService.ts` to call `POST /api/v1/companion/chat`.
- [ ] Replace static mock preview in `FloatingAiCompanionWidget.tsx` with dynamic API communication.
- [ ] Chat drawer renders conversation message history with distinct User and Companion message bubbles.
- [ ] Clickable quick prompt chips rendered below AI responses. Clicking a chip immediately sends the prompt.
- [ ] Display remaining daily turn counter for free users (3 turns/day); show upgrade modal or banner when quota reaches 0.
- [ ] Render clickable cards for referenced lessons returned in `referencedLessons`.

## 3. Technical Constraints (Tech Lead)
- Follow Warm Heritage design tokens (warm paper background, elegant serif typography for cultural companion).
- Strictly no hollow/stub state: handle loading spinner, error banners, and empty states.
- Clean separation between presentation components and API integration hooks.
- Verify with `npm run build` in `frontend`.

## 4. Blocker & Escalation Section
- Status: BLOCKED_BY_DEPENDENCY (Awaiting completion of TASK-001 backend endpoints).
- Question / Ambiguity Raised: None.

## 5. Work Execution Checklist (Assignee)
- [ ] Define TypeScript types in `frontend/src/types/companion.ts`.
- [ ] Create `companionService.ts` connecting to Spring Boot backend.
- [ ] Build `CompanionChatDrawer` and `CompanionQuickPrompts`.
- [ ] Mount companion widget trigger into the Reader page layout and main layout.
- [ ] Verify `npm run build` passes with 0 type errors.
