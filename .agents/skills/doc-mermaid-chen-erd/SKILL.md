---
name: doc-mermaid-chen-erd
description: Generates academic and conceptual Entity-Relationship Diagrams (Chen's notation) using Mermaid flowcharts with rectangles and diamonds.
---

# Mermaid Chen ERD (Conceptual)

Generates classic Conceptual ER Diagrams with Diamonds and Rectangles for VieCultures models instead of physical database tables.

## Directives
1. **Flowchart Syntax (Not erDiagram):**
   Mermaid's native `erDiagram` creates relational physical tables. For Chen notation, you MUST use `flowchart LR` or `flowchart TD`.
2. **Node Shapes & Undirected Edges:**
   - Entities: Rectangles `[Entity Name]`
   - Relationships: Diamonds `{Relationship Name}`
   - Connections: Undirected lines `---` with cardinality labels (`|1|`, `|M|`, `|N|`). Never use arrows (`-->`).
3. **Template:**
   ```mermaid
   %%{init: {"flowchart": {"curve": "linear"}}}%%
   flowchart LR
       E1[User]:::entity
       E2[ReadingPost]:::entity
       E3[VocabItem]:::entity
       E4[UserReflection]:::entity

       R1{reads}:::relation
       R2{contains}:::relation
       R3{submits}:::relation

       E1 ---|1| R1
       R1 ---|M| E2

       E2 ---|1| R2
       R2 ---|N| E3

       E1 ---|1| R3
       R3 ---|M| E4

       classDef entity fill:#1E4B43,stroke:#122A22,stroke-width:2px,color:#fff;
       classDef relation fill:#D9B76A,stroke:#B89745,stroke-width:2px,color:#000;
   ```
