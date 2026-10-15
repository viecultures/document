# 📌 Trích Xuất Từ Vựng Ngữ Cảnh & Lưu Từ 1 Chạm (Context Extraction & 1-Click Save)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_vocab.md`](./interface_vocab.md)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`VocabItem`)
- Tham chiếu Ngoại lệ: [`edge_cases_and_validation.md`](../00_core/edge_cases_and_validation.md) (`EC-02.1`, `EC-02.2`, `EC-02.3`)

---

## 2. Nguyên Tắc Cốt Lõi: Ngữ Cảnh Là Số 1 (Context First)

1. **Tuyệt đối không học từ vựng trơ trọi:**
   - Người học tiếng Anh thường nhanh quên nếu chỉ học từ vựng riêng lẻ kèm nghĩa tiếng Việt.
   - Mọi từ vựng trích xuất bắt buộc phải gắn liền với nguyên văn câu chứa từ đó trong bài đọc (`context_sentence`).
2. **Hỗ trợ cụm từ cố định (Multi-word Expressions):**
   - Cho phép trích xuất các cụm từ vựng văn hóa, phrasal verbs, idioms (ví dụ: *intangible cultural heritage*, *take place*, *passed down through generations*).

---

## 3. Thao Tác 1 Chạm (1-Click Save Interaction)

1. **Popup Tra Cứu Tức Thì (Interactive Vocab Tooltip):**
   - Người học bấm trực tiếp vào từ vựng được highlight trên văn bản bài đọc.
   - Thẻ Tooltip hiển thị ngay lập tức (không chuyển app, không mở tab mới) gồm:
     - Từ gốc (`word`)
     - Phiên âm quốc tế (`ipa`)
     - Từ loại (`pos`)
     - Nghĩa tiếng Việt trong ngữ cảnh (`vi_meaning`)
     - Loa phát âm từ đơn (`audio_url`)
     - Nút **"Lưu từ" (1-Click Save)**
2. **Cơ chế lưu sổ tay cá nhân:**
   - Khi bấm "Lưu từ", hệ thống tự động lưu `word_id` cùng `context_sentence` vào sổ tay từ vựng của người dùng (`UserVocabProgress`).
   - Nút chuyển trạng thái sang `[✓ Đã lưu]`.
