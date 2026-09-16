# HỆ THỐNG QUY CHUẨN THIẾT KẾ (DESIGN.MD)

> **Dự án:** VieCultures – Học Tiếng Anh Qua Văn Hóa & Nghệ Thuật Việt  
> **Phong cách:** Modern Heritage Editorial & Atmospheric Glassmorphism (Di sản đương đại hòa sắc không gian)  
> **Tôn chỉ thị giác:** Tôn trọng tác phẩm hội họa – Kiểu chữ phóng khoáng không đóng khung – Linh kiện mềm mại, trong trẻo.

---

## 1. Triết Lý Thiết Kế Giao Diện (Core Design Philosophy)

1. **Unboxed Layout (Bố cục mở, loại bỏ bao bọc cưỡng ép):**
   - Không sử dụng các khối thẻ (card) hình chữ nhật đục ngầu che chắn cảnh quan.
   - Tận dụng khoảng trống tự nhiên của tranh (bầu trời, rặng mây, thung lũng) làm nơi neo đậu cho chữ.
   - Chữ được giải phóng hoàn toàn, hiển thị trực tiếp với độ tương phản tự nhiên được hỗ trợ bởi hiệu ứng đổ bóng mờ cực mịn (`text-shadow: 0 2px 12px rgba(0,0,0,0.35)`).

2. **Soft Organic Forms (Hình thái hữu cơ mềm mại):**
   - Toàn bộ nút bấm (button), nhãn phân loại (badge/pill), ô tìm kiếm đều sử dụng chuẩn bo góc cực đại (`border-radius: 9999px` - Pill Shape).
   - Không sử dụng góc vuông cứng nhắc hay viền đen đậm làm gãy vụn đường nét uốn lượn của tranh.

3. **Atmospheric Glassmorphism (Kính mờ khí quyển):**
   - Các khối chức năng nổi sử dụng chất liệu kính mờ bán trong suốt kết hợp làm nhòe nền hậu cảnh (`backdrop-filter: blur(12px)`).
   - Đường viền chỉ dày 1px với độ trong suốt tinh tế (`border: 1px solid rgba(255, 255, 255, 0.2)`), tuyệt đối không dùng viền đen than.

---

## 2. Hệ Thống Kiểu Chữ Tạp Chí (Editorial Typography)

Bộ phông chữ được tuyển chọn để tạo cảm giác tri thức, thanh thoát của một ấn bản sách ảnh cao cấp:

- **Phông Tiêu Đề (`font-heading`):** `Playfair Display` hoặc `Cormorant Garamond` (Serif). Dày dặn, thanh lịch, mang âm hưởng văn hóa và nghệ thuật thi ca.
- **Phông Nội Dung (`font-body`):** `Plus Jakarta Sans` hoặc `Be Vietnam Pro` (Sans-serif). Nét chữ tròn trịa, hiện đại, thoáng đãng, cực kỳ êm mắt ở kích cỡ nhỏ.

### Thang Kích Thước Chữ (Type Scale)

| Cấp độ             | Kích thước Desktop | Kích thước Mobile | Trọng lượng    | Line-height | Màu sắc khuyên dùng                       |
| :----------------- | :----------------- | :---------------- | :------------- | :---------- | :---------------------------------------- |
| **Brand Logo**     | `26px – 28px`      | `22px`            | Bold (700)     | `1`         | Kem ngọc trai (`#FFFDF8`) hoặc Trắng      |
| **Hero Title**     | `52px – 64px`      | `32px – 38px`     | Bold (700)     | `1.15`      | Trắng tinh khiết (`#FFFFFF`)              |
| **Hero Subtitle**  | `22px – 26px`      | `18px – 20px`     | Medium (500)   | `1.3`       | Kem vàng nắng nhẹ (`#F5E8C7`)             |
| **Body Lead**      | `16px – 17px`      | `14px – 15px`     | Regular (400)  | `1.7`       | Trắng mờ sương (`rgba(255,255,255,0.85)`) |
| **Button Text**    | `14px – 15px`      | `13px – 14px`     | SemiBold (600) | `1`         | Tùy biến theo nền nút                     |
| **Tagline / Pill** | `12px – 13px`      | `11px – 12px`     | Medium (500)   | `1`         | Vàng nắng hoặc Trắng ngọc                 |

