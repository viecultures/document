# Đặc Tả Kỹ Thuật Phân Hệ Admin CMS Phase 3.1
## Màn Hình Tổng Quan Dashboard & Kênh Marketing Phân Phối Đa Nền Tảng

---

### 1. Kiến Trúc Màn Hình Tổng Quan (Overview Dashboard)

Màn hình Tổng quan (`/admin/dashboard`) đóng vai trò là tháp điều hành trung tâm (Central Operation Tower) dành cho Quản trị viên và Biên tập viên nền tảng VieCultures. Thiết kế tuân thủ ngôn ngữ **Warm Heritage** (giấy dó `#FAF6EE`, xanh di sản `#1D4A43`, vàng ánh đồng `#D9A05B`), trực quan hóa dữ liệu theo 3 hàng trọng yếu:

#### 1.1 Hàng 1: 4 Thẻ KPI Tăng Trưởng (Growth KPI Cards)
1. **Tổng học viên (Total Learners)**:
   - Dữ liệu: `totalUsers` lấy từ `adminOverviewService.getOverview()`.
   - Ý nghĩa: Quy mô cộng đồng người học đăng ký tài khoản trên nền tảng.
2. **Học viên hoạt động 7 ngày (7-Day Active Learners - WAU)**:
   - Dữ liệu: `activeLearnersWeek` đếm số `distinct` người dùng phát sinh nhật ký học tập trong 7 ngày gần nhất.
   - Ý nghĩa: Mức độ gắn kết thực tế của học viên với các nội dung học liệu.
3. **Tổng lượt đọc & Tỷ lệ bình quân (Total Reads & Precise Average)**:
   - Dữ liệu: `totalReads` và `avgReadsPerPost`.
   - **Quy tắc kỹ thuật**: Tỷ lệ đọc bình quân được hiển thị chính xác dưới dạng số thập phân tối thiểu 2 chữ số (ví dụ: `0.03 lượt/bài`), tuyệt đối không làm tròn số học thành `0`, đảm bảo tính minh bạch cho các bài viết mới xuất bản.
4. **Độ phủ học liệu đã xuất bản (Published Content Coverage)**:
   - Dữ liệu: `publishedPosts` trên `totalPosts` kèm tỷ lệ phần trăm hoàn tất kiểm duyệt.
   - Ý nghĩa: Tốc độ số hóa di sản và sẵn sàng phục vụ người học trên ứng dụng.

#### 1.2 Hàng 2: Phễu Chuyển Đổi & Phân Bổ Học Liệu Đa Chiều (2 Cột)
- **Cột trái: Phễu Chuyển Đổi Học Viên (Learner Conversion Funnel)**:
  Trực quan hóa 4 giai đoạn cốt lõi trong hành trình học tập văn hóa:
  1. *Khách truy cập web (Web Visitors)*: Học viên vãng lai tiếp cận bài viết qua tìm kiếm hoặc chiến dịch Marketing.
  2. *Đăng ký tài khoản (Account Signups)*: Chuyển đổi thành người dùng có tài khoản định danh.
  3. *Hoàn thành bài đầu tiên (First Lesson Completed)*: Học viên đọc hết đoạn văn song ngữ, nghe phát âm và trả lời câu hỏi phản tư.
  4. *Quay lại ngày 2 (Day-2 Retention)*: Học viên quay lại luyện từ vựng hoặc mở bài đọc tiếp theo trong lộ trình.
- **Cột phải: Phân Bổ Học Liệu CEFR (A1 - C2) & Vùng Miền (Interactive Distribution Bars)**:
  - Trực quan hóa độ bao phủ của kho bài viết theo chuẩn khung tham chiếu Châu Âu (CEFR: A1, A2, B1, B2, C1, C2) và 4 vùng văn hóa (Bắc Bộ, Trung Bộ, Nam Bộ, Toàn Quốc).
  - **Khả năng tương tác (Interactive Filtering)**: Mỗi thanh phân bổ đóng vai trò là một nút tắt thông minh. Khi quản trị viên nhấp vào mức độ CEFR hoặc tên vùng miền, giao diện tự động điều hướng sang tab `posts` với bộ lọc tương ứng đã được thiết lập sẵn.

#### 1.3 Hàng 3: Bảng Cảnh Báo "Bài Viết & Hành Trình Cần Chú Ý" (Readiness Attention Table)
- **Mục tiêu**: Hỗ trợ biên tập viên phát hiện ngay các nội dung học liệu chưa đạt chuẩn sư phạm trước khi tiếp cận học viên.
- **Tiêu chí lọc bài cần chú ý**:
  1. Bài viết đã kích hoạt xuất bản nhưng thiếu cặp đoạn văn song ngữ (`paragraphCount === 0`).
  2. Bài viết chưa có file âm thanh giọng đọc bản ngữ AI (`hasAudio === false`).
  3. Bài viết chưa biên soạn câu hỏi kiểm tra phản tư (`quizCount === 0`).
- **Thao tác nhanh**: Tích hợp nút `Bổ sung ngay` mở trực tiếp `PostFormModal` cho bài viết đó mà không cần qua nhiều bước tìm kiếm.

---

### 2. Kiến Trúc Phân Hệ Marketing & Đa Kênh (`/admin/marketing`)

Phân hệ Marketing được thiết kế bám sát định hướng triển khai tinh gọn trong `note_third_party.md`, hỗ trợ 4 phân vùng độc lập (đồng bộ qua URL query parameter `?tab=`):

