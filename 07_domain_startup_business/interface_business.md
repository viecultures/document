# 💼 [Interface] Domain Kinh Doanh, Vận Hành & Khảo Sát Startup

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`PRICING_TIERS`, `CP4_RUBRIC_TARGETS`)
- Khung chương trình: Capstone Startup Project (Kỳ 7, EXE101) & Yêu cầu Notice 4.

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `07_domain_startup_business` chịu trách nhiệm:
1. Định hình phân tầng người dùng (User Roles: Khách vãng lai, Free Tier, 7-Day Trial, Premium Tier).
2. Lưu trữ dữ liệu xác thực thị trường (81 khảo sát thực tế CP2, phân tích đối thủ, TAM/SAM/SOM).
3. Xây dựng mô hình tài chính 3 năm (2027–2029), biến phí COGS (Server/user, API Gemini/TTS, cổng thanh toán) và điểm hòa vốn.
4. Quản lý kế hoạch kiểm thử người dùng Checkpoint 4 (ít nhất 20 testers, Google Form, sửa tối thiểu 3 lỗi Before/After).

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`market_validation.md`](./market_validation.md): Kết quả khảo sát 81 mẫu thực tế, TAM/SAM/SOM, phân tích đối thủ cạnh tranh.
2. [`financial_model_cogs.md`](./financial_model_cogs.md): Bảng dự phóng doanh thu & chi phí 3 năm (2027–2029), biến phí COGS máy chủ/API, P&L.
3. [`cp4_user_testing_plan.md`](./cp4_user_testing_plan.md): Kế hoạch và kịch bản thử nghiệm 20+ người dùng mục tiêu, Google Form và danh mục khắc phục 3 vấn đề theo Notice 4.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Áp dụng chính sách truy cập cho toàn hệ thống:** Cung cấp thông tin quyền hạn (`canAccessFeature`, `savedVocabLimit`, `hasAds`) cho các domain `01_domain_reader`, `02_domain_vocab_flashcards`, `03_domain_ai_companion`.
