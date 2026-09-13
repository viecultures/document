# Quy Trình Điều Hướng & Đề Xuất UI/UX Trang Chủ (Navigation & UX Discovery)

## 1. Đề Xuất UI/UX Cho Trang Khám Phá Bài Đọc (Discovery UX Proposal)
Đối với nền tảng EdTech học tiếng Anh qua văn hóa, mô hình UI/UX tối ưu nhất kết hợp giữa **Bộ lọc đa chiều (Filter Bar)** và **Bảng tin gợi ý cá nhân hóa (Personalized Feed)**:

```
+-----------------------------------------------------------------------+
| [ Logo VN Culture Reader ]  [ Subscribed Level: B1 ]  [ Avatar ]       |
+-----------------------------------------------------------------------+
| Filter: [ Tất cả Chủ đề ▾ ]  [ Trình độ: A2 | B1 | B2 | C1 ]          |
+-----------------------------------------------------------------------+
| 🌟 HERO BANNER: Bài Đọc Nổi Bật Tốt Nhất Tuần (Có ảnh đẹp Visual Hook) |
| "Khám phá di sản kiến trúc Cố đô Huế qua góc nhìn tiếng Anh B1"      |
+-----------------------------------------------------------------------+
| 📚 BÀI ĐỌC THEO TRÌNH ĐỘ B1 CỦA BẠN (Recommended Grid/List)            |
| [ Card 1: Bánh mì SG ]   [ Card 2: Phố cổ Hội An ]   [ Card 3: ... ]   |
+-----------------------------------------------------------------------+
| 📜 BÀI VIẾT CẢM NGHĨ CỘNG ĐỒNG MỚI NHẤT (Reflections Feed)            |
+-----------------------------------------------------------------------+
```

## 2. Cấu Trúc Sitemap Ứng Dụng
1. Trang Chủ / Khám phá (`/`)
2. Màn hình Chi tiết Bài đọc & Shadowing Player (`/lessons/:id`)
3. Màn hình Ôn tập Flashcard bài học (`/lessons/:id/flashcards`)
4. Màn hình Cảm nghĩ Cộng đồng (`/community` hoặc `/lessons/:id/reflections`)
5. Trang Cá nhân & Tiến độ học tập (`/profile`)
6. Trang Quản trị Web Admin (`/admin`)
