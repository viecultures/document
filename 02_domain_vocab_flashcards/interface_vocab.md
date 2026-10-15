# 🗃️ [Interface] Domain Từ Vựng Ngữ Cảnh & Ôn Tập Flashcard

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Bước 3 & Bước 5)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`VocabItem`, `UserVocabProgress`)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`TIER_FREE`, `TIER_PREMIUM`)

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `02_domain_vocab_flashcards` chịu trách nhiệm:
1. Quản lý việc hiển thị tooltip tra cứu từ vựng học thuật trực tiếp trên bài đọc.
2. Thực thi tính năng **1-Click Save**: Lưu từ vựng kèm câu ngữ cảnh gốc (`context_sentence`) vào sổ tay cá nhân.
3. Tổ chức phiên ôn tập thẻ nhớ 2 mặt với cơ chế tự đánh giá nhị phân 🟢 *"Đã nhớ"* / 🔴 *"Cần ôn lại"*.
4. Điều phối thuật toán Spaced Repetition (Lặp lại ngắt quãng) và xử lý hàng đợi thẻ nhớ.

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`context_extraction.md`](./context_extraction.md): Quy tắc tra cứu popup tức thì, bắt buộc câu gốc và thao tác 1 chạm.
2. [`spaced_repetition.md`](./spaced_repetition.md): Đặc tả thẻ nhớ 2 mặt, cơ chế tự đánh giá nhị phân và thuật toán hàng đợi ôn tập.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Nhận từ `01_domain_reader`:** Nhận event `onWordSelect(wordId, contextSentence)` khi người dùng click vào từ vựng được highlight.
- **Gửi sự kiện sang `00_core`:** Bắn event `onFlashcardsCompleted(lessonId, masteredCount, reviewCount)` khi người học đã đánh giá hết các thẻ của bài.
- **Giao tiếp với `07_domain_startup_business`:** Kiểm tra hạn mức lưu từ (người dùng Free tối đa 30 từ, người dùng Premium/Trial không giới hạn theo `system_constants.md`).
