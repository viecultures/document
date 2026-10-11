# 🗺️ Lộ Trình Phát Triển & Mô Hình Kinh Doanh (Product Roadmap & Business Model)

> **Dự án:** VieCultures  
> **Nguyên tắc hành động:** *"Kiểm chứng giả định trước khi xây dựng – Tối ưu hóa tính khả thi của MVP trước khi mở rộng quy mô."*

---

## 1. Lộ Trình Triển Khai Thực Tế Sau Checkpoint 1 (Post-CP1 Execution Plan)

Kế hoạch hành động chi tiết theo tuần và tháng được phân bổ như sau:

```
Tuần 1–2          Tuần 3–4          Tháng thứ 2       Tháng thứ 3       Hậu Kiểm Chứng
┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│ Khảo sát &   │  │ Thiết kế     │  │ Xây dựng     │  │ Thử nghiệm   │  │ Mở rộng Thư  │
│ Phỏng vấn sâu│─▶│ Wireframe &  │─▶│ Cốt lõi      │─▶│ Closed Beta  │─▶│ viện, AI &   │
│ 18–25 tuổi   │  │ 10 bài mẫu   │  │ Web MVP      │  │ 50–100 SV    │  │ Mobile App   │
└──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘
```

### Giai Đoạn 1: Nghiên Cứu & Kiểm Chứng Người Dùng (Tuần 1 – Tuần 2)
- **Mục tiêu:** Kiểm chứng 3 giả định về nỗi đau (nội dung xa lạ, đứt mạch đọc do tra từ, thiếu vốn từ văn hóa) và thói quen học tập.
- **Hành động cụ thể:**
  - Tiến hành phỏng vấn sâu trực tiếp 30+ sinh viên đại học trong tệp khách hàng mục tiêu.
  - Phổ biến bảng khảo sát trực tuyến tới 150+ người trẻ từ 18–25 tuổi (trình độ CEFR A2–B2).
  - Hoàn thiện bảng phân tích đối thủ cạnh tranh (Competitor Benchmark).
- **Kết quả bàn giao (Deliverables):** Báo cáo kết quả khảo sát thực tế (User Research Findings Report).

### Giai Đoạn 2: Thiết Kế Giao Diện & Chuẩn Bị Nội Dung Mẫu (Tuần 3 – Tuần 4)
- **Mục tiêu:** Chốt cấu trúc giao diện và xây dựng kho dữ liệu thử nghiệm ban đầu.
- **Hành động cụ thể:**
  - Hoàn thiện bản vẽ Wireframe chi tiết cho 3 màn hình chính: Trang chủ/Khám phá, Màn hình đọc bài song ngữ, và Màn hình ôn Flashcard.
  - Biên soạn và hiệu đính 10 bài đọc văn hóa song ngữ mẫu (kèm tệp âm thanh bản ngữ và danh sách từ vựng trích xuất có câu ngữ cảnh gốc).
  - Chuẩn hóa Design System theo phong cách Di sản Ấm áp (*Warm Heritage Editorial*).
- **Kết quả bàn giao (Deliverables):** Bộ Wireframe & Prototype Figma + Kho dữ liệu 10 bài đọc mẫu.

### Giai Đoạn 3: Lập Trình Bản Web MVP Cốt Lõi (Tháng thứ 2)
- **Mục tiêu:** Hai kỹ sư phần mềm nội bộ (Luân, Cường) xây dựng sản phẩm web hoạt động đầy đủ tính năng cốt lõi.
- **Hành động cụ thể:**
  - Lập trình giao diện đọc song ngữ (Paragraph-Pairing Reader) hỗ trợ Desktop (2 cột) và Mobile (xếp chồng).
  - Tích hợp popup tra cứu từ vựng ngữ cảnh và tính năng 1-click Save từ vựng.
  - Xây dựng module ôn tập Flashcard 2 mặt kèm tính năng tự đánh giá nhị phân.
  - Thiết lập cơ sở dữ liệu lưu trữ tài khoản và tiến độ học tập của người dùng.
