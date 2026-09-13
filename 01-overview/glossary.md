# 📖 Từ Điển Thuật Ngữ Hệ Thống (Glossary)

Tài liệu này chuẩn hóa ngôn ngữ giao tiếp giữa **Business, Marketing, Developers và AI Agents** để tránh hiểu nhầm trong quá trình thiết kế, lập trình và vận hành dự án **VN Culture Reader**.

---

## 1. Thuật Ngữ Nghiệp Vụ Chính (Core Business Terms)

| Thuật ngữ | Tên tiếng Anh | Định nghĩa / Ý nghĩa nghiệp vụ |
| :--- | :--- | :--- |
| **Cặp đoạn văn Song ngữ** | Paragraph Pairing | Cấu trúc lưu trữ và hiển thị nội dung bài đọc gồm 1 đoạn tiếng Anh (chính) và 1 đoạn tiếng Việt dịch tương ứng (phụ trợ). |
| **Âm thanh Shadowing** | Shadowing Audio Stream | Luồng âm thanh đọc chuẩn bản xứ do AI tạo ra đính kèm bài đọc, cho phép người dùng vừa nghe vừa nhại theo để luyện phát âm và ngữ điệu. |
| **Từ vựng Ngữ cảnh** | Contextual Vocabulary | Từ vựng học thuật trọng tâm được hệ thống trích xuất độc lập, **bắt buộc lưu kèm câu văn gốc chứa từ đó** trong bài đọc. |
| **Cảm nghĩ Bài đọc** | Reflection (UGC) | Bài viết ngắn của người dùng chia sẻ suy nghĩ cá nhân dựa trên bài học. Tuyệt đối **không áp dụng các thuật toán chấm điểm hay sửa lỗi ngữ pháp**. |
| **Chèn từ vựng nhanh** | Quick Vocab Insertion | Công cụ gợi ý trên giao diện cho phép người dùng click để chèn nhanh các từ vựng vừa học vào bài Reflection của mình. |
| **Nhận diện Từ vựng UGC** | UGC Vocab Detection | Cơ chế tự động quét và highlight các từ vựng học thuật xuất hiện trong bài viết Reflection của người dùng. |
| **Flashcard 2 mặt** | Two-Sided Flashcard | Thẻ nhớ bài học: **Mặt định danh** hiển thị từ vựng + câu ngữ cảnh gốc; **Mặt giải nghĩa** hiển thị phiên âm IPA, nghĩa tiếng Việt và âm thanh phát âm. |
| **Tự đánh giá Nhị phân** | Binary Self-Assessment | Cơ chế đo lường tiến độ học tập trên Flashcard với 2 lựa chọn duy nhất: *"Đã nhớ"* (Mastered) hoặc *"Cần ôn lại"* (Needs Review). |

---

## 2. Thuật Ngữ Dữ Liệu & Kỹ Thuật (Technical & AI Terms)

| Thuật ngữ | Ý nghĩa kỹ thuật |
| :--- | :--- |
| **`ReadingPost`** | Thực thể bài đọc (chứa các đoạn song ngữ, audio URL, danh sách từ vựng). |
| **`ParagraphPair`** | Sub-entity chứa đoạn văn tiếng Anh (`en_text`) và đoạn dịch tương ứng (`vi_text`). |
| **`VocabItem`** | Thực thể từ vựng (`word`, `ipa`, `vi_meaning`, `context_sentence`, `audio_url`). |
| **`UserReflection`** | Thực thể cảm nghĩ do người dùng tạo ra (`content`, `user_id`, `post_id`, `reactions_count`). |
| **`Lemmatization`** | Thuật toán biến đổi từInflected (ví dụ: *historical* -> *history*, *preserved* -> *preserve*) về dạng nguyên mẫu để nhận diện từ vựng học thuật trong bài viết của người dùng. |
