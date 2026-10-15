---
name: doc-mermaid-sequence-diagrams
description: Generates clean Mermaid sequence diagrams for API requests, audio TTS streaming, and user interactions in VieCultures.
---

# Mermaid Sequence Diagrams

Generates interaction diagrams tracing requests across Frontend, Controller, Service, Database, and External AI/TTS Services.

## Directives
1. **Participant Declaration:**
   Always declare participants explicitly with descriptive aliases:
   ```mermaid
   sequenceDiagram
       autonumber
       actor Learner
       participant FE as React Client
       participant BE as Spring Controller
       participant SVC as AzureSpeechService
       participant DB as PostgreSQL
       participant AZ as Azure Speech API

       Learner->>FE: Click "Generate Audio"
       FE->>BE: POST /api/tts/generate
       BE->>SVC: synthesizeSpeech(text, voice)
       alt Audio already cached
           SVC-->>BE: Return cached audio URL
       else Not in cache
           SVC->>AZ: Synthesize SSML / Audio stream
           AZ-->>SVC: Audio WAV bytes
           SVC->>DB: Save VoiceTrack record
           SVC-->>BE: Return new audio URL
       end
       BE-->>FE: ApiResponse<VoiceTrackDto>
       FE-->>Learner: Play audio & highlight paragraphs
   ```
2. **Conventions:**
   - Use `autonumber` for step tracing.
   - Use solid arrows (`->>`) for sync calls and dashed arrows (`-->>`) for responses.
   - Use `alt`/`else` blocks for cache hits vs external API calls.
