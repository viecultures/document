# TÀI LIỆU THIẾT KẾ HỆ THỐNG GIAO DIỆN (DESIGN.MD)

> **Dự án:** Cổng Thông Tin & Trải Nghiệm Văn Hóa Việt Nam  
> **Phong cách chủ đạo:** Hội họa Dân gian Đông Hồ & Mỹ thuật Truyền thống (Folk Woodblock Aesthetic)  
> **Nguyên tắc cốt lõi:** Nền giấy điệp tự nhiên – Nét khắc viền đanh gọn – Khối màu phẳng thuần khiết – Kiểu chữ thống nhất.

---

## 1. Triết Lý Thiết Kế: Phong Cách Đông Hồ Đương Đại

Phong cách tranh khắc gỗ dân gian Đông Hồ không lạm dụng hiệu ứng đổ bóng phức tạp hay chuyển màu 3D hiện đại. Bản sắc được truyền tải thông qua 4 yếu tố mỹ thuật nguyên bản:

- **Chất nền Giấy Điệp (Texture & Ground):** Toàn bộ nền website sử dụng sắc trắng ngà, vàng nhạt của vỏ điệp nghiền trộn hồ nếp (`#F8E9CF`, `#FAF6EE`), loại bỏ hoàn toàn màu trắng tinh `#FFFFFF` công nghiệp để bảo vệ thị giác và tạo cảm giác mộc bản.
- **Nét Khắc Than Tre (Woodblock Outlines):** Thay vì các đường viền mờ nhạt mỏng mảnh, các khối card, nút bấm và khung ảnh sử dụng nét viền dứt khoát (1.5px – 2px) với tông mực đen than củi hoặc nâu đậm mộc mạc (`#351903`, `#12332B`).
- **Mảng Màu Khoáng Thô (Flat Natural Pigments):** Các khối thông tin sử dụng kỹ thuật đổ màu phẳng (flat color blocks), lấy cảm hứng từ màu tự nhiên: vàng hoa hòe, xanh gỉ đồng, đỏ son, lam chàm.
- **Bố Cục Ước Lệ & Khoảng Trống (Composition & Negative Space):** Giữ không gian thoáng đãng giữa các khối để tôn lên nhịp điệu của chữ và tranh vẽ, tránh nhồi nhét chi tiết.

---

## 2. Hệ Thống Kiểu Chữ Toàn Trang (Unified Typography)

Toàn bộ các trang trên website dùng chung một quy chuẩn font chữ nhằm tránh xung đột thị giác khi người dùng chuyển trang.

- **Phông Tiêu Đề (`font-heading`):** `Cormorant Garamond` hoặc `Playfair Display` (Hỗ trợ tiếng Việt đầy đủ). Mang đường nét thanh đậm mô phỏng nhát dao khắc gỗ và nét bút lông cổ điển.
- **Phông Nội Dung & Giao Diện (`font-body`):** `Be Vietnam Pro` (Sans-serif quốc dân, tối ưu tỷ lệ hiển thị trên màn hình số, chuẩn dấu tiếng Việt).

### Thang Kích Thước & Thông Số Chữ

| Cấp bậc           | Kích thước Desktop | Kích thước Mobile | Trọng lượng (Weight) | Khoảng cách dòng (Line-height) | Ứng dụng cụ thể                       |
| :---------------- | :----------------- | :---------------- | :------------------- | :----------------------------- | :------------------------------------ |
| **Hero Title**    | `52px – 60px`      | `32px – 36px`     | 700 (Bold)           | `1.15`                         | Tiêu đề chính trên Hero Banner        |
| **Heading 1**     | `38px – 44px`      | `28px – 30px`     | 700 (Bold)           | `1.25`                         | Tên trang, tiêu đề phần nội dung lớn  |
| **Heading 2**     | `28px – 32px`      | `22px – 24px`     | 600 (SemiBold)       | `1.3`                          | Tiêu đề mục con, khối danh mục        |
| **Heading 3**     | `20px – 22px`      | `18px – 20px`     | 600 (SemiBold)       | `1.4`                          | Tiêu đề Card thông tin                |
| **Body Large**    | `18px`             | `16px`            | 400 (Regular)        | `1.65`                         | Đoạn dẫn nhập (Intro/Lead text)       |
| **Body Base**     | `15px – 16px`      | `14px – 15px`     | 400 (Regular)        | `1.6`                          | Nội dung bài viết thường, mô tả       |
| **Caption / Tag** | `12px – 13px`      | `11px – 12px`     | 600 (SemiBold)       | `1.3`                          | Nhãn phân loại, ngày tháng, chú thích |

---

## 3. Bản Đồ Mã Màu Theo Từng Trang (Color Architecture)

