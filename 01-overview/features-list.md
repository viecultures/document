# DANH SÁCH CHỨC NĂNG HỆ THỐNG (SYSTEM FEATURES SPECIFICATION)

Tài liệu này tổng hợp toàn bộ các chức năng của hệ thống VN Culture Reader, phục vụ cho việc theo dõi, phát triển và nghiệm thu sản phẩm.

---

## 1. MODULE KHÁM PHÁ VÀ ĐỌC BÀI SONG NGỮ (READING & SHADOWING MODULE)

### 1.1. Bộ lọc và Tìm kiếm Bài đọc (Topic & Band Filter)
- Phân loại bài đọc theo Chủ đề văn hóa (Ẩm thực, Lịch sử, Danh lam thắng cảnh, Lễ hội, Đời sống).
- Phân loại bài đọc theo Cấp độ trình độ (CEFR / Band: A2, B1, B2, C1).
- Cho phép tìm kiếm bài đọc theo từ khóa và lọc kết hợp giữa Chủ đề x Trình độ.

### 1.2. Hiển thị Bài đọc Song ngữ Cặp đoạn văn (Paragraph Pairing Reader)
- Hiển thị bài đọc tiếng Anh (dữ liệu chính) đi kèm đoạn dịch tiếng Việt tương ứng (dữ liệu phụ trợ).
- Khớp tỷ lệ 1-1 giữa đoạn tiếng Anh và tiếng Việt theo chiều dọc.
- Tự động chuyển đổi giao diện: 2 cột song song trên Desktop và dạng Xếp chồng (Stacked) với nút bật/tắt bản dịch trên Mobile Web.
- Gắn hình ảnh bìa và minh họa văn hóa chất lượng cao cho từng bài đọc.

### 1.3. Trình phát Âm thanh AI Shadowing (Sentence & Lesson Audio Player)
- Phát âm thanh AI đọc chuẩn bản xứ cho toàn bộ bài đọc.
- Điều chỉnh tốc độ phát âm thanh (0.75x, 1.0x, 1.25x).
- Trình phát âm thanh theo từng câu (Sentence-level Audio): Bấm vào câu bất kỳ trong bài đọc để nghe âm thanh riêng của câu đó.

---

## 2. MODULE TRÍCH XUẤT VÀ XỬ LÝ TỪ VỰNG NGỮ CẢNH (CONTEXTUAL VOCABULARY MODULE)

### 2.1. Trích xuất Từ vựng Học thuật (Academic Vocab Extraction)
- Tự động nhận diện và trích xuất các từ vựng/cụm từ học thuật trọng tâm từ bài đọc.
- Lưu trữ thực thể từ vựng độc lập bao gồm: Từ gốc, Phiên âm IPA, Từ loại, Nghĩa tiếng Việt và file âm thanh đọc từ.

### 2.2. Bắt buộc Câu Ngữ cảnh Gốc (Mandatory Context Sentence)
- Mỗi từ vựng bắt buộc phải đính kèm nguyên văn câu chứa từ đó trong bài đọc gốc (`context_sentence`).
- Tự động highlight từ vựng học thuật trong văn bản bài đọc.

### 2.3. Thẻ Giải nghĩa Nhanh (Interactive Vocab Tooltip Card)
- Bấm hoặc rê chuột vào từ vựng được highlight trên bài đọc để mở popup giải nghĩa nhanh.
- Xem phiên âm, nghĩa tiếng Việt, câu ngữ cảnh và nút phát âm thanh từ vựng.

---

## 3. MODULE ÔN TẬP FLASHCARD VÀ LẶP NGẮT QUÃNG (FLASHCARD & SPACED REPETITION MODULE)

### 3.1. Thẻ Nhớ Flashcard 2 Mặt (Two-Sided Flashcard)
- Mặt 1 (Mặt định danh): Hiển thị từ vựng + Câu ngữ cảnh gốc.
- Mặt 2 (Mặt giải nghĩa): Hiển thị phiên âm IPA, từ loại, nghĩa tiếng Việt và âm thanh phát âm.
- Hiệu ứng lật thẻ (3D Flip Animation) hỗ trợ thao tác vuốt/bấm trên mobile và phím tắt trên desktop.

### 3.2. Cơ chế Tự đánh giá Nhị phân (Binary Self-Assessment)
- Đánh giá mức độ ghi nhớ sau khi lật mặt sau với 2 lựa chọn: "Đã nhớ" (Mastered) hoặc "Cần ôn lại" (Needs Review).
- Nếu chọn "Cần ôn lại", từ vựng tự động chèn lại vào cuối hàng chờ ôn tập của phiên hiện tại.