---

## 3. Hệ Bảng Màu Đương Đại (Modern Color Tokens)

Tất cả màu sắc được chiết xuất từ ánh sáng mặt trời, ngọc bích, sương mai và tà áo dài trong tranh, nhưng được hiện đại hóa dưới dạng màu kính và màu kem mềm.

### Trang Chủ: "Golden Sun & Jade Silk" (Tranh Sen & Áo Dài)

_Lấy cảm hứng từ ánh hoàng hôn rực rỡ và sắc áo ngọc bích sang trọng._

| Vai trò           | Tên màu            | Giá trị thực tế          | Mô tả ứng dụng                                                  |
| :---------------- | :----------------- | :----------------------- | :-------------------------------------------------------------- |
| **Primary CTA**   | Sungold Cream      | `#FCE5B5`                | Nút "Bắt Đầu Học Ngay": Màu kem vàng ấm, chữ nâu đen sang trọng |
| **Secondary CTA** | Deep Jade Glass    | `rgba(18, 42, 34, 0.65)` | Nút "Khám Phá": Nền kính xanh ngọc sẫm bán trong suốt           |
| **Pill Badge**    | Shadow Mist        | `rgba(0, 0, 0, 0.45)`    | Tag "Học Tiếng Anh Tự Nhiên": Kính đen mờ bo tròn               |
| **Text Primary**  | Pure Ivory         | `#FFFFFF`                | Tiêu đề chính, logo trên nền tranh                              |
| **Text Accent**   | Warm Lotus Gold    | `#F5D280`                | Tiêu đề phụ, dấu sao, icon điểm nhấn                            |
| **Page Base**     | Deep Heritage Jade | `#0D1C18`                | Nền chuyển tiếp khi cuộn xuống dưới chân trang                  |

---

### Trang 2: "Heritage Green & Gold" (Ruộng Bậc Thang & Rừng Vùng Cao)

| Vai trò             | Tên màu         | Giá trị thực tế            | Mô tả ứng dụng                                      |
| :------------------ | :-------------- | :------------------------- | :-------------------------------------------------- |
| **Primary**         | Terraced Forest | `#15503C`                  | Màu thương hiệu chính, thanh tiến trình học tập     |
| **Secondary Glass** | Jade Glaze      | `rgba(42, 129, 111, 0.25)` | Thẻ bài học kính mờ xanh bích                       |
| **Accent Glow**     | Ripe Paddy Gold | `#E2A93B`                  | Nút hoàn thành bài học, huy hiệu sao                |
| **Background**      | Silk Rice Paper | `#FDFBF7`                  | Nền trang nhã hạt gạo, sáng sạch không gây chói mắt |
| **Text Dominant**   | Deep Pine Ink   | `#112720`                  | Màu chữ bài viết, sắc sảo dễ đọc                    |

---

### Trang 3: "Lotus & River Mist" (Mặt Hồ & Tháp Cổ Sương Chiều)

| Vai trò             | Tên màu           | Giá trị thực tế            | Mô tả ứng dụng                             |
| :------------------ | :---------------- | :------------------------- | :----------------------------------------- |
| **Primary**         | Mist Blue         | `#59789F`                  | Nút luyện nghe Podcast, biểu tượng sóng âm |
| **Secondary Glass** | Pale Lake Mist    | `rgba(169, 182, 196, 0.2)` | Khối chứa đoạn hội thoại song ngữ          |
| **Accent Glow**     | Lotus Stamen      | `#F0E89E`                  | Điểm nhấn từ vựng mới, nút tua nhanh       |
| **Background**      | Morning Fog White | `#F5F8FA`                  | Nền trang màu lam ngọc sương nhạt          |
| **Text Dominant**   | Deep River Tone   | `#192A20`                  | Chữ đọc tài liệu, không dùng đen tuyền     |

---

### Trang 4: "Earth, Festival & Heritage" (Phố Cổ Hội An & Đèn Lồng)