Mỗi trang sở hữu một bộ mã màu độc lập lấy trực tiếp từ tranh mộc bản và bảng màu mẫu, nhưng đồng nhất về mặt ngữ nghĩa (Tokens).

### Trang Chủ: Tinh Thần Tranh Sơn Mài & Áo Dài Sen

_Không gian lễ hội thanh bình, giao hòa giữa áo dài xanh ngọc, hoa sen hồng phấn và ánh nhật nguyệt._

| Tên Màu                         | Mã HEX    | Giá Trị RGB          | Ứng Dụng Trong Giao Diện                                 |
| :------------------------------ | :-------- | :------------------- | :------------------------------------------------------- |
| **Màu Chủ Đạo (Primary)**       | `#1A7368` | `rgb(26, 115, 104)`  | Màu tà áo dài: Nút bấm chính, tiêu đề trang chủ          |
| **Màu Điểm Xuyết (Secondary)**  | `#E58396` | `rgb(229, 131, 150)` | Sắc sen hồng: Tag sự kiện, gạch chân trang trí, huy hiệu |
| **Màu Nhấn Sáng (Accent)**      | `#EAA22E` | `rgb(234, 162, 46)`  | Sắc vàng mặt trời: Icon nổi bật, viền khung danh dự      |
| **Màu Nền Giấy (Background)**   | `#FAF6EE` | `rgb(250, 246, 238)` | Nền trang chủ mô phỏng giấy điệp quét hạt sò             |
| **Màu Nét Mực (Text & Border)** | `#12332B` | `rgb(18, 51, 43)`    | Màu nét vẽ than củi: Văn bản chính, đường nét viền       |

---

### Trang Di Sản & Vùng Cao: Bảng Màu "Heritage Green & Gold"

_Chủ đề: Ruộng bậc thang Tây Bắc, làng bản nhà sàn, di sản thiên nhiên hùng vĩ._

| Tên Màu            | Mã HEX    | Giá Trị RGB          | Ứng Dụng Trong Giao Diện                                    |
| :----------------- | :-------- | :------------------- | :---------------------------------------------------------- |
| **Heritage Green** | `#15503C` | `rgb(21, 80, 60)`    | **Primary:** Thanh Menu chính, Nút xem chi tiết địa danh    |
| **Forest Jade**    | `#2A816F` | `rgb(42, 129, 111)`  | **Secondary:** Nền thẻ phụ, nhãn tag sinh thái              |
| **Golden Lotus**   | `#D9A441` | `rgb(217, 164, 65)`  | **Accent:** Sắc lúa chín: Viền card nổi bật, số thứ tự bước |
| **Rice Paper**     | `#F8E9CF` | `rgb(248, 233, 207)` | **Background:** Nền toàn trang tạo cảm giác ấm cúng, cổ xưa |
| **Earth Bronze**   | `#8A5A2B` | `rgb(138, 90, 43)`   | **Text / Border:** Màu đất đỏ bazan: Tiêu đề phụ, viền khối |

---

### Trang Không Gian Văn Hóa & Nghệ Thuật: Bảng Màu "Lotus & River Mist"

_Chủ đề: Sông nước Tràng An, Hồ Gươm sương sớm, tĩnh tại, thơ ca và tranh cổ._

| Tên Màu              | Mã HEX    | Giá Trị RGB          | Ứng Dụng Trong Giao Diện                                         |
| :------------------- | :-------- | :------------------- | :--------------------------------------------------------------- |
| **Glaucous Sky**     | `#59789F` | `rgb(89, 120, 159)`  | **Primary:** Màu lam khói sương: Nút bấm, thanh tiến trình       |
| **Powder Blue**      | `#A9B6C4` | `rgb(169, 182, 196)` | **Secondary:** Nền thẻ ảnh mờ ảo, viền chia phân đoạn            |
| **Vanilla Lotus**    | `#ECE69D` | `rgb(236, 230, 157)` | **Accent:** Sắc nhụy hoa sen: Điểm nhấn thông báo                |
| **Moss Green**       | `#7A9445` | `rgb(122, 148, 69)`  | **Tertiary:** Biểu tượng trang trí thiên nhiên, nút chuyển trang |
| **Deep River Green** | `#243C2C` | `rgb(36, 60, 44)`    | **Text / Border:** Nước hồ sâu: Màu chữ chính, khung tranh cổ    |

---

### Trang Lễ Hội & Phố Cổ: Bảng Màu "Earth, Festival & Heritage"

_Chủ đề: Đèn lồng Hội An, ẩm thực truyền thống, kiến trúc tường vàng ngói âm dương._

