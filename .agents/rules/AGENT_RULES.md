# VieCultures Documentation Rules & Architectural Constraints (SSOT)

This document establishes the mandatory documentation standards, OOP-style knowledge hierarchy, and diagramming rules for the `document/` repository. This repository is the **Single Source of Truth (SSOT)** for all business logic, data models, user flows, and technical requirements across VieCultures (Frontend, Backend, Mobile, Chrome Extension).

---

## 1. Prime Directives (Non-Negotiable)

### 1.1. Single Source of Truth (SSOT)
* **The `document/` repository is the supreme authority.**
* No feature, endpoint, database column, or UI screen may be implemented in `backend/` or `frontend/` without being documented here first.
* If a code change is requested:
  * **Direct & Clear:** Update the corresponding document in `01-overview/`, `02-business-rules/`, `03-product-spec/`, or `04-agent-and-dev-guidelines/` first.
  * **Ambiguous or Under-specified:** STOP immediately. Propose architectural or business options, wait for user confirmation, record the decision in `document/`, and then proceed.

### 1.2. OOP Documentation Architecture (Domain & Granularity)
All documentation must adhere to clean modular boundaries:
```
document/
├── 01-overview/                   # System domain, high-level vision, glossary & roadmap
│   ├── vision-and-goals.md        # Problem statement, target learners, cultural mission
│   ├── features-list.md           # Master catalog of features
│   ├── glossary.md                # Domain terms (CEFR, Shadowing, Spaced Repetition, etc.)
│   └── product-roadmap.md         # Phased execution milestones
├── 02-business-rules/             # Business rules & invariant constraints
│   ├── BR-01-reading-content.md   # Bilingual paragraph alignment & TTS audio rules
│   ├── BR-02-vocab-extraction.md  # Cultural vocabulary extraction & difficulty tagging
│   ├── BR-03-reflections-ugc.md   # User reflection submission & moderation
│   ├── BR-04-flashcard-spaced.md  # SM-2 / Leitner spaced repetition logic
│   ├── BR-05-user-journey.md      # Onboarding, reading flow, milestone completion
│   └── BR-06-gamification-habits.md # Streaks, cultural badges, XP rules
├── 03-product-spec/               # Detailed product specifications
│   ├── screen-specs.md            # Screen-by-screen UX, states & interactions
│   ├── sitemap-and-navigation.md  # Full site IA, route mapping & route guards
│   ├── content-management.md      # Admin CMS, TSV ingestion format, audio pipeline
│   └── learning-loop-ai-map.md    # AI Map & Gamification plan
└── 04-agent-and-dev-guidelines/   # Technical reference for engineers & agents
    ├── system-data-dictionary.md  # Entity schemas, column types & validation constraints
    └── edge-cases-and-validation.md # Failure modes, timeouts & input sanitization
```

---

## 2. Diagramming Standards

1. **Entity-Relationship Diagrams (Conceptual):**
   * Must use Chen's Notation generated via Mermaid `flowchart LR/TD` (Rectangles `[Entity]` for entities, Diamonds `{Relationship}` for relations, undirected lines `---|1|` and `---|M|`).
   * Follow `@skill:mermaid-chen-erd`.

2. **UX Sitemaps & Screen Flows:**
   * Must use Mermaid flowchart with `elk` renderer and `curve: "step"` for clean 90-degree orthogonal lines.
   * Color-code: Public screens (cream/orange `#ffe6cc`), Secure screens (white `#ffffff`), Actions (oval).
   * Follow `@skill:mermaid-screen-flows`.

3. **API & Request Tracing (Sequence Diagrams):**
   * Must use Mermaid `sequenceDiagram` with `autonumber`.
   * Explicit participant roles: Actor (User/Admin), FE (React), BE (Spring Boot), DB (Supabase), External (Azure TTS/Gemini).
   * Follow `@skill:mermaid-sequence-diagrams`.

---

## 3. Writing & Quality Guidelines

* **Bilingual Terminology:** English for technical terms, database tables, and architecture; Vietnamese for cultural content, idioms, and user stories.
* **Format:** Clean GitHub Markdown, concise tables, explicit ID codes (e.g. `BR-01`, `UC-02`, `FR-14`).
* **Zero Contradictions:** When modifying a business rule, ensure cross-references in `screen-specs.md` and `system-data-dictionary.md` are kept synchronized.
