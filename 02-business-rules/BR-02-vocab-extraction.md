# 📜 Quy Tắc Nghiệp Vụ BR-02: Trích Xuất & Quản Lý Từ Vựng Trong Ngữ Cảnh

## 1. Mục Đích & Phạm Vi
Quy định phương pháp trích xuất, cấu trúc dữ liệu và điều kiện bắt buộc đối với từ vựng học thuật trong dự án **VN Culture Reader**.

---

## 2. Các Quy Tắc Nghiệp Vụ Cốt Lõi (Core Business Rules)

### BR-02.1: Tự Động Trích Xuất Từ Vựng Học Thuật (Automatic Academic Vocab Extraction)
- **Quy tắc 2.1.1**: Hệ thống phải tự động phân tích và trích xuất các **từ khóa học thuật trọng tâm** (Key Academic Vocabulary - thuộc trình độ từ B1 đến C2 hoặc các từ chuyên ngành văn hóa/lịch sử) từ văn bản bài đọc tiếng Anh.
- **Quy tắc 2.1.2**: Các từ vựng trích xuất sẽ trở thành các **thực thể dữ liệu độc lập** (`VocabItem`), có thể tái sử dụng cho các tính năng Flashcards và Reflections.

### BR-02.2: Bắt Buộc Lưu Trữ Câu Ngữ Cảnh Gốc (Mandatory Context Sentence Requirement)
- **Quy tắc 2.2.1**: Mọi thực thể từ vựng (`VocabItem`) **bắt buộc phải lưu trữ kèm theo nguyên văn câu chứa từ đó** trong bài đọc gốc (`context_sentence`).
- **Quy tắc 2.2.2**: **Cấm tuyệt đối** lưu trữ một từ vựng độc lập mà không có câu ngữ cảnh gốc. Nếu thiếu câu ngữ cảnh gốc, hệ thống coi dữ liệu từ vựng đó là **không hợp lệ** và không cho phép xuất bản lên ứng dụng.

### BR-02.3: Các Trường Dữ Liệu Thành Phần Của Từ Vựng (Vocab Entity Attributes)
Một thực thể từ vựng hợp lệ phải bao gồm đầy đủ 5 thành phần dữ liệu sau:
1. `word`: Từ gốc (ví dụ: *Architectural*).
2. `ipa`: Phiên âm quốc tế IPA (ví dụ: */ˌɑːrkɪˈtektʃərəl/*).
3. `pos`: Từ loại (ví dụ: *adj.*).
4. `vi_meaning`: Nghĩa tiếng Việt trong ngữ cảnh bài học (ví dụ: *thuộc về kiến trúc*).
5. `context_sentence`: Nguyên văn câu chứa từ trong bài đọc (ví dụ: *"The citadel displays unique architectural features of the Nguyen Dynasty."*).

---

## 3. Ví Dụ Cấu Trúc Dữ Liệu Chuẩn (Standard JSON Schema)

```json
{
  "vocab_id": "voc_hue_001",
  "word": "architectural",
  "ipa": "/ˌɑːrkɪˈtektʃərəl/",
  "pos": "adj",
  "vi_meaning": "thuộc kiến trúc",
  "context_sentence": "The citadel displays unique architectural features of the Nguyen Dynasty.",
  "audio_url": "https://cdn.vnculturereader.com/audio/vocab/architectural.mp3"
}
```

---

## 4. Tác Động Đến Các Bộ Phận (Cross-Functional Impact)

- 🤖 **AI Agent / Backend**: Khi xử lý tự động bài đọc mới, pipeline của AI phải thực hiện 2 bước: 
  1. Detect từ vựng khó.
  2. Bắt cặp chính xác câu chứa từ đó trong bài (`context_sentence`).
- 🎨 **Frontend / UI**: Trên giao diện bài đọc, các từ vựng học thuật sẽ được gạch chân hoặc highlight nhẹ. Khi người dùng bấm/hover vào từ, một popup nhỏ (Tooltip Card) sẽ xuất hiện hiển thị đầy đủ thông tin từ vựng và câu ngữ cảnh.
