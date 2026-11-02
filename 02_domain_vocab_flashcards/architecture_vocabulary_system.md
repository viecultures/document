# Kien truc He thong Tu vung & Tu dien (Vocabulary & Dictionary Architecture)

> Pham vi: Module /dictionary, Reader In-Place Lookup, Personal Decks & Flashcards
> CSDL: PostgreSQL (Relational + JSONB Hybrid)
> Ngay thong qua: 2026-11-02

---

## 1. Tong quan Kien truc 3 Lop (3-Tier Architecture)

He thong tu vung duoc chia thanh 3 tang du lieu de toi uu bo nho, ngan chan trung lap va ho tro mo rong thuoc tinh linh hoat:

```
[ Reader Post Ingestion (AI 5-10 terms) ]   [ User Custom Input ]   [ In-Place AI Lookup (On-Demand) ]
                      \                               |                               /
                       ---------------------------------------------------------------
                                                      |
                                           [ Lexicon Service Facade ]
                                                      |
                      +-------------------------------+-------------------------------+
                      |                                                               |
        [ Tier 1: Master Dictionary ]                                       [ Tier 2: Post Binding ]
        - Bang: master_vocabularies                                         - Bang: post_vocab_contexts
        - Unique Key: normalized_word                                       - Unique (post_id, vocab_id)
        - Luu tru goc: IPA, POS, Meaning, Audio                             - Luu tru: context_sentence, cultural_note
        - attributes JSONB + GIN index                                      |
                      |                                                     |
                      +-------------------------------+---------------------+
                                                      |
                                     [ Tier 3: User Personal Deck ]
                                     - Bang: user_vocab_items
                                     - Bang: user_vocab_decks
                                     - Bang: deck_vocab_items (N-N)
                                     - Co che Fallback Overlay (custom_meaning, custom_note)
                                     - Thuat toan SRS (interval_days, next_review_at)
```

---

## 2. Chi tiet Luoc do Co so Du lieu (PostgreSQL Schema)

### 2.1. Tier 1: Master Vocabularies (`master_vocabularies`)
Luu tru thong tin ngon ngu hoc chuan hoa dung chung cho toan bo san. Khong chua du lieu rieng cua bai doc hay nguoi dung.

```sql
CREATE TABLE master_vocabularies (
    id VARCHAR(36) PRIMARY KEY,
    word VARCHAR(120) NOT NULL,
    normalized_word VARCHAR(120) NOT NULL UNIQUE, -- trimmed, lowercased, loai bo ky tu dac biet
    pos VARCHAR(50),                              -- noun, verb, idiom, phrase...
    ipa VARCHAR(100),
    vi_meaning TEXT NOT NULL,
    en_definition TEXT,
    audio_url VARCHAR(255),                      -- Audio TTS luu tren storage/CDN, sinh 1 lan duy nhat
    cefr_level VARCHAR(10) DEFAULT 'B1',          -- A1, A2, B1, B2, C1, C2
    search_count INT DEFAULT 1,
    attributes JSONB DEFAULT '{}'::jsonb,         -- Cac thuoc tinh mo rong: synonyms, antonyms, etymology, collocations
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_master_vocab_normalized ON master_vocabularies(normalized_word);
CREATE INDEX idx_master_vocab_prefix ON master_vocabularies(normalized_word varchar_pattern_ops);
CREATE INDEX idx_master_vocab_attributes_gin ON master_vocabularies USING GIN (attributes);
```

### 2.2. Tier 2: Post Vocab Contexts (`post_vocab_contexts`)
Giai quyet bai toan reuse tu vung giua cac bai doc ma van giu nguyen cau ngu canh dac thu va y nghia van hoa rieng.

```sql
CREATE TABLE post_vocab_contexts (
    id VARCHAR(36) PRIMARY KEY,
    post_id VARCHAR(36) NOT NULL REFERENCES reading_posts(id) ON DELETE CASCADE,
    vocab_id VARCHAR(36) NOT NULL REFERENCES master_vocabularies(id) ON DELETE CASCADE,
    context_sentence TEXT NOT NULL,               -- Cau tieng Anh goc trich tu doan van trong bai
    cultural_note TEXT,                           -- Giai thich sac thai van hoa rieng trong bai doc nay
    order_index INT DEFAULT 0,
    is_highlighted BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT uq_post_vocab UNIQUE (post_id, vocab_id)
);

CREATE INDEX idx_post_vocab_post ON post_vocab_contexts(post_id);
```

### 2.3. Tier 3: User Personal Lexicon & Folders (`user_vocab_items`, `user_vocab_decks`, `deck_vocab_items`)

