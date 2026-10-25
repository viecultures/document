---
id: TASK-001
title: Implement Backend AI Companion Chat API with Context Injection and PostgreSQL Search
flow: FLOW-AI-COMPANION
step_in_flow: Step 1 of 3 (Backend API & Gemini Service)
assigned_to: backend-dev
reviewer: tech-lead
status: IN_REVIEW
created_at: 2026-10-24
updated_at: 2026-10-24
inputs:
  - docs/03_domain_ai_companion/interface_ai_companion.md
  - docs/03_domain_ai_companion/context_retrieval_chat.md
  - docs/03_domain_ai_companion/fallback_mechanisms.md
  - docs/00_core/system_constants.md
outputs:
  - backend/src/main/java/com/viecultures/backend/dto/CompanionChatMessage.java
  - backend/src/main/java/com/viecultures/backend/dto/ReferencedLessonDto.java
  - backend/src/main/java/com/viecultures/backend/dto/CompanionChatRequest.java
  - backend/src/main/java/com/viecultures/backend/dto/CompanionChatResponse.java
  - backend/src/main/java/com/viecultures/backend/service/CompanionChatService.java
  - backend/src/main/java/com/viecultures/backend/service/impl/CompanionChatServiceImpl.java
  - backend/src/main/java/com/viecultures/backend/controller/CompanionChatController.java
dependencies:
  - docs/03_domain_ai_companion/context_retrieval_chat.md
---

# Task: [TASK-001] Implement Backend AI Companion Chat API with Context Injection and PostgreSQL Search

## 1. Flow Context
- **Target Flow**: FLOW-AI-COMPANION (AI Companion Cultural Chatbot)
- **Position in Flow**: Step 1 of 3.
- **Previous Step**: [ALIGN-002] Architecture Alignment (BA).
- **Next Step Triggered**: TASK-002 (Frontend Companion Widget).

## 2. Acceptance Criteria (Product Owner)
- [x] Implement `POST /api/v1/companion/chat` matching `CompanionChatRequest` and `CompanionChatResponse`.
- [x] If `lessonId` is provided: Load `ReadingPost` and associated paragraphs, inject into Gemini prompt context.
- [x] If `lessonId` is null: Search `ReadingPostRepository` by keyword (title/summary/topic), inject top matched posts or fallback gracefully if none found.
- [x] Free tier rate limit: Validate maximum 3 requests per day for non-pro users as defined in `system_constants.md`. Return 403 Forbidden with `LIMIT_EXCEEDED` when quota depleted.
- [x] Response includes conversational reply, 2 suggested prompts, and referenced lesson metadata.

## 3. Technical Constraints (Tech Lead)
- Apply interface structure: declare interface contracts prior to implementation (`CompanionChatService`).
- Always catch and log errors using structured loggers; never swallow exceptions.
- Never write placeholder, mock, or hollow code. Produce fully functional logic.
- Retrieve all secrets and configuration values strictly from environment variables.

## 4. Blocker & Escalation Section
- Status: CLEAR
- Question / Ambiguity Raised: None
- PO/BA Preliminary Decision & Proposal: Option 1 approved in ALIGN-002.

## 5. Work Execution Checklist (Assignee)
- [x] Create request and response DTOs with validation annotations.
- [x] Add search method in `ReadingPostRepository`.
- [x] Implement `CompanionChatService` with context retrieval and prompt construction logic.
- [x] Call Gemini API for chat generation with temperature 0.7 and safety settings.
- [x] Expose `POST /api/v1/companion/chat` in `CompanionChatController` with OpenAPI annotations.
