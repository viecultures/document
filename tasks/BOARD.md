# Project Task Board

This board represents the central state of all work orders organized by **Flows (Vertical Slices)**. The autonomous software development squad operates on this board, delivering end-to-end functionality to the **Client** (Stakeholder).

> 🎯 **CLIENT DIRECTIVE:** Chức năng chatbox (`FLOW-AI-COMPANION`) đã được Client tự hoàn tất. Squad bỏ qua chatbox và tập trung thực hiện các tính năng tiếp theo bám sát main flow (`FLOW-READER`, `FLOW-VOCAB-FLASHCARD`, v.v.).

---

## 1. Flow Pipeline Overview

| Flow Identifier | Flow Name | Total Tasks | Completed | Active Step | Priority & Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`FLOW-AI-COMPANION`** | Cultural Chatbot (Context Injection & PG Search) | 3 | 3 / 3 | Completed by Client | 🟢 **DELIVERED (BY CLIENT)** |
| **`FLOW-READER`** | Bilingual Reader & Sticky Audio Player [1x, 0.8x, 0.5x] | 1 | 1 / 1 | Completed: TASK-004 | 🟢 **DELIVERED** |
| **`FLOW-VOCAB-FLASHCARD`**| 1-Click Save with Context & Leitner Flashcards | 1 | 1 / 1 | Completed: TASK-005 | 🟢 **DELIVERED** |
| **`FLOW-GAMIFICATION`** | Daily Streak & Red Seal (Mộc Son Đỏ) Ritual | 1 | 1 / 1 | Completed: TASK-006 | 🟢 **DELIVERED** |
| **`FLOW-BUSINESS`** | Pro Subscription (39k/mo Mock QR & Quota Unlock) | 1 | 1 / 1 | Completed: TASK-007 | 🟢 **DELIVERED** |
| **`FLOW-COMMUNITY`** | Non-Judgmental Reflections UGC & Moderation | 1 | 1 / 1 | Completed: TASK-008 | 🟢 **DELIVERED** |

---

## 2. Active Flow: `FLOW-COMMUNITY` (Delivered)

### Backlog (Pending Execution)
- *None*

### In Progress (Active Subagents)
- *None*

### In Review (Awaiting Review & Sign-Off)
- *None*

### Done (Signed-Off Deliverables)
- 🟢 [TASK-008](done/TASK-008-community-reflections.md): Non-Judgmental Reflections UGC Feed with Passive Moderation (Status: **DONE** | Assignee: `frontend-dev`)
- 🟢 [TASK-007](done/TASK-007-pro-checkout-qr.md): Pro Subscription Mock Checkout QR and Unlimited Access Unlock (Status: **DONE** | Assignee: `frontend-dev`)
- 🟢 [TASK-006](done/TASK-006-gamification-streak-seal.md): Daily Streak Tracking and Red Seal (Mộc Son) Activation Ritual (Status: **DONE** | Assignee: `frontend-dev`)
- 🟢 [TASK-005](done/TASK-005-vocab-context-flashcard.md): 1-Click Save with Context Sentence and Leitner Binary Flashcards (Status: **DONE** | Assignee: `frontend-dev`)
- 🟢 [TASK-004](done/TASK-004-reader-audio-pairing.md): Bilingual Reader Paragraph Pairing and Sticky Audio Player Speeds (Status: **DONE** | Assignee: `frontend-dev`)
- `FLOW-AI-COMPANION`: Chatbox completed by Client.

---

## 3. Subsequent Flows Backlog (Main Experience Pipeline)

| Task ID | Target Flow | Title | Assignee | Status |
| :--- | :--- | :--- | :--- | :--- |
| [TASK-004](done/TASK-004-reader-audio-pairing.md) | `FLOW-READER` | Bilingual Reader Paragraph Pairing and Sticky Audio Player Speeds | `frontend-dev` | DONE |
| [TASK-005](done/TASK-005-vocab-context-flashcard.md) | `FLOW-VOCAB-FLASHCARD` | 1-Click Save with Context Sentence and Leitner Binary Flashcards | `frontend-dev` | DONE |
| [TASK-006](done/TASK-006-gamification-streak-seal.md) | `FLOW-GAMIFICATION` | Daily Streak Tracking and Red Seal (Mộc Son) Activation Ritual | `frontend-dev` | DONE |
| [TASK-007](done/TASK-007-pro-checkout-qr.md) | `FLOW-BUSINESS` | Pro Subscription Mock Checkout QR and Unlimited Access Unlock | `frontend-dev` | DONE |
| [TASK-008](done/TASK-008-community-reflections.md) | `FLOW-COMMUNITY` | Non-Judgmental Reflections UGC Feed with Passive Moderation | `frontend-dev` | DONE |

---

## 4. Pending Client Decisions

Items requiring high-level business direction or approval from the **Client** are consolidated by the PO/BA into [CLIENT_QUESTIONS.md](CLIENT_QUESTIONS.md).

| Decision ID | Target Flow | Topic | Selected Decision | Status |
| :--- | :--- | :--- | :--- | :--- |
| `DECISION-000` | Squad Governance | Operating Model | Autonomous Squad with User as Client/Stakeholder | RESOLVED |
| `DECISION-001` | All Flows | Core Milestone Priority Directive | **Updated Directive**: Client đã tự hoàn thiện tính năng Chatbox (`FLOW-AI-COMPANION`). Squad KHÔNG làm task chatbox nữa. PM và Squad bám sát theo main flow kế tiếp trên BOARD.md (bắt đầu từ `FLOW-READER` và các flow tiếp theo). | RESOLVED |
| `DECISION-002` | Milestone 2 | Next Milestone Priority Directive (Post-Core Pipeline Delivery) | [Option A (Recommended): `FLOW-SPEAKING-VOICE`](CLIENT_QUESTIONS.md#decision-002-next-milestone-priority-directive-post-core-pipeline-delivery) | PENDING_CLIENT_RESPONSE |

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
