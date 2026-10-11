# DANH SÁCH CHỨC NĂNG HỆ THỐNG (SYSTEM FEATURES SPECIFICATION)

> **Dự án:** VieCultures  
> **Phiên bản:** Cập nhật đồng bộ theo yêu cầu Checkpoint 1 (CP1)  
> **Nguyên tắc phân định:** Tách bạch rõ ràng giữa **Phạm vi Cốt lõi của Bản MVP** (tập trung 4–5 chức năng để hoàn thành tốt) và **Lộ trình Mở rộng Tương lai (Roadmap)** nhằm đảm bảo tính khả thi kỹ thuật và đáp ứng rubric chấm điểm.

---

## PHẦN I: PHẠM VI TÍNH NĂNG CỐT LÕI (CORE MVP SCOPE)

Nhóm 4–5 tính năng cốt lõi giải quyết trực tiếp 3 vấn đề (pain points) của người học:

### 1. Module Đọc Bài Song Ngữ Cặp Đoạn (Bilingual Reading & Audio)
- **1.1. Hiển thị Cặp Đoạn Song Ngữ (Paragraph-Pairing Reader):**
  - Hiển thị bài đọc tiếng Anh (nội dung chính) đối xứng 1:1 với đoạn dịch tiếng Việt (phụ trợ).
  - Tự động thích ứng giao diện: 2 cột song song trên Desktop và dạng Xếp chồng (Stacked) kèm nút bật/tắt bản dịch trên Mobile Web.
- **1.2. Phân loại theo Chủ đề & Trình độ (Topic & CEFR Filter):**
  - Lọc bài đọc theo các chủ đề văn hóa (Ẩm thực, Di sản, Lễ hội, Lối sống).
  - Phân cấp bài học theo các trình độ CEFR: A2, B1, B2.
- **1.3. Trình phát Âm thanh Bài học & Câu (Audio Player):**
  - Phát âm thanh đọc bài hoàn chỉnh cho toàn bài đọc.
  - Hỗ trợ nghe âm thanh câu đơn khi người dùng bấm trực tiếp vào câu tiếng Anh trong bài.

### 2. Module Trích Xuất & Lưu Từ Vựng Ngữ Cảnh (Contextual Vocabulary & 1-Click Save)
- **2.1. Thẻ Giải Nghĩa Nhanh Tương Tác (Interactive Vocab Tooltip):**
  - Nhấp trực tiếp vào từ vựng học thuật được highlight trên bài đọc để xem popup giải nghĩa tức thì mà không cần chuyển app từ điển.
  - Hiển thị: Từ gốc, Phiên âm quốc tế IPA, Từ loại, Nghĩa tiếng Việt trong ngữ cảnh và nút phát âm thanh từ.
- **2.2. Bắt Buộc Kèm Câu Ngữ Cảnh Gốc (Mandatory Context Sentence):**
  - Mỗi từ vựng trích xuất bắt buộc phải gắn liền với nguyên văn câu chứa từ đó trong bài đọc (`context_sentence`).
- **2.3. Lưu Từ Vựng Tức Thì (1-Click Save):**
  - Người dùng bấm nút "Lưu từ" trực tiếp từ popup để đưa vào danh sách sổ tay ôn tập cá nhân.

### 3. Module Ôn Tập Thẻ Nhớ Flashcard Ngữ Cảnh (Context Flashcards & Review)
- **3.1. Thẻ Nhớ 2 Mặt Gắn Ngữ Cảnh (Two-Sided Context Flashcard):**
  - **Mặt trước (Mặt Định danh):** Hiển thị từ vựng + nguyên văn câu ngữ cảnh gốc.
  - **Mặt sau (Mặt Giải nghĩa):** Hiển thị phiên âm IPA, từ loại, nghĩa tiếng Việt và âm thanh phát âm.
- **3.2. Cơ Chế Tự Đánh Giá Nhị Phân (Binary Self-Assessment):**
  - Sau khi lật mặt sau, người học chọn 1 trong 2 nút: 🟢 *"Đã nhớ"* (Mastered) hoặc 🔴 *"Cần ôn lại"* (Needs Review).
  - Thẻ được chọn *"Cần ôn lại"* sẽ tự động chèn vào cuối hàng chờ ôn của phiên học hiện tại.

### 4. Module Theo Dõi Tiến Độ Học Tập (Progress Tracking)
- **4.1. Quản Lý Trạng Thái Bài Đọc:**
  - Theo dõi bài đọc theo 3 trạng thái: *Chưa đọc*, *Đang đọc*, *Đã hoàn thành*.
  - Một bài học được tính là hoàn thành khi người dùng lật qua và tự đánh giá toàn bộ từ vựng Flashcard của bài.
