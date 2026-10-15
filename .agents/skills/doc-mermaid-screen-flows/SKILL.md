---
name: doc-mermaid-screen-flows
description: Generates crisp orthogonal UX sitemaps and screen flow diagrams with color-coded public, secure, and modal views for VieCultures.
---

# Mermaid Screen Flow Diagrams

Generates UX Sitemaps and Screen Flow Diagrams mapping page navigation structures for VieCultures.

## Directives
1. **Orthogonal Routing:**
   Use the `elk` layout engine with `curve: "step"` for clean 90-degree lines:
   ```mermaid
   %%{init: {"flowchart": {"defaultRenderer": "elk", "curve": "step", "nodeSpacing": 50, "rankSpacing": 70}}}%%
   flowchart LR
       LandingPage[Landing Page /]:::publicMain --> DiscoveryPage[Discovery & Heritage Map /discovery]:::publicMain
       DiscoveryPage --> ReaderPage[Bilingual Reader /reader/:id]:::publicMain
       ReaderPage --> DictationRoom[AI Dictation Playground /playground]:::publicMain
       ReaderPage --> VocabModal([Vocabulary Drawer]):::oval

       LandingPage --> AdminLogin[Admin Portal /admin]:::secure
       AdminLogin --> AdminDashboard[CMS Dashboard]:::secure
       AdminDashboard --> PostFormModal([Create/Edit Post Modal]):::oval

       classDef publicMain fill:#FBF7EE,stroke:#1E4B43,stroke-width:2px,color:#1E4B43;
       classDef secure fill:#F6EEDC,stroke:#9E2A2B,stroke-width:2px,color:#9E2A2B;
       classDef oval fill:#FFF9E6,stroke:#D9B76A,stroke-width:1.5px,color:#333;
   ```
2. **Subgraphs for Multi-panel Views:**
   Use subgraphs with light backgrounds to group panels contained within a single screen (e.g. Bilingual Split View, Vocabulary Drawer, Audio Controller).
