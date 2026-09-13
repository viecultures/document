# 📜 Quy Tắc Nghiệp Vụ BR-04: Ôn Tập Flashcard 2 Mặt & Đánh Giá Nhị Phân

## 1. Mục Đích & Phạm Vi
Quy định cơ chế học chủ động qua thẻ ghi nhớ (Flashcards), cấu trúc 2 mặt thẻ, quy trình tự đánh giá và đo lường tiến độ ghi nhớ từ vựng trên ứng dụng **VN Culture Reader**.

---

## 2. Các Quy Tắc Nghiệp Vụ Cốt Lõi (Core Business Rules)

### BR-04.1: Cấu Trúc Thẻ Nhớ 2 Mặt Bắt Buộc (Mandatory Two-Sided Flashcard Rules)
Mỗi Flashcard đại diện cho một thực thể `VocabItem` và bắt buộc phải tuân thủ cấu trúc hiển thị 2 mặt như sau:

- **Mặt 1: Mặt Định Danh (Front Side - Identification)**
  - Hiển thị: **Từ vựng học thuật** (ví dụ: *Architectural*).
  - Bắt buộc đi kèm: **Câu ngữ cảnh gốc (Context Sentence)** được trích xuất từ bài đọc (ví dụ: *"The citadel displays unique architectural features of the Nguyen Dynasty."*).
  - Mục đích: Kích thích trí nhớ của người học thông qua ngữ cảnh bài học đã từng trải nghiệm.

- **Mặt 2: Mặt Giải Nghĩa (Back Side - Definition & Linguistics)**
  - Hiển thị: Phiên âm IPA (ví dụ: */ˌɑːrkɪˈtektʃərəl/*), Từ loại (ví dụ: *adj.*), Nghĩa tiếng Việt (ví dụ: *thuộc kiến trúc*).
  - Đính kèm: **Nút phát âm thanh AI** (`audio_url`) chuẩn bản xứ.

### BR-04.2: Quy Trình Ôn Tập & Đánh Giá Nhị Phân (Binary Self-Assessment Rules)
- **Quy tắc 4.2.1**: Sau khi lật sang Mặt 2 (Mặt Giải Nghĩa), hệ thống yêu cầu người dùng tự đo lường mức độ ghi nhớ thông qua **nút đánh giá nhị phân duy nhất với 2 giá trị**:
  1. 🟢 **"Đã nhớ" (Mastered)**
  2. 🔴 **"Cần ôn lại" (Needs Review)**
- **Quy tắc 4.2.2**: Cấm sử dụng hệ thống đánh giá 4-5 cấp độ phức tạp (như *Again / Hard / Good / Easy* của Anki) nhằm giữ trải nghiệm học tập đơn giản, không gây mệt mỏi nhận thức (cognitive fatigue).

### BR-04.3: Cập Nhật Trạng Thái & Tiến Độ (Progress Tracking & Queue Logic)
- **Quy tắc 4.3.1**: Khi chọn 🟢 **"Đã nhớ"**: Từ vựng được tăng điểm ghi nhớ, đánh dấu trạng thái *Mastered* cho bài học đó và giảm tần suất lặp lại.
- **Quy tắc 4.3.2**: Khi chọn 🔴 **"Cần ôn lại"**: Từ vựng sẽ giữ nguyên trạng thái *Learning*, tự động chèn lại vào cuối hàng chờ ôn tập (Review Queue) của phiên học hiện tại để người dùng luyện tập lại ngay.

---

## 3. Giao Diện Minh Họa Flashcard (Flashcard UI Anatomy)

```
FRONT SIDE (Mặt Trước):
+-------------------------------------------------------+
|  architectural                                        |
|  (adj)                                                |
|                                                       |
|  "The citadel displays unique architectural           |
|   features of the Nguyen Dynasty."                    |
|                                                       |
|                     [ 🔄 Lật mặt ]                    |
+-------------------------------------------------------+

BACK SIDE (Mặt Sau):
+-------------------------------------------------------+
|  /ˌɑːrkɪˈtektʃərəl/             [ 🔊 Nghe âm thanh ]  |
|  Nghĩa: Thuộc kiến trúc                               |
|                                                       |
|  ---------------------------------------------------  |
|  Tự đánh giá ghi nhớ:                                 |
|     [ 🔴 Cần ôn lại ]          [ 🟢 Đã nhớ ]          |
+-------------------------------------------------------+
```

---

## 4. Tác Động Đến Các Bộ Phận (Cross-Functional Impact)

- 🎨 **UI/UX Designer**: Thiết kế hiệu ứng lật thẻ (Flip Animation) mượt mà trên Mobile Web App. Nút *Cần ôn lại* và *Đã nhớ* bố trí to, rõ ràng ở vùng chạm ngón tay cái (Thumb Zone).
- ⚙️ **Backend Dev**: Xây dựng bảng lưu trữ tiến độ `UserVocabProgress` với trạng thái `status: 'learning' | 'mastered'` và `last_reviewed_at`.
- 📊 **Business / Marketing**: Đưa thông điệp "Học từ vựng theo ngữ cảnh đơn giản với 1 click tự đánh giá" vào các chiến dịch truyền thông.