- **Kết quả bàn giao (Deliverables):** Bản Web MVP hoàn chỉnh, có thể truy cập trực tuyến.

### Giai Đoạn 4: Thử Nghiệm Kín & Thu Thập Phản Hồi (Tháng thứ 3 - Closed Beta)
- **Mục tiêu:** Đo lường mức độ tương tác và độ bám giữ chân người dùng (Retention).
- **Hành động cụ thể:**
  - Mời 50–100 sinh viên đại học tham gia trải nghiệm bản Closed Beta trong 2 tuần.
  - Đo lường các chỉ số then chốt: Tỷ lệ đọc hết bài, số từ vựng được lưu, tỷ lệ hoàn thành vòng ôn tập Flashcard.
  - Thu thập góp ý về độ mượt mà của giao diện và tính chuẩn xác của các câu ngữ cảnh.
- **Kết quả bàn giao (Deliverables):** Báo cáo phản hồi người dùng & Bản cập nhật tối ưu trải nghiệm (UX Polish).

### Giai Đoạn 5: Mở Rộng Thư Viện & Tính Năng Nâng Cao (Sau Kiểm Chứng Thành Công)
- Mở rộng kho nội dung lên 50+ bài đọc bao phủ các tỉnh thành, di sản văn hóa và ẩm thực 3 miền.
- Tích hợp tính năng AI xác nhận và phản hồi phát âm giọng đọc của người học.
- Mở rộng dòng cảm nghĩ cộng đồng (Reflections - UGC) với chính sách không phán xét.
- Phát triển ứng dụng Native Mobile (iOS/Android) có thông báo đẩy chu kỳ ôn tập Spaced Repetition.
- Khởi động chế độ học văn hóa cho du khách nước ngoài (Inbound Tourism Mode).

---

## 2. Mô Hình Kinh Doanh & Chiến Lược Doanh Thu (Freemium Model)

VieCultures áp dụng mô hình **Freemium** bền vững, chia làm 2 phân tầng người dùng:

| Hạng mục | Tài khoản Miễn Phí (Free Tier) | Tài khoản Cao Cấp (Premium Tier - Giả định) |
| :--- | :--- | :--- |
| **Mục đích** | Thu hút người dùng, lan tỏa giá trị cộng đồng | Tối ưu hóa trải nghiệm & Tạo nguồn thu bền vững |
| **Nội dung đọc** | Toàn bộ bài đọc văn hóa cơ bản | Thư viện chuyên sâu không giới hạn theo tỉnh thành |
| **Công cụ từ vựng** | Tra cứu ngữ cảnh & Lưu tối đa 30 từ | Lưu từ vựng không giới hạn, tạo sổ tay cá nhân |
| **Ôn tập Flashcard** | Ôn tập theo từng bài học vừa đọc | Ôn tập tổng hợp theo thuật toán Spaced Repetition |
| **Trải nghiệm học** | Kèm quảng cáo hiển thị nhẹ nhàng | Trải nghiệm hoàn toàn **Không quảng cáo** |
| **Ngoại tuyến** | Chỉ dùng trực tuyến (Online) | Hỗ trợ tải bài đọc & Audio học ngoại tuyến (Offline) |
| **Tính năng AI** | Nghe giọng đọc bản ngữ chuẩn | Ưu tiên thử nghiệm tính năng AI phân tích phát âm |

### Nguồn Thu Bổ Trợ
1. **Tiếp thị Liên kết Văn hóa (Affiliate Marketing):** Hợp tác với các đơn vị tổ chức tour du lịch di sản, bảo tàng, workshop làng nghề và nhà xuất bản sách học tiếng Anh.
2. **Quảng cáo Hiển thị Nhẹ (Display Ads):** Các banner quảng cáo tinh tế ở chân trang dành cho người dùng miễn phí, cam kết không gây ảnh hưởng đến mạch đọc bài học.