### 3.3. Thuật toán Lặp ngắt quãng (Spaced Repetition System)
- Xếp lịch tự động nhắc ôn tập lại các từ vựng "Đã nhớ" theo chu kỳ tăng dần: 1 ngày, 3 ngày, 7 ngày, 30 ngày.
- Gửi thông báo/nhắc nhở ôn tập khi đến chu kỳ để giữ chân người học.

---

## 4. MODULE CẢM NGHĨ CỘNG ĐỒNG VÀ UAG (COMMUNITY REFLECTIONS & UGC MODULE)

### 4.1. Đăng bài Cảm nghĩ (Reflection Creation)
- Mở khung viết cảm nghĩ cá nhân dựa trên bài đọc vừa hoàn thành.
- Tích hợp Thanh công cụ chèn nhanh từ vựng (Quick Vocab Insertion Toolbar) để người dùng click chèn từ vừa học vào văn bản.

### 4.2. Môi trường Học tập Không Phán xét (No-Judgment Policy)
- Tuyệt đối không áp dụng thuật toán chấm điểm hay sửa lỗi ngữ pháp trên bài viết Reflection.
- Tự động phân phối bài viết lên Dòng thời gian cộng đồng (Community Feed).

### 4.3. Kiểm duyệt và Tương tác Cộng đồng (Moderation & Engagement)
- Kiểm duyệt tự động bằng bộ lọc từ cấm (Automated Keyword Moderation) đối với các nội dung thù hận, vi phạm thuần phong mỹ tục hoặc nhạy cảm văn hóa.
- Tự động highlight từ vựng học thuật xuất hiện trong bài viết cảm nghĩ của người dùng (UGC Vocab Detection via Lemmatization).
- Thả tim (Reactions) và Lọc từ ngữ phản cảm ở phần bình luận.
- Nút Báo cáo vi phạm (Report) để người dùng gắn cờ bài viết không phù hợp.

---

## 5. MODULE TÀI KHOẢN VÀ TIẾN ĐỘ HỌC TẬP (USER ACCOUNT & PROGRESS MODULE)

### 5.1. Quản lý Tài khoản và Đăng nhập (Authentication & Profile)
- Bắt buộc đăng nhập để lưu trữ kết quả học tập.
- Quản lý thông tin cá nhân và thiết lập trình độ mặc định (A2, B1, B2, C1).

### 5.2. Theo dõi Tiến độ Học tập (Progress Tracking)
- Quản lý trạng thái bài đọc (Chưa đọc, Đang đọc, Đã hoàn thành).
- Tính điểm hoàn thành bài học khi lật qua 100% Flashcards của bài đó.
- Lưu trữ lịch sử từ vựng đã thuộc và danh sách từ vựng cần ôn lại.

---

## 6. MODULE QUẢN TRỊ WEB ADMIN VÀ CMS (WEB ADMIN & CONTENT MANAGEMENT MODULE)

### 6.1. Nhập liệu và Cấu hình Bài đọc (Lesson Content Management)
- Tạo mới, chỉnh sửa, xóa bài đọc song ngữ.
- Nhập các cặp đoạn văn tiếng Anh - tiếng Việt và tự động validation khớp 1:1.
- Gán chỉ số Phân loại Chủ đề và Trình độ Band.

### 6.2. Tải lên và Quản lý Media (Media & Audio Upload)
- Tải lên hoặc chèn liên kết file âm thanh AI Shadowing.
- Tải lên hình ảnh bìa và hình ảnh minh họa bài đọc.

### 6.3. Quản lý Từ vựng và Kiểm duyệt (Vocab & Moderation Management)
- Quản lý danh sách từ vựng trích xuất cho từng bài đọc.
- Danh sách bài viết Reflection bị gắn cờ hoặc chứa từ nhạy cảm chờ xử lý.

---

## 7. MODULE DOANH THU VÀ THƯƠNG MẠI (MONETIZATION MODULE)

### 7.1. Quảng cáo (In-App Display Ads)
- Hiển thị banner quảng cáo ở các vị trí cố định không ảnh hưởng đến trải nghiệm học bài.

### 7.2. Tiếp thị Liên kết (Affiliate Marketing)
- Tích hợp liên kết giới thiệu tour du lịch, sách văn hóa, tài liệu học tiếng Anh liên quan đến chủ đề bài học.

---

## 8. DANH SÁCH Ý TƯỞNG DỰ PHÒNG PHIÊN BẢN SAU (IDEAS BACKLOG)
Các chức năng dưới đây nằm trong danh sách ý tưởng mở rộng, chưa thuộc scope MVP:
- Ghi âm kiểm tra phát âm của người học và so sánh với AI.
- Dạy phát âm từ/tên riêng tiếng Việt cho người nước ngoài.
- Tải ảnh cá nhân và check-in địa điểm du lịch khi đăng Reflection.
- Lưu trữ lịch sử các bản ghi âm giọng đọc theo thời gian.