- **4.2. Thống Kê Từ Vựng Cá Nhân:**
  - Bảng tổng kết số từ vựng đã học, số từ đã nắm vững và phân nhóm theo chủ đề văn hóa.

### 5. Module Khám Phá Văn Hóa & Ẩm Thực Vùng Miền (Regional Discovery)
- **5.1. Bản Đồ / Danh Mục Ẩm Thực & Đặc Sản Địa Phương:**
  - Cung cấp danh mục khám phá các món ăn truyền thống, nét sinh hoạt đặc trưng trên khắp 54 tỉnh thành / vùng miền Việt Nam.
  - Cung cấp cho người dùng những điều thú vị về văn hóa mà họ chưa từng biết để tìm kiếm bằng tiếng Anh.

---

## PHẦN II: LỘ TRÌNH MỞ RỘNG TƯƠNG LAI (ROADMAP / FUTURE LAYERS)

Các tính năng nâng cao dưới đây được xếp vào giai đoạn sau khi đã kiểm chứng (validate) thành công bản MVP:

### 6. Module AI Xác Nhận & Đánh Giá Phát Âm (AI Pronunciation Feedback)
- **6.1. Thu Âm Giọng Đọc Của Người Học:**
  - Cho phép người dùng thu âm lại câu đọc hoặc từ vựng của mình qua microphone (Web Speech API / Cloud AI Service).
- **6.2. AI Đánh Giá & Phản Hồi:**
  - AI so sánh giọng đọc của người học với giọng mẫu bản ngữ và đưa ra điểm số hoặc phản hồi mức độ chuẩn xác.

### 7. Module Cảm Nghĩ Cộng Đồng (Community Reflections & UGC)
- **7.1. Đăng Cảm Nghĩ Cá Nhân:**
  - Khung viết cảm nghĩ tự do sau khi đọc bài, tích hợp thanh công cụ gợi ý chèn nhanh từ vựng vừa học.
- **7.2. Chính Sách Môi Trường Học Tập Không Phán Xét (No-Judgment Policy):**
  - Tuyệt đối không áp dụng thuật toán chấm điểm hay sửa lỗi ngữ pháp trên bài viết của người học để giải tỏa rào cản tâm lý e ngại.
- **7.3. Tương Tác & Kiểm Duyệt:**
  - Thả tim động viên (Reactions), bộ lọc từ ngữ phản cảm và nút báo cáo vi phạm (Report).

### 8. Module Game Hóa & Thói Quen Học Tập (Gamification & Retention)
- **8.1. Chuỗi Ngày Học Liên Tiếp (Daily Streak):** Bộ đếm chuỗi ngày hoàn thành ít nhất 1 bài đọc hoặc 5 thẻ flashcard.
- **8.2. Hệ Thống Điểm Thưởng & Huy Hiệu (EXP & Badges):** Tích lũy điểm khi học bài và mở khóa các huy hiệu vinh danh văn hóa.
- **8.3. Bảng Xếp Hạng Tuần (Weekly Leaderboard):** Thi đua giữa cộng đồng học viên dựa trên điểm EXP tích lũy.

### 9. Module Du Khách Nước Ngoài (Inbound Tourism Mode)
- **9.1. Học Ngược Cho Khách Quốc Tế:**
  - Hướng dẫn khách du lịch nước ngoài cách phát âm tên riêng địa danh, món ăn đường phố (Phở, Bánh Mì, Bún Bò...) và các câu giao tiếp cơ bản khi du lịch Việt Nam qua lời giải thích bằng tiếng Anh.

### 10. Module Ứng Dụng Native Di Động & Ngoại Tuyến (Mobile Native & Offline)
- **10.1. Native Mobile App:** Phát triển ứng dụng chuyên biệt trên iOS & Android với thông báo đẩy chu kỳ ôn tập.
- **10.2. Chế Độ Ngoại Tuyến (Offline Mode):** Tải trước các gói bài đọc và âm thanh để học khi không có kết nối mạng.

### 11. Module Doanh Thu & Thương Mại Hóa (Monetization Engine)
- **11.1. Gói Đăng Ký Cao Cấp (Freemium Subscription):** Học không quảng cáo, mở khóa các gói chuyên đề độc quyền.
- **11.2. Tiếp Thị Liên Kết Văn Hóa (Affiliate Marketing):** Giới thiệu tour du lịch, sách học tiếng Anh, workshop văn hóa địa phương.
