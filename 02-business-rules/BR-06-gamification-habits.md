# 📜 Quy Tắc Nghiệp Vụ BR-06: Gamification & Thói Quên Học Tập (Habit Loop)

> [!NOTE]
> **ĐỘ ƯU TIÊN THẤP / TÙY CHỌN (LOW PRIORITY / OPTIONAL)**
>
> Các tính năng trong tài liệu này là các phương án bổ sung nhằm gia tăng độ bám giữ chân người dùng (Retention). Team phát triển có thể ưu tiên làm sau khi đã hoàn thiện các tính năng cốt lõi (Reading, Dictation, Flashcard).

---

## 1. Mục Đích & Phạm Vi
Quy định cơ chế game hóa (Gamification), đếm chuỗi ngày học liên tiếp (Streak), tính điểm kinh nghiệm (EXP), bảng xếp hạng tuần và thử thách cộng đồng cho ứng dụng **VN Culture Reader**.

---

## 2. Các Quy Tắc Nghiệp Vụ (Business Rules)

### BR-06.1: Chuỗi Ngày Học Liên Tiếp (Daily Streak)
- **Quy tắc 6.1.1**: Người dùng được tính 1 ngày học hợp lệ (Streak +1) khi hoàn thành **ít nhất 1 trong các hoạt động**:
  - Đọc hoàn chỉnh 1 bài đọc song ngữ.
  - Hoàn thành nghe chép chính tả (Dictation) ít nhất 3 câu.
  - Ôn tập tối thiểu 5 thẻ Flashcard.
- **Quy tắc 6.1.2**: Streak tự động reset về 0 nếu người dùng không thực hiện hoạt động nào trong vòng 24 giờ (từ 00:00 đến 23:59 theo múi giờ địa phương).

### BR-06.2: Quy Tắc Tính Điểm Kinh Nghiệm (EXP Calculation)
- **Quy tắc 6.2.1**: Điểm EXP được cộng dồn dựa trên các hành động học tập thực tế:
  - Hoàn thành 1 bài đọc: `+20 EXP`.
  - Gõ đúng 100% 1 câu Dictation (không cần bấm Show Full Answer): `+10 EXP`.
  - Ôn thành công 1 thẻ Flashcard (*Đã nhớ* hoặc *Good/Easy*): `+5 EXP`.
  - Đăng 1 bài cảm nghĩ Reflection hợp lệ: `+15 EXP`.

### BR-06.3: Bảng Xếp Hạng Tuần (Weekly Leaderboard)
- **Quy tắc 6.3.1**: Bảng xếp hạng tổng hợp danh sách Top 20 người dùng có tổng điểm EXP cao nhất trong tuần.
- **Quy tắc 6.3.2**: Bảng xếp hạng tự động làm mới (Reset) vào lúc 00:00 Chủ Nhật hàng tuần.

### BR-06.4: Thử Thách Viết Tuần (Weekly Writing Challenge)
- **Quy tắc 6.4.1**: Mỗi tuần, team Marketing đưa ra 1 chủ đề tranh luận / cảm nghĩ văn hóa (*"Is Ao Dai suitable for daily work?"*).
- **Quy tắc 6.4.2**: Người dùng tham gia bằng cách đăng bài Reflection đính kèm hashtag thử thách (`#WeeklyChallenge`). Bài viết nhận được nhiều thả tim nhất tuần sẽ nhận huy hiệu vinh danh.

---

## 3. Tác Động Đến Các Bộ Phận (Cross-Functional Impact)

- 🎨 **UI/UX Designer**: Thiết kế Widget Streak (biểu tượng ngọn lửa) trên Topbar và Bảng xếp hạng Leaderboard mượt mà.
- ⚙️ **Backend Dev**: Xây dựng bảng `UserGamification` (lưu `streak_count`, `total_exp`, `last_active_date`) và CRON Job tổng hợp Leaderboard tuần.
- 📊 **Marketing**: Sử dụng kết quả Leaderboard và Weekly Challenge làm nội dung truyền thông trên mạng xã hội.
