# Rule: Documentation is the Single Source of Truth (SSOT)

## 1. Core Principle
* The `document/` repository is the authoritative Source of Truth for all VieCultures applications (Backend, Frontend, Mobile, Chrome Extension).
* Every functional requirement, database entity schema, and screen design MUST originate from or be reflected in `document/`.
* Agents working on `frontend/` or `backend/` must verify specifications against `document/` before proposing or generating code.

## 2. Decision Tree When Requirements Change

```
                 Incoming Request / Code Change
                               │
               Is it already defined in `document/`?
                               │
                ┌──────────────┴──────────────┐
               YES                            NO
                │                              │
         Proceed to Code          Is the request direct & clear?
                                               │
                                 ┌─────────────┴─────────────┐
                                YES                          NO
                                 │                           │
                          1. Update `document/`       1. STOP & Ask User
                          2. Then write code             (provide proposals)
                                                      2. Wait for confirmation
                                                      3. Update `document/`
                                                      4. Then write code
```

## 3. Scope Mapping
* **New Feature:** Document high-level goal in `01-overview/features-list.md`, specify business logic in `02-business-rules/`, and define UX interactions in `03-product-spec/screen-specs.md`.
* **Data Model Changes:** Update `04-agent-and-dev-guidelines/system-data-dictionary.md` with column names, types, constraints, and audit fields before writing JPA Entities.
* **API Changes:** Document request/response contracts and sequence flows before creating Spring Boot `@RestController` methods.
