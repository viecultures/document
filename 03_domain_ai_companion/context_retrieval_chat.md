# Context Retrieval & In-Context Injection Architecture for AI Companion

## 1. Tong Quan (Overview)
Tai lieu nay quy dinh kien truc va dac ta ky thuat cho tinh nang Chatbox (AI Companion) su dung mo hinh Context Injection ket hop PostgreSQL Full-Text Search thay the cho kien truc RAG phuc tap (Vertex AI RAG Engine + Cloud Spanner).

Tai lieu cap nhat quy dinh bo sung ho tro da ngon ngu (Bilingual Companion: 'vi', 'en', 'bilingual'), dich thuat van hoa inline va co che luu tru lich su hoi thoai (Chat History Persistence) da tang.

---

## 2. Phan Loai Che Do Tro Chuyen (Chat Modes)

He thong ho tro 2 che do hoat dong chinh:

### Che do A: Lesson-Scoped Chat (Hoi thoai trong boi canh bai hoc cu the)
- **Dieu kien kich hoat:** Client gui kem `lessonId` hop le.
- **Luong xu ly du lieu:**
  1. Backend truy van entity `ReadingPost` va danh sach `ParagraphPair` tuong ung qua `ReadingPostRepository`.
  2. Trich xuat cac truong: `title_en`, `title_vi`, `topic`, `region`, `summary`, va noi dung song ngu cua cac doan van.
  3. Truyen truc tiep toan bo noi dung bai hoc vao system prompt cua Google Gemini API.
  4. Mo hinh dong vai Cultural Companion giai thich tu vung, ngu canh van hoa va dan dat nguoi hoc luyen tieng Anh xoay quanh bai doc.

### Che do B: Global Cultural Chat (Hoi thoai kham pha van hoa toan he thong)
- **Dieu kien kich hoat:** `lessonId` la `null` hoac nguoi dung mo hop thoai companion tai trang chu / ban do kham pha.
- **Luong xu ly du lieu:**
  1. Backend phan tich cau hoi cua nguoi dung (keyword / entity extraction).
  2. Thuc hien truy van tren PostgreSQL su dung Full-Text Search hoac JPA Specification tren bang `reading_posts` (quet qua `title_en`, `title_vi`, `topic`, `summary`) de lay top 1 - 3 bai viet lien quan nhat.
  3. Neu tim thay bai viet: Inject tieu de va `summary` cua cac bai nay lam can cu du lieu cho Gemini tra loi, dong thoi tra kem metadata (`referencedLessons`) de frontend hien thi link goi y doc them.
  4. Neu khong tim thay bai viet phu hop: Kich hoat quy trinh du phong theo tai lieu `fallback_mechanisms.md` (tra loi khai quat, tu choi kheo leo ve kho du lieu chua co bai chi tiet va dua ra 2-3 cau hoi thao luan mo).

---

## 3. Dac Ta Hop Dong API (API Contracts)

### 3.1. Gui tin nhan hoi thoai (Send Chat Message)
- **URL:** `POST /api/v1/companion/chat`
- **Authentication:** Bearer Token (hoac Session ID cho Khach vang lai).

#### Request DTO: `CompanionChatRequest`
```json
{
  "lessonId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "message": "Tai sao nguoi Ha Noi thuong an pho kem quay nong?",
  "language": "bilingual",
  "history": [
    {
      "role": "user",
      "content": "Hello, I want to learn about Hanoi cuisine."
    },
    {
      "role": "assistant",
      "content": "Welcome! Hanoi is famous for Pho, Bun Cha, and Cha Ca La Vong. What dish would you like to explore?"
    }
  ]
}
```
*Ghi chu truong:*
- `lessonId` (String, Optional): UUID cua bai doc. Neu null, he thong chay theo Che do B (Global).
- `message` (String, Required): Noi dung tin nhan nguoi dung. Toi da 1000 ky tu.
- `language` (String, Optional): Gia tri hop le gom `vi`, `en`, `bilingual`. Mac dinh la `bilingual`.
- `history` (Array, Optional): Danh sach toi da 6 luot tin nhan gan nhat de duy tri ngu canh ngan han.

#### Response DTO: `CompanionChatResponse`
```json
{
  "reply": "An pho kem quay la mot thoi quen dac trung cua nguoi Ha Noi. Quay gion rum ngam nuoc dung beo ngot tao nen huong vi kho quen.\n\nEating Pho with crispy fried dough sticks (quay) is a classic Hanoi tradition. The crunchy quay absorbs the flavorful beef broth, creating a deeply satisfying texture.",
  "language": "bilingual",
  "suggestedPrompts": [
    "Have you ever tried crispy quay with hot broth?",
    "Do you prefer Pho Bo or Pho Ga in Hanoi?"
  ],
  "referencedLessons": [
    {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "title": "Pho Hanoi - The Essence of Northern Broth"
    }
  ],
  "remainingDailyTurns": 2
}
```

---

