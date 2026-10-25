# Project Task Board

This board represents the central state of all work orders organized by **Flows (Vertical Slices)**. The autonomous software development squad operates on this board, delivering end-to-end functionality to the **Client** (Stakeholder).

> 🎯 **CLIENT DIRECTIVE (HIGHEST PRIORITY):** Đảm bảo chức năng chatbox hoạt động tốt. Ưu tiên bốc và hoàn thiện luồng chatbox trước tiên (`FLOW-AI-COMPANION`). Sau khi hoàn thành mới làm các tính năng khác bám theo main flow.

---

## 1. Flow Pipeline Overview

| Flow Identifier | Flow Name | Total Tasks | Completed | Active Step | Priority & Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`FLOW-AI-COMPANION`** | Cultural Chatbot (Context Injection & PG Search) | 3 | 0 / 3 | Step 1: TASK-001 | 🔴 **PRIORITY #1 (ACTIVE / READY)** |
| **`FLOW-READER`** | Bilingual Reader & Sticky Audio Player [1x, 0.8x, 0.5x] | 1 | 0 / 1 | Step 1: TASK-004 | ⏳ BACKLOG |
| **`FLOW-VOCAB-FLASHCARD`**| 1-Click Save with Context & Leitner Flashcards | 1 | 0 / 1 | Step 1: TASK-005 | ⏳ BACKLOG |
| **`FLOW-GAMIFICATION`** | Daily Streak & Red Seal (Mộc Son Đỏ) Ritual | 1 | 0 / 1 | Step 1: TASK-006 | ⏳ BACKLOG |
| **`FLOW-BUSINESS`** | Pro Subscription (39k/mo Mock QR & Quota Unlock) | 1 | 0 / 1 | Step 1: TASK-007 | ⏳ BACKLOG |
| **`FLOW-COMMUNITY`** | Non-Judgmental Reflections UGC & Moderation | 1 | 0 / 1 | Step 1: TASK-008 | ⏳ BACKLOG |

---

## 2. Active Flow: `FLOW-AI-COMPANION` (Priority #1)

### Backlog (Pending Execution)
- 🟢 [TASK-001](backlog/FLOW-AI-COMPANION/TASK-001-backend-companion-chat.md): Implement Backend AI Companion Chat API with Context Injection and PostgreSQL Search (Status: **READY** | Assignee: `backend-dev`)
- 🔒 [TASK-002](backlog/FLOW-AI-COMPANION/TASK-002-frontend-companion-widget.md): Build Frontend AI Companion Chat Widget and Client Service (Status: **BLOCKED** by TASK-001 | Assignee: `frontend-dev`)
- 🔒 [TASK-003](backlog/FLOW-AI-COMPANION/TASK-003-e2e-verification-quota.md): End-to-End Functional Verification & Quota Enforcement Testing (Status: **BLOCKED** by TASK-001, TASK-002 | Assignee: `qa-engineer`)

### In Progress (Active Subagents)
- *None (Awaiting Phase 2 Single Ticket Execution Gate)*

### In Review (Awaiting Review & Sign-Off)
- *None*

### Done (Signed-Off Deliverables)
- *None (Previous paper QA report archived; actual functional code to be delivered and verified in Phase 2)*

---

## 3. Subsequent Flows Backlog (Main Experience Pipeline)

| Task ID | Target Flow | Title | Assignee | Status |
| :--- | :--- | :--- | :--- | :--- |
| [TASK-004](backlog/FLOW-READER/TASK-004-reader-audio-pairing.md) | `FLOW-READER` | Bilingual Reader Paragraph Pairing and Sticky Audio Player Speeds | `frontend-dev` | BACKLOG |
| [TASK-005](backlog/FLOW-VOCAB-FLASHCARD/TASK-005-vocab-context-flashcard.md) | `FLOW-VOCAB-FLASHCARD` | 1-Click Save with Context Sentence and Leitner Binary Flashcards | `frontend-dev` | BACKLOG |
| [TASK-006](backlog/FLOW-GAMIFICATION/TASK-006-gamification-streak-seal.md) | `FLOW-GAMIFICATION` | Daily Streak Tracking and Red Seal (Mộc Son) Activation Ritual | `frontend-dev` | BACKLOG |
| [TASK-007](backlog/FLOW-BUSINESS/TASK-007-pro-checkout-qr.md) | `FLOW-BUSINESS` | Pro Subscription Mock Checkout QR and Unlimited Access Unlock | `frontend-dev` | BACKLOG |
| [TASK-008](backlog/FLOW-COMMUNITY/TASK-008-community-reflections.md) | `FLOW-COMMUNITY` | Non-Judgmental Reflections UGC Feed with Passive Moderation | `frontend-dev` | BACKLOG |

---

## 4. Pending Client Decisions

Items requiring high-level business direction or approval from the **Client** are consolidated by the PO/BA into [CLIENT_QUESTIONS.md](CLIENT_QUESTIONS.md).

| Decision ID | Target Flow | Topic | Selected Decision | Status |
| :--- | :--- | :--- | :--- | :--- |
| `DECISION-000` | Squad Governance | Operating Model | Autonomous Squad with User as Client/Stakeholder | RESOLVED |
| `DECISION-001` | All Flows | Core Milestone Priority Directive | **Top Priority**: Đảm bảo chức năng chatbox hoạt động tốt. Ưu tiên bốc và giải quyết ticket chatbox trước tiên. Sau khi xong mới làm tiếp các chức năng khác bám theo main flow. | RESOLVED |

---

## 5. Autonomous Squad Responsibility Directory

- **Client (User)**: Primary stakeholder. Communicates feedback directly to BA; reviews high-level proposals when desired.
- **Business Analyst (`business-analyst`)**: Directly interfaces with Client, logs meeting minutes in [CLIENT_BA_ALIGNMENT.md](CLIENT_BA_ALIGNMENT.md), updates use cases, and briefs PM on task adjustments.
- **Product Owner (`product-owner`)**: Holds full decision-making authority in the squad to prevent delays; enforces invariants and business rules.
- **Project Manager (`project-manager`)**: Flow orchestration, task assignment, status updates across ticket folders and this board.
- **Tech Lead (`tech-lead`)**: Directs implementation in code files (`src/`), audits codebase to prevent duplicates, reviews code quality. No code definition in markdown.
- **Backend Developer (`backend-dev`)**: Production implementation directly in backend source files.
- **Frontend Developer (`frontend-dev`)**: Production implementation directly in frontend source files.
- **QA Engineer (`qa-engineer`)**: Verifies working code against acceptance criteria.
