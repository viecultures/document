---
id: TASK-003
title: End-to-End Functional Verification & Quota Enforcement Testing
flow: FLOW-AI-COMPANION
step_in_flow: Step 3 of 3 (QA Verification & Edge Case Audit)
assigned_to: qa-engineer
reviewer: product-owner
status: BLOCKED
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/03_domain_ai_companion/fallback_mechanisms.md
  - docs/00_core/edge_cases_and_validation.md
  - docs/tasks/backlog/FLOW-AI-COMPANION/TASK-001-backend-companion-chat.md
  - docs/tasks/backlog/FLOW-AI-COMPANION/TASK-002-frontend-companion-widget.md
outputs:
  - docs/tasks/done/FLOW-AI-COMPANION-QA-REPORT.md
dependencies:
  - TASK-001
  - TASK-002
---

# Task: [TASK-003] End-to-End Functional Verification & Quota Enforcement Testing

## 1. Flow Context
- **Target Flow**: FLOW-AI-COMPANION
- **Position in Flow**: Step 3 of 3.
- **Previous Step**: TASK-002 (Frontend Companion Widget).
- **Next Step Triggered**: None (Flow Sign-Off).

## 2. Acceptance Criteria (Product Owner)
- [ ] Verify Lesson-Scoped chat accurately pulls lesson content and answers within topic context.
- [ ] Verify Global Cultural chat searches Postgres articles and recommends relevant lessons.
- [ ] Verify Graceful Fallback triggers for out-of-scope topics without crashing or throwing raw 500 errors.
- [ ] Verify 3 turns/day limit for free tier; verify upgrade CTA appears on 4th attempt.
- [ ] Verify handling of Gemini API network timeout / key failure without breaking the client UI.

## 3. Technical Constraints (Tech Lead)
- Report explicit reproducible steps for every defect.
- Verify both desktop and mobile responsiveness for the chat drawer.

## 4. Blocker & Escalation Section
- Status: BLOCKED_BY_DEPENDENCY (Awaiting completion of TASK-001 and TASK-002).
- Question / Ambiguity Raised: None.

## 5. Work Execution Checklist (Assignee)
- [ ] Test scenario 1: Chat inside lesson `/reader/:id`.
- [ ] Test scenario 2: General chat from global map / header.
- [ ] Test scenario 3: Out-of-bounds question (fallback test).
- [ ] Test scenario 4: Rate limit threshold test (3 requests).
- [ ] Compile actual verification sign-off report to `docs/tasks/done/`.
