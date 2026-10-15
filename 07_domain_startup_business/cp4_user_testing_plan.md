# 🧪 Kế Hoạch Kiểm Thử Người Dùng Checkpoint 4 (User Testing Plan - CP4)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_business.md`](./interface_business.md)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`CP4_MIN_TESTERS: 20`, `CP4_MIN_BUGS_FIXED: 3`, `AudioSpeeds: ['1x', '0.8x', '0.5x']`)
- Căn cứ thực hiện: Rubric chấm điểm Checkpoint 4 (Notice 4).

---

## 2. Tiêu Chí Đánh Giá Bắt Buộc (Notice 4 Rubric)

| Tiêu Chí | Yêu Cầu Cụ Thể | Cách Thức Đáp Ứng Của VieCultures |
| :--- | :--- | :--- |
| **User Testing** | Kiểm thử với **ít nhất 20 người dùng mục tiêu**; nộp kèm file kết quả Excel gốc. | Tuyển 25–30 sinh viên (19–24 tuổi, CEFR A2–B2) trải nghiệm trên Web Demo Vercel, điền Google Form khảo sát. |
| **Fix >= 3 Problems** | Khắc phục ít nhất 3 vấn đề phát sinh từ người dùng và chứng minh Before/After. | Lập bảng theo dõi 3 lỗi trọng tâm, quay video/chụp ảnh minh chứng trước và sau khi fix. |
| **Demo All Roles** | Trình diễn luồng chính của từng vai trò người dùng trong lớp học. | Demo luồng Free User (bài đọc cơ bản) và Premium User (đầy đủ tốc độ audio, AI đàm thoại không giới hạn). |

---

## 3. Kịch Bản Kiểm Thử (5 Nhiệm Vụ Trải Nghiệm)

Người tham gia mở link [Web Demo](https://frontend-olive-chi-8de2fo4jbr.vercel.app/) và thực hiện lần lượt:
1. **Nhiệm vụ 1:** Chọn 1 bài đọc văn hóa ở Level 2 tại trang chủ.
2. **Nhiệm vụ 2:** Đọc bài song ngữ, chuyển đổi tốc độ audio `1x`, `0.8x`, `0.5x` và bấm vào 1 câu đơn để nghe đọc nhại (Shadowing).
3. **Nhiệm vụ 3:** Bấm vào từ vựng được highlight, xem giải nghĩa và bấm nút **"Lưu từ" (1-Click Save)**.
4. **Nhiệm vụ 4:** Chuyển sang Flashcard, lật thẻ xem câu ngữ cảnh và bấm tự đánh giá 🟢 *"Đã nhớ"* hoặc 🔴 *"Cần ôn lại"*.
5. **Nhiệm vụ 5:** Mở AI Map hỏi 1 câu về nét văn hóa của bài học hoặc thử tính năng Dictation.

---

## 4. Danh Mục 3 Vấn Đề Trọng Tâm Cần Sửa Đổi (Fix >= 3 Problems)

```
┌────────────────────────────────────────────────────────────────────────┐
│ VẤN ĐỀ 1: ĐIỀU HƯỚNG TỪ READER SANG FLASHCARD MANG THEO DỮ LIỆU BÀI HỌC│
├────────────────────────────────────────────────────────────────────────┤
│ • Trước khi sửa (Before): Nút "Sang Flashcard" mở bộ thẻ tổng thay vì  │
│   bộ thẻ của chính bài học người dùng vừa đọc.                         │
│ • Sau khi sửa (After): Nối state `lessonId` và từ vựng vừa lưu trực    │
│   tiếp vào phiên ôn Flashcard; người học ôn ngay các từ vừa gặp.      │
│ • Minh chứng: Video quay lại thao tác Before/After & Code commit diff. │
├────────────────────────────────────────────────────────────────────────┤
│ VẤN ĐỀ 2: ĐIỀU KHIỂN TỐC ĐỘ AUDIO & HIGHLIGHT CÂU ĐANG ĐỌC             │
├────────────────────────────────────────────────────────────────────────┤
│ • Trước khi sửa (Before): Nút chỉnh tốc độ audio chưa mượt mà trên     │
│   Mobile; người học khó nhận biết câu đang phát thanh trên màn hình nhỏ.│
│ • Sau khi sửa (After): Sticky Audio Player cố định với 3 nút bấm nhanh │
│   [1x] [0.8x] [0.5x], tự động highlight viền câu tiếng Anh đang đọc.   │
│ • Minh chứng: Ảnh chụp màn hình Responsive Mobile Before/After.        │
├────────────────────────────────────────────────────────────────────────┤
│ VẤN ĐỀ 3: CẢI THIỆN ĐỘ TRỄ & HƯỚNG DẪN CẤU HÌNH GEMINI API KEY         │
├────────────────────────────────────────────────────────────────────────┤
│ • Trước khi sửa (Before): Người học bối rối khi chatbox báo lỗi quota. │
│ • Sau khi sửa (After): Bổ sung hướng dẫn 3 bước kèm link lấy key; tích │
│   hợp sẵn các câu hỏi mẫu gợi ý (Quick Prompts) để bấm là chạy.       │
│ • Minh chứng: Modal cấu hình API Key thân thiện & Gợi ý đàm thoại.     │
└────────────────────────────────────────────────────────────────────────┘
```