### 3.2. Dich thuat van hoa tuc thi (Cultural Inline Translation)
- **URL:** `POST /api/v1/companion/translate`
- **Authentication:** Bearer Token hoac Session ID.

#### Request DTO: `CompanionTranslateRequest`
```json
{
  "text": "Nuoc dung pho bo Ha Noi phai trong, ngot thanh vi xuong ong ham ky cung que, hoi va gung nuong.",
  "sourceLanguage": "vi",
  "targetLanguage": "en",
  "culturalContext": "Hanoi Traditional Culinary Heritage"
}
```
*Ghi chu truong:*
- `text` (String, Required): Van ban can dich. Toi da 2000 ky tu.
- `sourceLanguage` (String, Optional): `vi` hoac `en`. Neu null, he thong tu dong phat hien.
- `targetLanguage` (String, Required): `en` hoac `vi`.
- `culturalContext` (String, Optional): Boi canh van hoa hoac chu de bai hoc de toi uu do chuan xac cua ban dich.

#### Response DTO: `CompanionTranslateResponse`
```json
{
  "originalText": "Nuoc dung pho bo Ha Noi phai trong, ngot thanh vi xuong ong ham ky cung que, hoi va gung nuong.",
  "translatedText": "Traditional Hanoi beef Pho broth must remain clear, carrying a naturally delicate sweetness extracted from long-simmered marrow bones infused with cinnamon, star anise, and charred ginger.",
  "sourceLanguage": "vi",
  "targetLanguage": "en",
  "culturalNotes": [
    "Ngot thanh: Refers to a gentle, clear, non-greasy sweetness typical of Northern Vietnamese culinary philosophy.",
    "Gung nuong: Charred ginger, a crucial technique used to eliminate beef odor and elevate the fragrance."
  ]
}
```

---

### 3.3. Lay lich su hoi thoai (Get Chat History)
- **URL:** `GET /api/v1/companion/history`
- **Authentication:** Bearer Token (Bat buoc).
- **Query Parameters:**
  - `lessonId` (String, Optional): Loc theo bai hoc cu the. Neu khong truyen, tra ve phien Global Chat.
  - `page` (Integer, Optional, Default: 0): So trang.
  - `size` (Integer, Optional, Default: 20): So luong tin nhan tren mot trang.

#### Response DTO: `CompanionHistoryResponse`
```json
{
  "sessionId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "lessonId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "page": 0,
  "size": 20,
  "totalElements": 8,
  "totalPages": 1,
  "messages": [
    {
      "id": "b1eebc99-9c0b-4ef8-bb6d-6bb9bd380a22",
      "role": "user",
      "content": "Why do people in Hanoi eat Pho with quay?",
      "language": "en",
      "createdAt": "2026-10-25T09:15:30Z"
    },
    {
      "id": "c2eebc99-9c0b-4ef8-bb6d-6bb9bd380a33",
      "role": "assistant",
      "content": "Eating Pho with quay is a classic Hanoi habit...",
      "language": "en",
      "createdAt": "2026-10-25T09:15:33Z"
    }
  ]
}
```

---

### 3.4. Luu hoac dong bo lich su hoi thoai (Save/Sync Chat History)
- **URL:** `POST /api/v1/companion/history`
- **Authentication:** Bearer Token (Bat buoc).
- **Muc dich:** Ho tro dong bo tin nhan tu Guest LocalStorage len Backend sau khi dang nhap.

#### Request DTO: `CompanionHistorySyncRequest`
```json
{
  "lessonId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "messages": [
    {
      "role": "user",
      "content": "What is the origin of Dan Ca Quan Ho?",
      "language": "en",
      "createdAt": "2026-10-25T09:00:00Z"
    },
    {
      "role": "assistant",
      "content": "Quan Ho folk singing originated in Bac Ninh and Bac Giang provinces...",
      "language": "en",
      "createdAt": "2026-10-25T09:00:04Z"
    }
  ]
}
```

#### Response DTO: `CompanionHistorySyncResponse`
```json
{
  "sessionId": "a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11",
  "syncedCount": 2,
  "status": "SUCCESS",
  "message": "Chat history synced successfully."
}
```

---

### 3.5. Xoa lich su hoi thoai (Clear Chat History)
- **URL:** `DELETE /api/v1/companion/history`
- **Authentication:** Bearer Token (Bat buoc).
- **Query Parameters:**
  - `lessonId` (String, Optional): Neu truyen UUID, xoa lich su cua phien bai hoc do. Neu truyen `all` hoac bo trong, xoa toan bo tat ca phien hoi thoai cua nguoi dung do.

#### Response DTO: `CompanionHistoryDeleteResponse`
```json
{
  "deletedCount": 14,
  "status": "SUCCESS",
  "message": "Chat history deleted successfully."
}
```

---

## 4. Mo Hinh Du Lieu Quan Ly Lich Su (Database Persistence Model)

He thong luu tru thong qua 2 bang PostgreSQL:

### Bang `companion_chat_sessions`
- `id` (UUID, Primary Key, Default: `gen_random_uuid()`)
- `user_id` (UUID, Foreign Key -> `users.id`, Not Null, Indexed)
- `lesson_id` (UUID, Foreign Key -> `reading_posts.id`, Nullable, Indexed)
- `session_type` (VARCHAR(32): `LESSON_SCOPED`, `GLOBAL`, Not Null)
- `language_preference` (VARCHAR(16): `vi`, `en`, `bilingual`, Default: `bilingual`)
- `created_at` (TIMESTAMP WITH TIME ZONE, Default: `NOW()`)
- `updated_at` (TIMESTAMP WITH TIME ZONE, Default: `NOW()`)
- `is_active` (BOOLEAN, Default: `TRUE`)

*Constraint:* UNIQUE(`user_id`, `lesson_id`) cho cac phien dang hoat dong (`is_active = TRUE`).

### Bang `companion_chat_messages`
- `id` (UUID, Primary Key, Default: `gen_random_uuid()`)
- `session_id` (UUID, Foreign Key -> `companion_chat_sessions.id`, On Delete Cascade, Indexed)
- `role` (VARCHAR(16): `user`, `assistant`, Not Null)
- `content` (TEXT, Not Null)
- `language` (VARCHAR(16): `vi`, `en`, `bilingual`)
- `created_at` (TIMESTAMP WITH TIME ZONE, Default: `NOW()`, Indexed)

---

## 5. Kiem Soat Han Muc, Bao Mat va Rate Limiting

### Han muc (Quota Management)
- **Khach vang lai (Guest):** Toi da 3 luot hoi dap / ngay. Giam tru theo IP va Client Session Token qua Redis Cache.
- **TIER_FREE (Da dang nhap):** Toi da 5 luot chat / ngay. Luu tru day du lich su chat vao Database.
- **TIER_PREMIUM / TRIAL:** Khong gioi han so luot chat va tinh nang dich thuat.
- Khi het han muc: Tra ve loi HTTP `403 Forbidden` kem error code `DAILY_LIMIT_EXCEEDED`.

### Quy tac bao mat va cach ly du lieu (Data Isolation & Security)
1. **Tenant / User Isolation:** Moi truy van lich su (`GET`, `POST`, `DELETE`) deu phai trich xuat `userId` tu JWT Token xac thuc. Khong cho phep nguoi dung truy cap hoac xoa session cua nguoi dung khac.
2. **XSS & Input Sanitization:** Tat ca noi dung tin nhan truoc khi luu vao DB hoac gui vao Prompt phai duoc lam sach bang HTML Sanitizer de chong tan cong Prompt Injection va Cross-Site Scripting.
3. **Prompt Leakage Prevention:** Cac huong dan he thong trong system prompt khong duoc tiet lo cho nguoi dung duoi bat ky cau lenh yeu cau nao (System Instruction Protection).

---

## 6. System Prompt Templates cho Gemini

### Template A: Companion Chat Prompt (Ho tro 3 che do ngon ngu)
```text
You are VieCultures Cultural Companion, a warm, culturally knowledgeable, and encouraging language partner.
Your mission is to help learners explore Vietnamese culture (traditions, food, heritage, people) while practicing English comfortably.

[TARGET LANGUAGE MODE]
{target_language_mode}
- If "vi": Respond entirely in natural, evocative Vietnamese with rich cultural vocabulary. English translations of terms should be placed in parentheses if helpful.
- If "en": Respond entirely in natural, fluent English (CEFR A2-B2 level).
- If "bilingual": Provide your response structured into bilingual sections (Vietnamese first, followed by clear English counterpart, with shared cultural nuance).

[CONTEXT DATA FROM DATABASE]
{retrieved_lesson_context}

[CONSTRAINTS]
1. Ground your factual knowledge in [CONTEXT DATA FROM DATABASE]. If the information is not in the context, give a concise cultural summary and politely suggest related topics.
2. Keep answers under 150 words per turn to avoid overwhelming the user in a chat interface.
3. Always conclude with 1 engaging discussion question to maintain learning momentum.
4. Maintain a warm, welcoming tone that celebrates Vietnamese heritage.
```

### Template B: Cultural Contextual Translation Prompt
```text
You are VieCultures Cultural Translator, an expert in preserving cultural authenticity and subtle nuances between Vietnamese and English.

[TASK]
Translate the given text from {source_language} to {target_language}.
Contextual Topic: {cultural_context}

[CONSTRAINTS]
1. Never produce raw or literal word-by-word machine translations.
2. Accurately translate Vietnamese cultural idioms, culinary items, and historical practices while retaining the original emotional warmth.
3. If translating culinary or cultural terms into English, keep the original name with a concise descriptive English explanation (e.g., "Banh mi (Vietnamese baguette)", "Nuoc dung (simmered broth)").
4. Output JSON format:
{
  "translatedText": "...",
  "culturalNotes": [
    "Note 1 explaining nuanced phrase",
    "Note 2 explaining cooking technique or historical origin"
  ]
}
```