```
/admin/marketing
├── ?tab=utm         -> 1. Tạo link UTM (Nội bộ - Lựa chọn hiện tại)
├── ?tab=analytics   -> 2. Google Analytics & Search Console
├── ?tab=broadcast   -> 3. Email & Bản tin di sản (Gmail SMTP Engine)
└── ?tab=social      -> 4. Mạng xã hội & Ads (Tích hợp tương lai)
```

#### 2.1 Phân Vùng 1: Tạo Link UTM Nội Bộ (`?tab=utm`)
- **Triết lý**: Theo dõi chuyển đổi qua UTM nội bộ hoàn toàn miễn phí, không phụ thuộc API bên thứ ba.
- **Cơ chế hoạt động**:
  - Biên tập viên chọn nội dung đích (Bài đọc hoặc Hành trình học), kênh phân phối (Facebook, TikTok, Google, Email, Zalo), nhập tên chiến dịch (`utm_campaign`) và nội dung mẩu tin (`utm_content`).
  - Hệ thống tự động tạo URL chuẩn: `https://viecultures.com/reading/{id}?utm_source=tiktok&utm_medium=social_video&utm_campaign=pho_hanoi`.
  - Hỗ trợ lưu trữ danh sách chiến dịch cục bộ (`localStorage`), sao chép 1-click vào khay nhớ tạm.
  - Khi học viên click link và đăng ký, hệ thống lưu `utm_source` và `utm_campaign` vào hồ sơ người dùng để phân tích hiệu quả kênh.

#### 2.2 Phân Vùng 2: Google Analytics & Search Console (`?tab=analytics`)
- **Thông số tích hợp thực tế (Cấu hình chính thức)**:
  - **GA4 Measurement ID**: `G-CTMMCTEFPM`
  - **GA4 Stream ID**: `16250918205`
  - **GA4 Stream Name**: `VieCultures Web`
  - **Stream URL**: `https://viecultures.app`
  - **Google Search Console Site URL**: `https://viecultures.com`
  - **Service Account Credentials**: Tích hợp khóa xác thực an toàn qua biến môi trường `GOOGLE_APPLICATION_CREDENTIALS="./service-account.json"`.
- **Giao diện quản trị**: Hiển thị bảng tổng hợp thông số kết nối, đoạn mã chèn thẻ `gtag.js` chuẩn xác, và hướng dẫn phân quyền Service Account vào Google Search Console.

#### 2.3 Phân Vùng 3: Email & Bản Tin Di Sản (`?tab=broadcast`)
- **Động cơ gửi mail Backend**: Tích hợp trực tiếp máy chủ Spring Boot qua 2 endpoint:
  1. `POST /api/v1/mail/send-notification`: Gửi email thông báo tùy biến và bản tin văn hóa với template HTML **Warm Heritage** sang trọng, nút hành động CTA và chữ ký thương hiệu.
  2. `POST /api/v1/mail/test-connection`: Kiểm tra kết nối nhanh (SMTP Ping) tới máy chủ Google Gmail SMTP thông qua Google App Password.
- **Tính năng giao diện**:
  - Biểu mẫu soạn thảo bản tin với tiêu đề, lời tựa nổi bật, nội dung bài viết, link nút bấm hành động.
  - Nút kiểm tra SMTP tức thì với phản hồi trạng thái kết nối thời gian thực.

#### 2.4 Phân Vùng 4: Mạng Xã Hội & Ads (`?tab=social`)
- **Định hướng theo `note_third_party.md`**:
  - **Cách 1 (Hiện tại)**: Tiếp tục phát huy công cụ tạo link UTM nội bộ để đo lường chuyển đổi organic và trả phí mà không tốn chi phí kết nối API.
  - **Cách 2 (Sắp ra mắt)**:
    - *Meta Business Graph API*: Hướng dẫn đăng ký Business App trên Meta for Developers, kết nối Ad Account ID và Access Token để đọc số tiền chi tiêu (Spend).
    - *Google Ads API*: Chuẩn bị hồ sơ đăng ký tài khoản MCC (My Client Center) và xin Developer Token từ Google.
    - *Webhook Tự Động Hóa*: Tích hợp webhook n8n hoặc Make qua biến môi trường `SOCIAL_CROSSPOST_WEBHOOK_URL="https://hook.eu1.make.com/xxxxxx"` để tự động đồng bộ bài viết mới lên các kênh mạng xã hội.

---

### 3. Chuẩn Hóa 100% Tiếng Việt Có Dấu Trên Toàn Bộ Phân Hệ /admin

Toàn bộ nhãn nút bấm, thông báo trạng thái, tiêu đề bảng, thông điệp phản hồi lỗi và chú thích thuộc các thành phần quản trị được chuẩn hóa tiếng Việt có dấu chuẩn ngữ pháp:
- **`AdminServiceConnections.tsx`**: Trạng thái kiểm tra kết nối API, CSDL PostgreSQL, Giọng đọc AI Neural TTS, Quyền quản trị viên.
- **`AdminActivityLogView.tsx`**: Nhãn cột, bộ lọc phân trang, tìm kiếm nhật ký, hiển thị chi tiết JSON Payload, thông báo sao chép.
- **`MarketingManagementView.tsx`**: Các trường nhập liệu, nút kiểm tra SMTP, danh sách chiến dịch đã tạo.
- **Dịch vụ TypeScript (`adminActivityLogService.ts`, `adminMailService.ts`)**: Chuẩn hóa thông điệp lỗi trả về giao diện người dùng.
- **Nguyên tắc biểu tượng**: 100% sử dụng vector SVG từ thư viện `lucide-react`, tuyệt đối không sử dụng icon emoji Unicode.
