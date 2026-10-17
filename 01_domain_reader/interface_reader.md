# 📖 [Interface] Domain Reader & Listening

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Bước 2 & Bước 4)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`AudioSpeedConstant`, `ContentBandLevel`)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`ReadingPost`, `ParagraphPair`, `QuizQuestion`)

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `01_domain_reader` chịu trách nhiệm:
1. Hiển thị nội dung bài đọc song ngữ đối xứng 1:1, tự thích ứng trên Desktop (2 cột) và Mobile (xếp chồng).
2. Quản lý trình phát âm thanh tự nhiên Sticky Audio Player với 3 tốc độ chuẩn (`1x`, `0.8x`, `0.5x`).
3. Cung cấp chế độ luyện nghe chép câu (Dictation Mode) với cơ chế khớp từ thời gian thực.
4. Triển khai hệ thống Bộ câu hỏi đọc hiểu (Comprehension Check Quiz) nhằm kiểm tra mức độ thấu hiểu văn hóa và nội dung bài đọc của người học.
5. Đảm bảo tiêu chuẩn biên tập văn hóa bền vững, cấu trúc 3 Level và quy tắc Phản đề ở Level 3.

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`paragraph_pairing.md`](./paragraph_pairing.md): Quy chuẩn kỹ thuật đối xứng đoạn 1:1 và chế độ hiển thị Responsive.
2. [`natural_audio_dictation.md`](./natural_audio_dictation.md): Luồng âm thanh tự nhiên, dải tốc độ và chế độ nghe chép DailyDictation.
3. [`editorial_guidelines.md`](./editorial_guidelines.md): Bộ quy chuẩn biên soạn 15 bài mẫu 3 miền, không tường thuật báo chí, tính trường tồn và quy tắc Phản đề Level 3.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Gửi sự kiện sang `02_domain_vocab_flashcards`:** Khi người dùng click vào từ vựng được highlight ➔ Bắn event `onWordSelect(wordId, contextSentence)` để mở Tooltip và cho phép 1-Click Save.
- **Nhận dữ liệu từ `00_core`:** Nhận `lessonId`, `AudioSpeedConstant`, `level`.
- **Hợp đồng dữ liệu câu hỏi đọc hiểu (`QuizQuestion` API Contract):**
  - Cung cấp danh sách câu hỏi trắc nghiệm thấu hiểu đi kèm các lựa chọn (`options`), khóa đáp án (`correct_key`) và phần giải thích ý nghĩa văn hóa (`explanation`) cho mỗi bài đọc.
  - Cơ chế phản hồi kết quả đọc hiểu: Tiếp nhận đáp án người dùng gửi lên, trả về trạng thái đúng/sai kèm theo `explanation` để tăng cường trải nghiệm học tập phản hồi tức thì (Immediate Feedback).
- **Gửi sự kiện hoàn thành sang `00_core`:** Bắn event `onReadingCompleted(lessonId)` khi người học đã hoàn thành bài đọc, nghe audio và vượt qua bài kiểm tra đọc hiểu (Comprehension Check Quiz).
