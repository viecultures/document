# Project Task Board

This board represents the central state of all work orders organized by **Flows (Vertical Slices)**. The autonomous software development squad operates on this board, delivering end-to-end functionality to the **Client** (Stakeholder).

---

## 1. Flow Pipeline Overview

| Flow Identifier | Flow Name | Total Tasks | Completed | Active Step | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`FLOW-AI-COMPANION`** | Cultural Chatbot (Context Injection & PG Search) | 3 | 3 / 3 | Completed | COMPLETED |
| **`FLOW-AUDIT`** | Codebase Gap Analysis & Backlog Mapping | 1 | 0 / 1 | Step 1 (Audit) | READY |

---

## 2. Active Flow: `FLOW-AI-COMPANION` (Completed)

### Backlog (Pending Execution)
- None

### In Progress (Active Subagents)
- None

### In Review (Awaiting Review & Sign-Off)
- None

### Done (Signed-Off Deliverables)
- [TASK-001](backlog/FLOW-AI-COMPANION/TASK-001-backend-companion-chat.md): Implement Backend AI Companion Chat API with Context Injection and PostgreSQL Search (Completed by `backend-dev`)
- [TASK-002](backlog/FLOW-AI-COMPANION/TASK-002-frontend-companion-widget.md): Build Frontend AI Companion Chat Widget and Client Service (Completed by `frontend-dev`)
- [TASK-003](backlog/FLOW-AI-COMPANION/TASK-003-e2e-verification-quota.md): End-to-End Functional Verification & Quota Enforcement Testing (Completed by `qa-engineer`)
- Verification Sign-Off: [FLOW-AI-COMPANION-QA-REPORT.md](done/FLOW-AI-COMPANION-QA-REPORT.md)

---

## 3. Active Flow: `FLOW-AUDIT` Board

### Backlog (Pending Execution)
- Awaiting initial Codebase Audit across backend and frontend to identify missing features vs requirements.

### In Progress (Active Subagents)
- None

### In Review (Awaiting Review & Sign-Off)
- None

### Done (Signed-Off Deliverables)
- None

---

## 4. Pending Client Decisions

Items requiring high-level business direction or approval from the **Client** are consolidated by the PO/BA into [CLIENT_QUESTIONS.md](CLIENT_QUESTIONS.md).

| Decision ID | Target Flow | Topic | PO/BA Recommendation | Client Status |
| :--- | :--- | :--- | :--- | :--- |
| - | - | No active blockers pending client | - | CLEAR |

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
