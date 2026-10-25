# Context Retrieval & In-Context Injection Architecture for AI Companion

## 1. Tong Quan (Overview)
Tai lieu nay quy dinh kien truc va dac ta ky thuat cho tinh nang Chatbox (AI Companion) su dung mo hinh Context Injection ket hop PostgreSQL Full-Text Search (Phuong an 1) thay the cho kien truc RAG phuc tap (Vertex AI RAG Engine + Cloud Spanner).

---

## 2. Phan Loai Che Do Tro Chuyen (Chat Modes)

He thong ho tro 2 che do hoat dong chinh:

### Che do A: Lesson-Scoped Chat (Hoi thoai trong boi canh bai hoc cu the)
- **Dieu kien kich hoat:** Client gui kem `lessonId`.
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

## 3. Dac Ta API Contract

### Endpoint
- **URL:** `POST /api/v1/companion/chat`
- **Authentication:** Bearer Token (hoac Session ID cho Anonymous Free Tier).

### Request DTO: `CompanionChatRequest`
```json
{
  "lessonId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "message": "Why do people in Hanoi eat Pho with quay?",
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

### Response DTO: `CompanionChatResponse`
```json
{
  "reply": "Eating Pho with quay (crispy fried dough sticks) is a classic Hanoi habit. The crispy quay absorbs the flavorful beef broth, creating a rich and satisfying texture.",
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

## 4. Kiem Soat Han Muc & Chi Phi (Quota & Rate Limiting)
- Tham chieu: `docs/00_core/system_constants.md`
- **TIER_FREE:** Gioi han toi da 3 luot chat / ngay. Moi request kiem tra va giam bo dem `daily_chat_turns` trong user profile hoac Redis/Cache.
- **TIER_TRIAL / TIER_PREMIUM:** Khong gioi han so luot chat.
- Khi vuot qua han muc: Tra ve loi `403 Forbidden` kem ma loi `LIMIT_EXCEEDED` va goi y nang cap len Pro.

---

## 5. System Prompt Template cho Gemini

```text
You are VieCultures Cultural Companion, a warm, culturally knowledgeable, and encouraging language partner.
Your mission is to help learners explore Vietnamese culture (traditions, food, heritage) while practicing English comfortably.

[CONTEXT DATA FROM DATABASE]
{retrieved_lesson_context}

[CONSTRAINTS]
1. Answer in natural, friendly English suitable for CEFR A2-B2 learners. If the user asks in Vietnamese, respond in bilingual format or natural English with clear explanations.
2. Ground your factual knowledge in [CONTEXT DATA FROM DATABASE]. If the information is not in the context, give a concise cultural summary and politely suggest related topics.
3. Keep answers under 150 words per turn to avoid overwhelming the user in a chat interface.
4. Always conclude with 1 engaging discussion question to maintain learning momentum.
```
