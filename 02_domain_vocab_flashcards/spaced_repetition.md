# 🗂️ Ôn Tập Thẻ Nhớ 2 Mặt & Lặp Lại Ngắt Quãng (Flashcards & Spaced Review)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_vocab.md`](./interface_vocab.md)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`UserVocabProgress`)
- Tham chiếu Ngoại lệ: [`edge_cases_and_validation.md`](../00_core/edge_cases_and_validation.md) (`EC-04.1`, `EC-04.2`)

---

## 2. Thiết Kế Thẻ Nhớ 2 Mặt (Two-Sided Context Card)

Khác với các ứng dụng flashcard thông thường chỉ có từ vựng và nghĩa dịch, VieCultures đưa ngữ cảnh văn hóa vào trung tâm:

### A. Mặt Trước (Mặt Nhận Diện & Ngữ Cảnh)
- **Từ vựng / Cụm từ to rõ:** Nằm ở vị trí trung tâm.
- **Nguyên văn câu ngữ cảnh gốc (`context_sentence`):** In nghiêng ngay bên dưới, từ mục tiêu được highlight/gạch chân.
- **Mục tiêu:** Kích hoạt trí nhớ chủ động (Active Recall) bằng cách gợi nhớ lại tình huống trong bài đọc văn hóa.

### B. Mặt Sau (Mặt Giải Nghĩa & Phát Âm)
- **Phiên âm quốc tế IPA** và **Từ loại**.
- **Nghĩa tiếng Việt chuẩn ngữ cảnh bài đọc**.
- **Loa phát âm AI/Tự nhiên:** Tự động phát âm thanh từ khi lật mặt sau.

---

## 3. Cơ Chế Tự Đánh Giá Nhị Phân (Binary Self-Assessment)

Sau khi lật mặt sau, người học chọn 1 trong 2 nút điều khiển:
1. 🟢 **"Đã nhớ" (Mastered):**
   - Từ vựng được đánh dấu là nắm vững trong phiên học.
   - Thẻ được đưa ra khỏi hàng đợi của phiên học hiện tại.
2. 🔴 **"Cần ôn lại" (Needs Review):**
   - Thẻ được tự động chèn vào cuối hàng đợi ôn tập của phiên học để người học gặp lại lần nữa trước khi kết thúc bài.

> [!TIP]
> **Giới hạn lặp thẻ khó (`EC-04.1`):** Nếu một từ bị chọn *"Cần ôn lại"* quá **3 lần trong cùng 1 phiên học**, hệ thống sẽ dừng lặp thẻ đó và nhắc nhở: *"Từ này có vẻ khó với bạn, hãy đọc lại câu ngữ cảnh trong bài đọc!"* để tránh gây kiệt sức nhận thức (Cognitive Fatigue).
