# 📈 Mô Hình Tài Chính & Dự Phóng COGS 3 Năm (Financial Model & COGS 2027–2029)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_business.md`](./interface_business.md)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`PRICING_TIERS`)
- Căn cứ thực hiện: Biểu mẫu tài chính chuẩn mực Checkpoint 4 tại Notice 4.

---

## 2. Cấu Trúc Chi Phí (Cost Structure Assumptions)

### A. Giá Vốn Hàng Bán (COGS - Biến phí theo từng người dùng hoạt động)
1. **Chi phí máy chủ & cơ sở dữ liệu (Cloud & Server Hosting):** Ước tính 1.500đ – 2.500đ/active user/tháng (băng thông, lưu trữ tệp âm thanh).
2. **Chi phí API bên thứ ba (Third-party APIs):**
   - **Google Gemini API:** Tính theo token truy vấn của trợ lý AI Companion (~0.00015$/1k tokens).
   - **TTS Audio Generation API (nếu có bài mới):** Chi phí phát sinh một lần khi biên soạn bài đọc.
3. **Phí cổng thanh toán (Payment Gateway Fee):** 2,5% – 3,0% trên mỗi giao dịch đăng ký gói Premium thành công.

### B. Chi Phí Hoạt Động (OPEX - Định phí & Tiếp thị)
1. **Chi phí Marketing & Bán hàng (CAC):** Quảng bá qua các câu lạc bộ tiếng Anh đại học, cuộc thi di sản, workshop văn hóa.
2. **Chi phí thù lao đội ngũ sáng lập (Founder Salaries):** Phân bổ hợp lý theo quy định Notice 4 (không được để bằng 0 nếu làm việc toàn thời gian).
3. **Chi phí kiểm định văn hóa:** Thù lao thỉnh ý kiến nghệ nhân/chuyên gia di sản.

---

## 3. Khung Dự Phóng Tài Chính 3 Năm (2027 – 2029)

| Khoản Mục (VND) | Năm 2027 (Năm 1 theo Tháng) | Năm 2028 (Năm 2 theo Quý) | Năm 2029 (Năm 3 theo Quý) |
| :--- | :--- | :--- | :--- |
| **Số khách hàng trả phí lũy kế** | 3.800 users | 12.000 users | 35.000 users |
| **Doanh thu thuần (Revenue)** | Đạt điểm hòa vốn cuối năm | Tăng trưởng ổn định | Mở rộng quy mô |
| **Giá vốn hàng bán (COGS)** | Chi phí Server, Gemini API, Cổng thanh toán | Chi phí Server, Gemini API, Cổng thanh toán | Chi phí Server, Gemini API, Cổng thanh toán |
| **Lợi nhuận gộp (Gross Profit)** | Tỷ suất lợi nhuận gộp > 75% | Tỷ suất lợi nhuận gộp > 80% | Tỷ suất lợi nhuận gộp > 82% |
| **Tổng chi phí hoạt động (OPEX)** | Marketing, Công cụ, Lương founder | Marketing, Vận hành nội dung | Quy mô nhân sự & Marketing |
| **EBIT (Lợi nhuận trước lãi vay & thuế)** | Âm nửa đầu năm ➔ Dương cuối năm | Dương bền vững | Tái đầu tư mở rộng |
| **Thuế TNDN (Corporate Income Tax)** | 20% (theo luật hiện hành) | 20% | 20% |
| **Lợi nhuận ròng (Net Profit)** | Đạt điểm hòa vốn (Break-even) | Lãi ròng dương | Tái đầu tư mở rộng 54 tỉnh thành |
