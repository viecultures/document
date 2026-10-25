# Client Questions & Decision Registry

This document serves as the communication bridge between the autonomous software development squad and the **Client** (Human Stakeholder). 

Whenever business decisions or requirement trade-offs require Client confirmation, the **Product Owner / Business Analyst (PO/BA)** logs the item here with preliminary analysis and a recommended option. The Client reviews this document and inputs answers or approves recommendations.

---

## 1. Pending Decisions (Awaiting Client Response)

*No active pending decisions at this time.*

---

## 2. Resolved Decisions (Signed Off by Client)

| Decision ID | Topic | Selected Decision | Sign-off Date | Status |
| :--- | :--- | :--- | :--- | :--- |
| `DECISION-000` | Squad Operating Model | Autonomous Squad with User as Client/Stakeholder | 2026-10-24 | RESOLVED |
| `DECISION-001` | Core Milestone Priority Directive | **Updated Directive**: Client đã tự hoàn thiện tính năng Chatbox (`FLOW-AI-COMPANION`). Squad KHÔNG làm task chatbox nữa. PM và Squad bám sát theo main flow kế tiếp trên BOARD.md (bắt đầu từ `FLOW-READER` và các flow tiếp theo). | 2026-10-25 | RESOLVED |
| `DECISION-002` | Milestone 2 Priority Directive | **Selected Option B: `FLOW-BACKEND-PERSISTENCE`**. Xây dựng REST API Spring Boot và PostgreSQL lưu trữ dữ liệu cho Community Reflections và Gamification Streak.<br><br>**Thống nhất kỹ thuật (/grill-me):**<br>1. *Auth Strategy*: Strict Auth (bắt buộc Bearer JWT token cho toàn bộ endpoint reflections và streak).<br>2. *Gamification Model*: Tách riêng entity `UserStreak` (streak_days, last_active_date, freeze_count, streak_protected) và `UserSeal` (reading_post_id, sealed_at, words_learned_count).<br>3. *Reaction Mechanism*: Bảng quan hệ `user_reflection_reactions` (user_id, reflection_id, created_at) đảm bảo toggle like/unlike idempotent. | 2026-10-26 | RESOLVED |