```sql
-- Danh sach cac Decks / Thu muc do user tu tao giong Quizlet
CREATE TABLE user_vocab_decks (
    id VARCHAR(36) PRIMARY KEY,
    user_id VARCHAR(36) NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    name VARCHAR(120) NOT NULL,
    description TEXT,
    color_code VARCHAR(20) DEFAULT '#8A3B14',
    is_default BOOLEAN DEFAULT FALSE,            -- Deck mac dinh de nhan tu tu 1-Click Save
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_user_decks_user ON user_vocab_decks(user_id);

-- Danh sach tu vung ca nhan cua nguoi dung
CREATE TABLE user_vocab_items (
    id VARCHAR(36) PRIMARY KEY,
    user_id VARCHAR(36) NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    vocab_id VARCHAR(36) NOT NULL REFERENCES master_vocabularies(id) ON DELETE RESTRICT,
    source_type VARCHAR(20) NOT NULL,            -- 'READING_POST', 'AI_LOOKUP', 'MANUAL_INPUT'
    source_post_id VARCHAR(36) REFERENCES reading_posts(id) ON DELETE SET NULL,
    
    -- Fallback Overlay: Neu null thi fallback ve dinh nghia cua master_vocabularies
    custom_vi_meaning TEXT,
    custom_context_sentence TEXT,
    custom_note TEXT,
    
    -- Thong so Spaced Repetition (SRS)
    status VARCHAR(20) DEFAULT 'LEARNING',       -- 'LEARNING', 'REVIEWING', 'MASTERED'
    review_count INT DEFAULT 0,
    ease_factor FLOAT DEFAULT 2.5,
    interval_days INT DEFAULT 0,
    next_review_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_reviewed_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    CONSTRAINT uq_user_vocab UNIQUE (user_id, vocab_id)
);

CREATE INDEX idx_user_vocab_schedule ON user_vocab_items(user_id, next_review_at);

-- Quan he Many-to-Many giua Decks va User Vocab Items
CREATE TABLE deck_vocab_items (
    deck_id VARCHAR(36) NOT NULL REFERENCES user_vocab_decks(id) ON DELETE CASCADE,
    user_vocab_id VARCHAR(36) NOT NULL REFERENCES user_vocab_items(id) ON DELETE CASCADE,
    added_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (deck_id, user_vocab_id)
);
```

---

## 3. Quy dinh Nghiep vu & Han muc (Business Rules)

1. **Hạn mức tài khoản (Theo `system_constants.md`):**
   - Tai khoan Free (`TIER_FREE`): Toi da luu 30 tu trong `user_vocab_items`. Khi dat 30 tu, popup chan yeu cau nang cap Premium.
   - Tai khoan Premium / Trial: Khong gioi han so luong tu luu va so luong Decks.

2. **Deduplication Tuyet doi (Chong trung lap):**
   - Moi tu khi dua vao bang master bat buoc chay qua ham chuan hoa `normalizeWord(word)`: lowercase, loai bo khoang trang thua va dau cau.
   - Khi co 10 bai doc dung chung tu "lantern", chi co 1 ban ghi "lantern" trong `master_vocabularies` va 1 file audio TTS; 10 ban ghi trong `post_vocab_contexts` se tro ve cung `vocab_id` nay.

3. **Fallback Overlay (Tuy bien ca nhan):**
   - Khi hien thi the tu vung ca nhan cua nguoi hoc:
     `effective_meaning = (item.custom_vi_meaning != null && !item.custom_vi_meaning.isBlank()) ? item.custom_vi_meaning : master.vi_meaning;`
     `effective_context = (item.custom_context_sentence != null && !item.custom_context_sentence.isBlank()) ? item.custom_context_sentence : post_context.context_sentence;`

---

## 4. Kien truc Giao dien Trang `/dictionary`

Trang chia lam 3 phan khu (Tab Navigation):
1. **Tab 1 - "So tu & Decks cua toi" (Personal Notebook):**
   - Hien thi danh sach cac Deck (Thu muc dang luoi the giong Quizlet).
   - Nut "Tao Deck moi", "Them tu thu cong".
   - Bam vao tung Deck de xem danh sach the tu, loc theo trang thai (Dang hoc / Da nho), va nut "Luyen tap Flashcard theo Deck nay".
2. **Tab 2 - "Tu dien tong hop toan he thong" (Global Lexicon):**
   - Thanh tim kiem thong minh voi Autocomplete Prefix Search.
   - Bo loc theo trinh do CEFR (A2, B1, B2) va chu de van hoa.
   - Moi the tu co nut "Them nhanh vao So tu ca nhan".
3. **Tab 3 - "On tap hom nay" (SRS Due Reviews):**
   - Danh sach cac the tu co `next_review_at <= NOW()`.
   - Giao dien Flashcard 2 mat danh gia nhi phan ("Da nho" / "Can on lai") de cap nhat tien do SRS.
