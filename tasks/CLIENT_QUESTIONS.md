# Client Questions & Decision Registry

This document serves as the communication bridge between the autonomous software development squad and the **Client** (Human Stakeholder). 

Whenever business decisions or requirement trade-offs require Client confirmation, the **Product Owner / Business Analyst (PO/BA)** logs the item here with preliminary analysis and a recommended option. The Client reviews this document and inputs answers or approves recommendations.

---

## 1. Pending Decisions (Awaiting Client Response)

### [DECISION-002] Next Milestone Priority Directive Post-Core Pipeline Delivery
- **Date Raised**: 2026-10-25
- **Target Flow / Task**: Next Milestone Phase (Post `FLOW-COMMUNITY`)
- **Context & Impact**:
  All 6 initial flows specified in the product roadmap and on `BOARD.md` have been fully delivered and verified:
  1. `FLOW-AI-COMPANION`: Cultural Chatbox delivered by Client.
  2. `FLOW-READER` (TASK-004): 1:1 bilingual paragraph pairing & sticky audio player with SSOT speeds (`0.5x`, `0.8x`, `1.0x`).
  3. `FLOW-VOCAB-FLASHCARD` (TASK-005): 1-Click Save with context sentence & Leitner binary flashcards.
  4. `FLOW-GAMIFICATION` (TASK-006): Daily streak tracking & Mộc Son Red Seal activation ritual.
  5. `FLOW-BUSINESS` (TASK-007): Pro subscription 39k/mo mock VietQR checkout & quota gateway.
  6. `FLOW-COMMUNITY` (TASK-008): Non-Judgmental Reflections UGC feed with passive moderation & quick vocab toolbar.

  The backlog for this first milestone wave is now completely delivered (0 unblocked tickets remaining). The autonomous squad seeks Client directive on which flow to decompose into backlog tickets next.
- **BA/PO Proposals & Options**:
  - [x] **Option A (Recommended)**: **`FLOW-SPEAKING-VOICE`** (`document/04_domain_speaking_voice/pronunciation_feedback.md`). Implement Web Speech API pronunciation scoring, color-coded word accuracy (`#2F855A` green for clear, `#DD6B20` orange for mispronounced/skipped), and encouraging feedback metrics in the Reader practice workspace.
  - [ ] **Option B**: **`FLOW-BACKEND-PERSISTENCE`**. Implement backend REST API endpoints and PostgreSQL persistence for Community Reflections (`UserReflectionController`, `GET /api/v1/reflections`, `POST /api/v1/reflections`, reactions) and Gamification Streak sync (`StreakController`).
  - [ ] **Option C**: **`FLOW-MOBILE-SYNC`**. Connect Expo React Native mobile app (`mobile/`) to backend endpoints for reader, flashcards, and community screens.
- **Client Decision**: [Awaiting Client choice]
- **Status**: PENDING_CLIENT_RESPONSE

---

## 2. Resolved Decisions (Signed Off by Client)

| Decision ID | Topic | Selected Decision | Sign-off Date | Status |
| :--- | :--- | :--- | :--- | :--- |
| `DECISION-000` | Squad Operating Model | Autonomous Squad with User as Client/Stakeholder | 2026-10-24 | RESOLVED |
| `DECISION-001` | Core Milestone Priority Directive | **Updated Directive**: Client đã tự hoàn thiện tính năng Chatbox (`FLOW-AI-COMPANION`). Squad KHÔNG làm task chatbox nữa. PM và Squad bám sát theo main flow kế tiếp trên BOARD.md (bắt đầu từ `FLOW-READER` và các flow tiếp theo). | 2026-10-25 | RESOLVED |