| Tên Màu             | Mã HEX    | Giá Trị RGB          | Ứng Dụng Trong Giao Diện                                          |
| :------------------ | :-------- | :------------------- | :---------------------------------------------------------------- |
| **Golden Brown**    | `#925E06` | `rgb(146, 94, 6)`    | **Primary:** Sắc vàng đất nung phố cổ: Nút đặt vé, nút sự kiện    |
| **Apple Green**     | `#8DA432` | `rgb(141, 164, 50)`  | **Secondary:** Nền badge lễ hội, biểu tượng thời gian             |
| **Flax**            | `#EDE383` | `rgb(237, 227, 131)` | **Accent:** Sắc vàng nắng hoàng hôn: Khối nổi bật đặc biệt        |
| **Dark Moss Green** | `#365004` | `rgb(54, 80, 4)`     | **Text Secondary:** Màu rêu phong ngói cũ: Chữ tiêu đề phụ        |
| **Bistre**          | `#351903` | `rgb(53, 25, 3)`     | **Text Main / Footer:** Sắc gỗ lim đen: Nền chân trang, viền card |

---

## 4. Nguyên Tắc Thiết Kế Linh Kiện UI Thuần Dân Gian

Để giao diện toát lên chất tranh mộc bản Đông Hồ thay vì phong cách phẳng Tây phương (Flat Design) thông thường, các thành phần giao diện tuân theo nguyên tắc sau:

- **Đường viền nét khắc (Woodblock Border):** Mọi khối nội dung (`.dongho-card`, `.dongho-btn`) đều có đường viền màu đậm bản sắc (`border: 2px solid var(--color-border)`). Bo góc rất nhẹ (`border-radius: 4px` hoặc `2px`), giữ cảm giác phôi gỗ vuông vức.
- **Bóng đổ cứng (Hard Cut-out Shadows):** Tuyệt đối không dùng bóng mờ nhòe (soft blur shadow). Sử dụng bóng đổ dịch chuyển góc cứng (Hard Offset Shadow) mô phỏng các tấm mộc bản xếp chồng:
  `box-shadow: 4px 4px 0px var(--color-border);`
- **Nút bấm kiểu Con Dấu Khắc Gỗ:**
  - Trạng thái tĩnh: Nền màu đơn sắc + Viền đen/đậm + Bóng cứng 3px.
  - Trạng thái Hover: Dịch chuyển nhẹ `-2px -2px` và bóng giãn thành `5px 5px`.
  - Trạng thái Active: Lún xuống vị trí cũ `translate(2px, 2px)` và bóng mất đi (`box-shadow: none`).

---

## 5. Mã Nguồn Triển Khai Hoàn Chỉnh (`tokens.css`)

Lưu tệp này vào dự án (`assets/css/tokens.css`). Khi viết file HTML chỉ cần gắn thuộc tính `data-theme` tương ứng vào thẻ `<body>`.

```css
/* ==========================================================================
   1. GOOGLE FONTS DÙNG CHUNG (Cormorant Garamond & Be Vietnam Pro)
   ========================================================================== */
@import url('[https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&family=Cormorant+Garamond:ital,wght@0,500;0,600;0,700;1,600&display=swap](https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&family=Cormorant+Garamond:ital,wght@0,500;0,600;0,700;1,600&display=swap)');

/* ==========================================================================
   2. BIẾN TOÀN CỤC & THÔNG SỐ ĐÔNG HỒ CHUẨN
   ========================================================================== */
:root {
  --font-heading: 'Cormorant Garamond', Georgia, serif;
  --font-body: 'Be Vietnam Pro', -apple-system, sans-serif;

  /* Quy chuẩn bo góc kiểu mộc bản (không bo tròn dạng viên thuốc) */
  --radius-woodcut: 3px;
  --border-width: 2px;

  /* Hiệu ứng chuyển động */
  --transition-dongho: all 0.2s cubic-bezier(0.25, 1, 0.5, 1);
}

/* ==========================================================================
   3. BẢNG MÀU THEO TRANG (THEMES)
   ========================================================================== */

/* --- TRANG CHỦ: TRANH SEN & ÁO DÀI --- */
body[data-theme="home"] {
  --color-primary: #1A7368;
  --color-primary-hover: #13584F;
  --color-secondary: #E58396;
  --color-accent: #EAA22E;
  --color-bg: #FAF6EE;         /* Nền giấy điệp */
  --color-surface: #FFFFFF;    /* Mặt thẻ card */
  --color-text-main: #12332B;  /* Nét than mực */
  --color-text-muted: #4A635D;
  --color-border: #12332B;     /* Viền nét khắc mộc */
  --shadow-color: #12332B;
}

/* --- TRANG DI SẢN: HERITAGE GREEN & GOLD --- */
body[data-theme="heritage"] {
  --color-primary: #15503C;
  --color-primary-hover: #0E3628;
  --color-secondary: #2A816F;
  --color-accent: #D9A441;
  --color-bg: #F8E9CF;         /* Nền vàng rơm cổ */
  --color-surface: #FCF5E9;
  --color-text-
```