| Vai trò             | Tên màu         | Giá trị thực tế            | Mô tả ứng dụng                          |
| :------------------ | :-------------- | :------------------------- | :-------------------------------------- |
| **Primary**         | Lantern Ochre   | `#A86708`                  | Nút đặt vé sự kiện, chọn phòng văn hóa  |
| **Secondary Glass** | Moss Glaze      | `rgba(141, 164, 50, 0.15)` | Khối thông tin địa danh phố cổ          |
| **Accent Glow**     | Old Wall Yellow | `#F2E788`                  | Nhãn giờ mở cửa, huy hiệu di sản UNESCO |
| **Background**      | Warm Paper      | `#FDFCF7`                  | Nền vàng nắng nhạt của bức tường vôi cũ |
| **Text Dominant**   | Ebony Wood      | `#2B1503`                  | Màu chữ nâu gỗ trầm lắng                |

---

## 4. Đặc Tả Thành Phần Giao Diện Chuẩn 88d (Component Blueprint)

### A. Thanh Điều Hướng (Floating Glass Navbar)

- Không viền đáy, không đóng ô vuông. Nền trong suốt hoặc kính mờ nhẹ khi cuộn trang.
- Menu căn giữa, khoảng cách rộng rãi (gap: 32px).
- Chữ trắng kem, khi hover xuất hiện gạch chân siêu mảnh hoặc chuyển sang sắc vàng nắng.

### B. Thẻ Nhãn Đỉnh Đầu (Category Pill Tag)

- Nền kính đen mờ: `background: rgba(0, 0, 0, 0.4);`
- Làm nhòe hậu cảnh: `backdrop-filter: blur(8px);`
- Viền mờ tinh tế: `border: 1px solid rgba(255, 255, 255, 0.15);`
- Bo góc: `border-radius: 9999px;`
- Điểm xuyết một chấm tròn nhỏ màu cam đất bên cạnh chữ.

### C. Nút Bấm Đôi (The Dual Button Group)

1. **Nút Chính (Primary Pill):**
   - Nền: Màu kem vàng lúa chín mượt mà (`#FCE5B5`).
   - Chữ: Màu nâu đen mộc (`#1A1A1A`), font chữ dày dặn, có mũi tên nhỏ chỉ sang phải `→`.
   - Hiệu ứng: Không có viền đen thô. Đổ bóng mờ mịn màng (`box-shadow: 0 4px 20px rgba(252, 229, 181, 0.25)`).
2. **Nút Phụ (Secondary Glass Pill):**
   - Nền: Kính sẫm màu ngọc bích `rgba(18, 42, 34, 0.6)`.
   - Chữ: Màu trắng tinh khôi, viền kính siêu mỏng `1px solid rgba(255, 255, 255, 0.2)`.
   - Có icon sao lấp lánh (Sparkle) hoặc la bàn nhỏ ở bên trái.

---

## 5. File Mã Nguồn Triển Khai CSS (`modern-tokens.css`)

Sao chép toàn bộ khối code này vào dự án của bạn để tạo ra giao diện chuẩn 100% như bức ảnh 88d:

