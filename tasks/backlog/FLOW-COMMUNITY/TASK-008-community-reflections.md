---
id: TASK-008
title: Non-Judgmental Reflections UGC Feed with Passive Moderation
flow: FLOW-COMMUNITY
step_in_flow: Step 1 of 1 (Social Community & Belonging)
assigned_to: frontend-dev
reviewer: tech-lead
status: BACKLOG
created_at: 2026-10-25
updated_at: 2026-10-25
inputs:
  - docs/06_domain_community/interface_community.md
  - docs/06_domain_community/reflections_moderation.md
outputs:
  - frontend/src/features/community/components/ReaderReflectionsSection.tsx
dependencies:
  - FLOW-READER
---

# Task: [TASK-008] Non-Judgmental Reflections UGC Feed with Passive Moderation

## 1. Flow Context
- **Target Flow**: FLOW-COMMUNITY (Main Experience Phase 3)
- **Position in Flow**: Post-reading reflection.
- **Previous Flow**: FLOW-READER.

## 2. Acceptance Criteria (Product Owner)
- [ ] Allow readers to submit personal cultural reflections (English or bilingual) below each reading post.
- [ ] Enforce "Non-Judgmental English Policy": prominently display banner assuring learners that language errors are welcome.
- [ ] Passive profanity and inappropriate content filter before reflection becomes public.

## 3. Technical Constraints (Tech Lead)
- Optimistic UI updates with instant local reflection rendering.
