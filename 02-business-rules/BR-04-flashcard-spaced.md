# Quy Tắc Nghiệp Vụ BR-04: Ôn Tập Flashcard 2 Mặt & Thuật Toán Lặp Ngắt Quãng

## 1. Mục Đích & Phạm Vi
Quy định cơ chế thẻ ghi nhớ 2 mặt, quy trình tự đánh giá nhị phân và thuật toán nhắc ôn tập tự động (Spaced Repetition).

---

## 2. Các Quy Tắc Nghiệp Vụ Cốt Lõi (Core Business Rules)

### BR-04.1: Cấu Trúc Thẻ Nhớ 2 Mặt Bắt Buộc
- **Mặt 1 (Mặt Định Danh)**: Hiển thị từ vựng + Câu ngữ cảnh gốc trích xuất từ bài đọc.
- **Mặt 2 (Mặt Giải Nghĩa)**: Hiển thị phiên âm IPA, từ loại, nghĩa tiếng Việt và nút phát âm thanh AI.

### BR-04.2: Chiến Lược Ôn Tập 2 Giai Đoạn (2-Phase Flashcard Strategy)

Hệ thống ôn tập từ vựng được lộ trình hóa theo 2 giai đoạn phát triển:

- **Giai đoạn 1: Đánh Giá Nhị Phân Đơn Giản (Binary Self-Assessment)**
  - Người dùng tự đo lường mức độ ghi nhớ sau khi lật sang Mặt 2 thông qua **2 nút đánh giá nhị phân duy nhất**:
    1. 🔴 **"Cần ôn lại" (Needs Review)**: Đánh dấu từ ở trạng thái `learning`, tự động chèn lại vào cuối hàng chờ phiên học.
    2. 🟢 **"Đã nhớ" (Mastered)**: Đánh dấu từ ở trạng thái `mastered`, tăng điểm ghi nhớ bài học.
  - Mục đích: Giữ trải nghiệm đơn giản, không gây mệt mỏi nhận thức (cognitive fatigue).

- **Giai đoạn 2: Thuật Toán Spaced Repetition Chuẩn Anki (SuperMemo-2 / SM-2)**
  - Nâng cấp giao diện lật mặt sau với **4 mức độ tự đánh giá chuẩn Anki/SuperMemo-2**:
    1. 🔴 **Again (1 ngày)**: Quên hoàn toàn từ vựng.
    2. 🟠 **Hard (Khoảng cách ngắn)**: Nhớ ngập ngừng, tốn nhiều thời gian.
    3. 🔵 **Good (Khoảng cách tiêu chuẩn)**: Nhớ tốt sau vài giây suy nghĩ.
    4. 🟢 **Easy (Khoảng cách dài)**: Nhớ ngay lập tức mà không cần suy nghĩ.
  - **Thuật toán SM-2 tự động tính toán**:
    - `interval`: Khoảng cách số ngày lặp lại lần kế tiếp.
    - `repetitions`: Số lần lặp lại thành công liên tiếp.
    - `ease_factor`: Hệ số độ dễ của từ vựng (mặc định 2.5, điều chỉnh theo từng phản hồi).
    - `next_review_at`: Ngày chính xác người dùng cần mở app ôn lại thẻ này.

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

BACK SIDE - GIAI ĐOẠN 1 (Binary Assessment):
+-------------------------------------------------------+
|  /ˌɑːrkɪˈtektʃərəl/             [ 🔊 Nghe âm thanh ]  |
|  Nghĩa: Thuộc kiến trúc                               |
|  ---------------------------------------------------  |
|  Tự đánh giá ghi nhớ:                                 |
|     [ 🔴 Cần ôn lại ]          [ 🟢 Đã nhớ ]          |
+-------------------------------------------------------+

BACK SIDE - GIAI ĐOẠN 2 (Anki SM-2 Spaced Repetition):
+-------------------------------------------------------+
|  /ˌɑːrkɪˈtektʃərəl/             [ 🔊 Nghe âm thanh ]  |
|  Nghĩa: Thuộc kiến trúc                               |
|  ---------------------------------------------------  |
|  Chọn mức độ ghi nhớ (SM-2 Algorithm):                |
|  [ 🔴 Again ]  [ 🟠 Hard ]  [ 🔵 Good ]  [ 🟢 Easy ]  |
|   (1 ngày)      (3 ngày)     (6 ngày)     (12 ngày)   |
+-------------------------------------------------------+
```

---

## 4. Tác Động Đến Các Bộ Phận (Cross-Functional Impact)

- 🎨 **UI/UX Designer**: Thiết kế giao diện lật thẻ (Flip Animation) mượt mà. Đảm bảo hỗ trợ cả 2 nút Binary (Giai đoạn 1) và nâng cấp responsive lên 4 nút SM-2 (Giai đoạn 2).
- ⚙️ **Backend Dev**:
  - Giai đoạn 1: Quản lý bảng `UserVocabProgress` với `status: 'learning' | 'mastered'`.
  - Giai đoạn 2: Bổ sung logic tính toán toán học SM-2 (`interval`, `repetitions`, `ease_factor`, `next_review_at`).
- 📊 **Business / Marketing**: Truyền thông thông điệp "Học từ vựng theo ngữ cảnh kết hợp thuật toán lặp lại ngắt quãng Anki thông minh".