```css
/* ==========================================================================
   1. GOOGLE FONTS CAO CẤP DÙNG CHUNG
   ========================================================================== */
@import url("[https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,500;0,600;0,700;1,500&display=swap](https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,500;0,600;0,700;1,500&display=swap)");

/* ==========================================================================
   2. HỆ BIẾN THIẾT KẾ TOÀN TRANG (GLOBAL TOKENS)
   ========================================================================== */
:root {
  --font-heading: "Playfair Display", Georgia, serif;
  --font-body:
    "Plus Jakarta Sans", -apple-system, BlinkMacSystemFont, sans-serif;

  /* Chuẩn bo tròn hạt đậu / viên thuốc (Pill Shape) */
  --radius-pill: 9999px;
  --radius-card: 16px;

  /* Hiệu ứng chuyển động mượt */
  --transition-smooth: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

/* ==========================================================================
   3. THEME TRANG CHỦ (CHUẨN FORM ẢNH 88D)
   ========================================================================== */
body[data-theme="home"] {
  /* Màu sắc chủ đạo */
  --btn-primary-bg: #fce5b5;
  --btn-primary-text: #18221e;
  --btn-primary-hover: #fff0ce;

  --btn-glass-bg: rgba(18, 42, 34, 0.65);
  --btn-glass-text: #ffffff;
  --btn-glass-border: rgba(255, 255, 255, 0.25);
  --btn-glass-hover: rgba(26, 60, 48, 0.85);

  --pill-tag-bg: rgba(0, 0, 0, 0.45);
  --pill-tag-text: #f5e8c7;
  --pill-tag-border: rgba(255, 255, 255, 0.15);

  --text-hero-main: #ffffff;
  --text-hero-sub: #f7e5c3;
  --text-hero-desc: rgba(255, 255, 255, 0.85);
}

/* ==========================================================================
   4. CÁC LINH KIỆN GIAO DIỆN HIỆN ĐẠI (COMPONENTS)
   ========================================================================== */

/* Khối nhãn nhỏ trên tiêu đề (Pill Tag) */
.glass-pill {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px;
  background-color: var(--pill-tag-bg);
  border: 1px solid var(--pill-tag-border);
  border-radius: var(--radius-pill);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  color: var(--pill-tag-text);
  font-family: var(--font-body);
  font-size: 0.82rem;
  font-weight: 500;
  letter-spacing: 0.5px;
  margin-bottom: 24px;
}

.glass-pill-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: #e27941; /* Điểm cam đất nhấn nhẹ */
}

/* Cụm Tiêu Đề Hero (Không dùng hộp bao quanh) */
.hero-title-group {
  max-width: 680px;
  margin-bottom: 32px;
}

.hero-logo-tag {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.hero-logo-box {
  display: inline-block;
  background-color: #a13225; /* Đỏ son mộc bản */
  color: #ffffff;
  font-family: var(--font-body);
  font-size: 0.7rem;
  font-weight: 700;
  padding: 3px 6px;
  border-radius: 3px;
  line-height: 1.1;
  text-align: center;
}

.hero-brand-name {
  font-family: var(--font-heading);
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--text-hero-main);
  letter-spacing: -0.01em;
  text-shadow: 0 2px 16px rgba(0, 0, 0, 0.4);
}

.hero-main-heading {
  font-family: var(--font-heading);
  font-size: 3rem;
  font-weight: 600;
  line-height: 1.25;
  color: var(--text-hero-main);
  text-shadow: 0 2px 14px rgba(0, 0, 0, 0.5);
  margin-bottom: 8px;
}

.hero-main-subheading {
  font-family: var(--font-heading);
  font-size: 1.5rem;
  font-weight: 400;
  font-style: italic;
  color: var(--text-hero-sub);
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
  margin-bottom: 20px;
}

.hero-description {
  font-family: var(--font-body);
  font-size: 1rem;
  line-height: 1.65;
  color: var(--text-hero-desc);
  max-width: 580px;
  text-shadow: 0 1px 8px rgba(0, 0, 0, 0.6);
  margin-bottom: 36px;
}

/* Cụm Nút Bấm Đôi Chuẩn 88d */
.hero-btn-group {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

/* Nút Chính (Màu Kem Nắng Ấm) */
.btn-pill-primary {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background-color: var(--btn-primary-bg);
  color: var(--btn-primary-text);
  font-family: var(--font-body);
  font-size: 0.95rem;
  font-weight: 600;
  padding: 13px 30px;
  border-radius: var(--radius-pill);
  text-decoration: none;
  border: none;
  cursor: pointer;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.2);
  transition: var(--transition-smooth);
}

.btn-pill-primary:hover {
  background-color: var(--btn-primary-hover);
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(252, 229, 181, 0.35);
}

/* Nút Phụ (Kính Mờ Đen Rêu) */
.btn-pill-glass {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background-color: var(--btn-glass-bg);
  color: var(--btn-glass-text);
  border: 1px solid var(--btn-glass-border);
  font-family: var(--font-body);
  font-size: 0.95rem;
  font-weight: 500;
  padding: 13px 28px;
  border-radius: var(--radius-pill);
  text-decoration: none;
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  cursor: pointer;
  transition: var(--transition-smooth);
}

.btn-pill-glass:hover {
  background-color: var(--btn-glass-hover);
  border-color: rgba(255, 255, 255, 0.4);
  transform: translateY(-2px);
}
```
