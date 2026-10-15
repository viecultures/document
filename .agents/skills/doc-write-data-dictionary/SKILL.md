---
name: doc-write-data-dictionary
description: Documents entity attributes, field data types, validations, and relational constraints in 04-agent-and-dev-guidelines/system-data-dictionary.md.
---

# Write Data Dictionary

Maintains the system data dictionary in `document/04-agent-and-dev-guidelines/system-data-dictionary.md`.

## Directives
1. **File Location:** `document/04-agent-and-dev-guidelines/system-data-dictionary.md`
2. **Template Structure:**
   ```markdown
   ## Entity: `<EntityName>` (Table: `<table_name>`)

   | Field Name | Type | Constraints | Description & Business Rules |
   | :--- | :--- | :--- | :--- |
   | `id` | `Long` | PK, Generated | Unique identifier |
   | `slug` | `String` | Unique, Non-null, Max 255 | URL slug (e.g. `hoang-thanh-thang-long`) |
   | `title_vi` | `String` | Non-null, Max 255 | Vietnamese title |
   | `title_en` | `String` | Non-null, Max 255 | English title |
   | `province` | `String` | Non-null, Max 100 | Vietnamese province (e.g. `Hà Nội`, `Huế`) |
   | `cefr_level` | `String` | Enum (`A1`, `A2`, `B1`, `B2`, `C1`) | Difficulty rating |
   | `audio_url` | `String` | Nullable | URL to cached TTS speech file |
   | `created_at` | `Timestamp` | Non-null | Auto-generated creation audit timestamp |
   ```
