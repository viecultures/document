# Client & BA Alignment Log

This log captures direct discussions, change requests, and requirement confirmations between the **Client** (Human Stakeholder) and the **Business Analyst (BA)**. 

Whenever the Client confirms requirements or requests UI/logic adjustments, the BA records the discussion here, updates the domain specifications, and triggers the **Project Manager (PM)** to adjust tickets on `BOARD.md`.

---

## Alignment Sessions & Change Requests

### [ALIGN-001] Baseline Squad Operating Model Alignment
- **Date**: 2026-10-24
- **Participants**: Client (User), Business Analyst (BA)
- **Discussion Summary**: 
  - PO has full decision autonomy to avoid team delays.
  - Client communicates directly with the BA for requirement changes and confirmations.
  - BA logs alignment notes here, updates documentation, and triggers PM to generate adjustment tasks.
  - Client / Team members can prompt directly for quick UI fixes, while the assistant synchronizes changes back to docs to preserve architecture integrity.
- **Specification Updates**:
  - Added `business-analyst` agent role.
  - Updated `product-owner` role to autonomous decision-maker.
- **Action Items for PM**:
  - Register BA in squad matrix on `docs/tasks/BOARD.md`.
  - Maintain synchronization between ad-hoc UI prompts and design specs.
- **Status**: CLOSED

### [ALIGN-002] Chatbox Architecture Alignment - Context Injection & PostgreSQL Search
- **Date**: 2026-10-24
- **Participants**: Client (User), Business Analyst (BA)
- **Discussion Summary**: 
  - Client proposed using Vertex AI Managed RAG Engine + Cloud Spanner for the website cultural chatbot.
  - BA analyzed feasibility, infrastructure complexity, and COGS: Vertex RAG + Spanner is over-engineering for the current scale (<100 articles, ~100k tokens total).
  - Client agreed to proceed with **Option 1**: Context Injection + PostgreSQL Full-Text Search using existing Spring Boot backend and Google Gemini API.
- **Specification Updates**:
  - Created `docs/03_domain_ai_companion/context_retrieval_chat.md` specifying two chat modes (Lesson-scoped and Global search), API contracts (`POST /api/v1/companion/chat`), system prompt templates, and quota tiers.
  - Updated `docs/03_domain_ai_companion/interface_ai_companion.md` with reference to the new context retrieval specification.
- **Action Items for PM**:
  - Register implementation task for backend chat service and frontend AI companion widget.
  - Coordinate with `backend-dev` for Gemini integration and `frontend-dev` for floating chat modal.
- **Status**: CLOSED

### [ALIGN-003] Bilingual AI Companion and Chat History Persistence Alignment
- **Date**: 2026-10-25
- **Participants**: Client (User), Business Analyst (BA)
- **Discussion Summary**:
  - Client requested expanding AI Companion capabilities with:
    1. Bilingual conversational modes ('vi', 'en', 'bilingual') to support diverse learner segments.
    2. Contextual inline translation for messages preserving Vietnamese culinary and cultural depth.
    3. Multi-tier chat history persistence: localStorage for guest users (up to 3 daily turns), and PostgreSQL sync for authenticated users with cross-device retrieval and privacy-first deletion.
  - BA formalized the conversational lifecycles, Given-When-Then acceptance criteria, API contracts (5 endpoints), database persistence schema, and security isolation rules.
- **Specification Updates**:
  - Updated `document/03_domain_ai_companion/conversational_flows.md` with bilingual state transitions, inline translation sequence diagram, session persistence lifecycles, and acceptance criteria.
  - Updated `document/03_domain_ai_companion/context_retrieval_chat.md` with comprehensive API contracts for `/chat`, `/translate`, `/history` (GET, POST, DELETE), database schema (`companion_chat_sessions`, `companion_chat_messages`), security rules, and Gemini prompts.
- **Action Items for PM**:
  - [ ] Create backlog ticket `TASK-COMPANION-003`: Backend Chat History Persistence & Translation API implementation.
  - [ ] Create backlog ticket `TASK-COMPANION-004`: Frontend Chatbox UI Bilingual switcher, inline translate button, and session sync.
  - [ ] Update `docs/tasks/BOARD.md` to reflect backlog priorities.
- **Status**: CLOSED

<!-- Template for future alignment entries:
### [ALIGN-xxx] Title of Discussion or Change Request
- **Date**: YYYY-MM-DD
- **Participants**: Client, Business Analyst
- **Discussion Summary**: Key points, UI adjustments, or business logic requested.
- **Specification Updates**: Files in docs/00-product/ or docs/01-logic/ modified by BA.
- **Action Items for PM**:
  - [ ] Adjust ticket TASK-xxx or create rework ticket TASK-yyy in docs/tasks/backlog/.
  - [ ] Update docs/tasks/BOARD.md status.
- **Status**: OPEN / IN_PROGRESS / CLOSED
-->
