# 📖 [Interface] Domain Reader & Listening

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Bước 2 & Bước 4)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`AudioSpeedConstant`, `ContentBandLevel`)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`ReadingPost`, `ParagraphPair`)

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `01_domain_reader` chịu trách nhiệm:
1. Hiển thị nội dung bài đọc song ngữ đối xứng 1:1, tự thích ứng trên Desktop (2 cột) và Mobile (xếp chồng).
2. Quản lý trình phát âm thanh tự nhiên Sticky Audio Player với 3 tốc độ chuẩn (`1x`, `0.8x`, `0.5x`).
3. Cung cấp chế độ luyện nghe chép câu (Dictation Mode) với cơ chế khớp từ thời gian thực.
4. Đảm bảo tiêu chuẩn biên tập văn hóa bền vững, cấu trúc 3 Level và quy tắc Phản đề ở Level 3.

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`paragraph_pairing.md`](./paragraph_pairing.md): Quy chuẩn kỹ thuật đối xứng đoạn 1:1 và chế độ hiển thị Responsive.
2. [`natural_audio_dictation.md`](./natural_audio_dictation.md): Luồng âm thanh tự nhiên, dải tốc độ và chế độ nghe chép DailyDictation.
3. [`editorial_guidelines.md`](./editorial_guidelines.md): Bộ quy chuẩn biên soạn 15 bài mẫu 3 miền, không tường thuật báo chí, tính trường tồn và quy tắc Phản đề Level 3.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Gửi sự kiện sang `02_domain_vocab_flashcards`:** Khi người dùng click vào từ vựng được highlight ➔ Bắn event `onWordSelect(wordId, contextSentence)` để mở Tooltip và cho phép 1-Click Save.
- **Nhận dữ liệu từ `00_core`:** Nhận `lessonId`, `AudioSpeedConstant`, `level`.
- **Gửi sự kiện hoàn thành sang `00_core`:** Bắn event `onReadingCompleted(lessonId)` khi người học đã đọc hết các đoạn văn và nghe audio.
