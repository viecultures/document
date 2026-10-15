# 🏆 [Interface] Domain Động Lực Học Tập & Thói Quen (Gamification & Retention)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Bước 7)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md)
- Triết lý sản phẩm: Gamification đóng vai trò ghi nhận sự nỗ lực và củng cố cảm xúc tự hào văn hóa, không biến việc học thành áp lực điểm số cày cuốc.

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `05_domain_gamification` chịu trách nhiệm:
1. Duy trì chuỗi ngày học liên tục (Daily Streak) nhằm hình thành thói quen tiếp xúc tiếng Anh hàng ngày.
2. Trao tặng **Mộc son văn hóa (Cultural Seal)** khi người học hoàn thành trọn vẹn một bài học di sản.
3. Cung cấp lời nhận xét khích lệ từ **Mascot đồng hành** ở màn hình tổng kết phiên học.
4. Cập nhật hồ sơ năng lực cá nhân (số bài đã đọc, số từ nắm vững).

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`habit_tracking.md`](./habit_tracking.md): Quy tắc tính Daily Streak, nghi thức đóng Mộc son văn hóa và thẻ kỷ niệm Mascot.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Nhận từ `00_core`:** Nhận event hoàn thành phiên học `onLearningSessionFinished(lessonId, stats)`.
- **Giao tiếp với `07_domain_startup_business`:** Cung cấp chỉ số giữ chân người dùng (Retention Rate, DAU/WAU) phục vụ đo lường hiệu quả kinh doanh.
