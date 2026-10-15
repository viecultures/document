# 📌 Hằng Số Hệ Thống & Single Source of Truth (System Constants - SSOT)

> **Dự án:** VieCultures  
> **Vai trò tài liệu:** Nguồn chân lý duy nhất (Single Source of Truth - SSOT) định nghĩa toàn bộ các hằng số, tham số cấu hình, enum và bảng giá dùng chung trong toàn bộ hệ thống. Mọi tài liệu nghiệp vụ, giao diện và mã nguồn đều bắt buộc phải tham chiếu từ file này, tuyệt đối không tự định nghĩa lặp lại.

---

## 1. Dải Tốc Độ Âm Thanh (Audio Speeds Constant)

Được áp dụng thống nhất cho trình phát Sticky Player của Reader, Dictation và Shadowing:

| Tên Hằng Số | Giá Trị | Nhãn Hiển Thị (UI Label) | Ý Nghĩa Sử Dụng |
| :--- | :--- | :--- | :--- |
| `SPEED_NORMAL` | `1.0` | **`1x`** | Tốc độ chuẩn tự nhiên, luyện phản xạ giao tiếp đời sống |
| `SPEED_SLOW` | `0.8` | **`0.8x`** | Tốc độ chậm vừa phải, nhận diện rõ nối âm và ngữ điệu câu |
| `SPEED_VERY_SLOW` | `0.5` | **`0.5x`** | Tốc độ rất chậm, hỗ trợ nghe tách bạch từng âm tiết / từ khó |

> [!IMPORTANT]
> **Quy định bất biến:** Hệ thống chỉ hỗ trợ 3 tốc độ trên: `['1x', '0.8x', '0.5x']`. Tuyệt đối không bổ sung các dải tốc độ khác (`0.75x`, `1.2x`, `1.25x`) để tránh phân mảnh trải nghiệm người dùng.

---

## 2. Phân Cấp Trình Độ Bài Đọc (Content Banding Levels)

| Tên Cấp Độ | Mã Kỹ Thuật | Trình Độ CEFR Tương Ứng | Số Từ Trung Bình | Cấu Trúc Ngữ Pháp / Từ Vựng | Đặc Điểm Nhận Diện |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Level 1** | `LEVEL_1` | A2 – B1 | 150 – 200 từ (3–4 cặp đoạn) | Câu đơn & câu ghép cơ bản; từ vựng miêu tả đời sống | Dễ đọc, khơi gợi tò mò văn hóa |
| **Level 2** | `LEVEL_2` | B1 – B2 | 250 – 350 từ (4–6 cặp đoạn) | Câu phức, mệnh đề quan hệ; mở rộng phong tục | Bối cảnh di sản, làng nghề, lịch sử |
| **Level 3** | `LEVEL_3` | B2+ | 400 – 550 từ (6–8 cặp đoạn) | Từ vựng học thuật chuyên sâu; lập luận đa chiều | **Bắt buộc có phần "Phản đề" văn hóa** |

---

## 3. Phân Bổ Vùng Miền & Chủ Đề Văn Hóa (Regions & Cultural Topics)

### A. Vùng Miền (`RegionEnum`)
1. `REGION_NORTH`: **Bắc Bộ** (Hà Nội, Vịnh Hạ Long, Làng gốm Bát Tràng, Tò he Xuân La, v.v.)
2. `REGION_CENTRAL`: **Trung Bộ** (Cố đô Huế, Phố cổ Hội An, Mì Quảng, Đảo Lý Sơn, Hang Sơn Đoòng, v.v.)
3. `REGION_SOUTH`: **Nam Bộ** (Chợ nổi miền Tây, Sài Gòn, Hủ tiếu Sa Đéc, Đờn ca tài tử, Rừng tràm Trà Sư, v.v.)

### B. Chủ Đề Văn Hóa (`TopicEnum`)
1. `TOPIC_CUISINE`: **Ẩm thực** (Món ăn truyền thống, nghệ thuật thưởng trà, phong vị đường phố)
2. `TOPIC_HERITAGE`: **Di sản & Danh lam** (Kiến trúc cổ, di tích lịch sử, cảnh quan thiên nhiên kỳ vĩ)
3. `TOPIC_FESTIVALS`: **Lễ hội** (Hội Gióng, Lễ Khao lề thế lính Hoàng Sa, Đua ghe Ngo Khmer)
4. `TOPIC_CUSTOMS`: **Phong tục & Lối sống** (Nghề thủ công dân gian, tập quán gia đình, sinh hoạt bản địa)

### C. Quy Mô Bài Đọc Thử Nghiệm (Pilot Content Scope)
- `PILOT_LESSONS_TOTAL`: **15 bài đọc đặc trưng** (chia đều 5 bài x 3 miền; mỗi bài có đủ 3 Levels).

---

## 4. Phân Tầng Tài Khoản & Bảng Giá (Monetization & Pricing Tiers)

| Hạng Mục | Gói Miễn Phí (`TIER_FREE`) | 7 Ngày Dùng Thử (`TIER_TRIAL`) | Gói Cao Cấp (`TIER_PREMIUM`) |
| :--- | :--- | :--- | :--- |
| **Thời hạn** | Vĩnh viễn | 7 ngày từ khi đăng ký | Đăng ký theo tháng |
| **Mức phí (VND)** | **0 VNĐ** | **0 VNĐ** | **39.000đ – 49.000đ/tháng** (A/B testing) |
| **Thư viện bài đọc** | 15 bài mẫu cơ bản | Không giới hạn | Toàn bộ bài đọc văn hóa 3 miền |
| **Số từ vựng lưu trữ** | Tối đa 30 từ | Không giới hạn | Không giới hạn sổ tay cá nhân |
| **Dải tốc độ audio** | Chỉ hỗ trợ `1x` | Đầy đủ (`1x`, `0.8x`, `0.5x`) | Đầy đủ (`1x`, `0.8x`, `0.5x`) |
| **Trợ lý AI Companion** | 3 lượt đàm thoại/ngày | Không giới hạn | Không giới hạn lượt tương tác |
| **Quảng cáo (Ads)** | Kèm banner hiển thị chân trang | Không quảng cáo | **100% Không quảng cáo** |

---

## 5. Chỉ Tiêu Kiểm Thử Người Dùng Checkpoint 4 (CP4 Rubric Targets)

- `CP4_MIN_TESTERS`: **Tối thiểu 20 người dùng mục tiêu** (sinh viên 19–24 tuổi, CEFR A2–B2).
- `CP4_MIN_BUGS_FIXED`: **Tối thiểu 3 vấn đề (problems/bugs)** được xử lý và ghi nhận Before/After.
- `CP4_FINANCIAL_FORECAST_YEARS`: **3 năm (2027 – 2029)**.
- `CP4_PITCH_DECK_SLIDES`: **13 – 15 slides**.
