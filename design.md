# HỆ THỐNG QUY CHUẨN THIẾT KẾ (DESIGN.MD)

> **Dự án:** VieCultures – Nền tảng học Tiếng Anh qua Văn Hóa & Bản Sắc Việt  
> **Slogan:** *Khắc ghi nguồn cội, gìn giữ văn hóa*  
> **Thông điệp chính (Tagline):** *Gom từng từ nhỏ, hiểu một Việt Nam lớn. (Small words, wonderful worlds)*  
> **Phong cách:** Warm Heritage Editorial & Cultural Storytelling (Di sản ấm áp & Nghệ thuật kể chuyện văn hóa)  
> **Cảm hứng thị giác:** Chất liệu giấy dó thủ công, sắc men gốm lam, xanh di sản, vàng son cung đình và sắc sen hồng dịu nhẹ.

---

## 1. Triết Lý Thiết Kế Giao Diện (Core Design Philosophy)

1. **Warm Paper & Heritage Atmosphere (Không gian giấy mộc & Di sản ấm áp):**
   - Chuyển từ phong cách kính tối (dark glassmorphism) sang tông màu nền giấy kem ngà (`#FBF7EE` / `#F6EEDC`), mang lại cảm giác thân thuộc như lật mở từng trang sách ảnh di sản văn hóa.
   - Tránh nền trắng tinh `#FFFFFF` công nghiệp gây gắt mắt; tận dụng các sắc độ kem và be mây làm dịu thị giác người học.

2. **Harmonious Cultural Palette (Bảng màu văn hóa hài hòa):**
   - Màu sắc được chắt lọc từ các gam màu truyền thống: xanh di sản đậm của tà áo dài và nếp rêu cổ kính, xanh ngọc trời mây, vàng son hoàng cung, và điểm xuyết sắc hồng sen tao nhã.
   - Màu sắc đóng vai trò phân tầng thị giác: nền dịu giúp văn bản và các tác phẩm minh họa nổi bật trang trọng.

3. **Curated Editorial Typography (Kiểu chữ ấn bản & Thi pháp):**
   - Kết hợp ba dòng phông chữ:
     - **Serif cổ điển:** Tôn vinh nét đẹp tri thức, trang trọng cho tiêu đề chính.
     - **Sans-serif hiện đại:** Tối ưu khả năng đọc lướt từ vựng và nội dung học thuật.
     - **Cursive nghệ thuật:** Điểm xuyết các câu danh ngôn, trích dẫn truyền cảm hứng theo lối thư bút mềm mại.

4. **Structured Topic Exploration (Khám phá theo chuyên đề trực quan):**
   - Bố cục trang mạch lạc, dẫn dắt tự nhiên từ **Nhận diện & Định hướng (Navbar)** -> **Khởi nguồn cảm hứng & Tương tác nhanh (Hero Section)** -> **Bốn miền khám phá văn hóa (Explore Section Cards)**.
   - Mọi khối nội dung đều có hình ảnh minh họa sống động, nút tương tác rõ nét định vị mục tiêu học tập.

---

## 2. Hệ Thống Kiểu Chữ (Typography System)

| Nhóm phông | Tên phông chữ | Phong cách / Vai trò | Ứng dụng cụ thể |
| :--- | :--- | :--- | :--- |
| **Heading** | `'Playfair Display', 'Lora', serif` | Sang trọng, học thuật, di sản | Tiêu đề trang (Brand H1), tiêu đề section (H2), tiêu đề thẻ chủ đề (H3) |
| **Body** | `'Be Vietnam Pro', sans-serif` | Rõ ràng, hiện đại, tối ưu tiếng Việt & tiếng Anh | Đoạn văn, thẻ bài học, phụ đề (sub-tagline), menu điều hướng, nút CTA |
| **Decorative** | `'Dancing Script', cursive` | Viết tay phóng khoáng, thi pháp | Câu trích dẫn nghệ thuật (Quotes), ghi chú cảm hứng văn hóa |

### Thang Kích Thước & Phân Cấp Chữ (Type Scale)

| Cấp độ | Desktop Size | Mobile Size | Weight | Line Height | Ứng dụng |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Display Title (Hero H1)** | `48px – 56px` | `32px – 36px` | Bold (700) | `1.15` | Tên thương hiệu `VieCultures` |
| **Hero Tagline** | `22px – 26px` | `18px – 20px` | SemiBold (600) | `1.35` | "Gom từng từ nhỏ, hiểu một Việt Nam lớn." |
| **Hero Sub-tagline** | `16px – 18px` | `14px – 15px` | Medium (500) | `1.5` | "Học tiếng Anh qua văn hóa Việt Nam" |
| **Decorative Quote** | `22px – 26px` | `18px – 20px` | SemiBold (600) | `1.3` | "Small words, wonderful worlds" |
| **Section Heading (H2)** | `32px – 38px` | `24px – 28px` | Bold (700) | `1.2` | "Bốn miền khám phá" |
| **Section Lead** | `15px – 16px` | `14px` | Regular (400) | `1.6` | Đoạn giới thiệu dưới H2 |
| **Card Title (H3)** | `18px – 20px` | `16px – 18px` | SemiBold (600) | `1.3` | Tên 4 chuyên đề khám phá |
| **Navigation Links** | `14px – 15px` | `14px` | Medium (500) | `1` | Menu navbar & footer links |
| **CTA / Buttons** | `14px – 15px` | `13px – 14px` | SemiBold (600) | `1` | "Bắt đầu khám phá →", "Khám phá →" |
| **Slogan Tagline** | `12px – 13px` | `11px – 12px` | Regular (400) | `1.2` | "Khắc ghi nguồn cội, gìn giữ văn hóa" |

---

## 3. Hệ Bảng Màu & Design Tokens (Color Palette & Tokens)

### Bảng Màu Văn Hóa Chủ Đạo

```
┌─────────────────────────────────────────────────────────────────────────┐
│  #FBF7EE        #F6EEDC        #BFE3EA        #9FCED8        #6E9FA1    │
│  Kem ngà sáng   Kem giấy       Xanh trời dịu  Xanh horizon   Xanh teal  │
│  (Nền chính)    (Nền phụ)      (Nền banner)   (Card phụ)     (Icon)     │
├─────────────────────────────────────────────────────────────────────────┤
│  #1E4B43        #D9B76A        #E8B7B2        #E8DFCB        #2C2523    │
│  Xanh di sản    Vàng cổ        Hồng sen       Be mây         Chữ chính  │
│  (Chữ/Nút/Base) (Viền/Accent)  (Accent nhẹ)   (Divider)      (Text dark)│
└─────────────────────────────────────────────────────────────────────────┘
```

| Tên màu sắc | Mã HEX | Vai trò kiến trúc giao diện |
| :--- | :--- | :--- |
| **Kem ngà sáng (Light Ivory)** | `#FBF7EE` | **Nền chính (Body Background):** Tạo cảm giác trang giấy thanh nhã, ấm cúng. |
| **Kem giấy (Parchment Cream)** | `#F6EEDC` | **Nền phụ / Section Sub-bg:** Dùng cho thanh điều hướng, ô widget, nền phân đoạn. |
| **Xanh trời dịu (Soft Sky Teal)** | `#BFE3EA` | **Nền section / banner:** Tạo không gian thoáng đãng, mở rộng chiều sâu thị giác. |
| **Xanh horizon (Horizon Blue)** | `#9FCED8` | **Card / Block phụ:** Điểm nhấn cho khối phụ, banner con, viền card nổi bật. |
| **Xanh teal núi (Mountain Teal)** | `#6E9FA1` | **Icon / Minh họa phụ:** Màu sắc cho đồ họa, icon chức năng, huy hiệu chuyên mục. |
| **Xanh di sản đậm (Heritage Jade)** | `#1E4B43` | **Chữ tiêu đề, Button chính, Footer:** Màu nhận diện thương hiệu chủ đạo, độ tương phản cao. |
| **Vàng cổ (Antique Gold)** | `#D9B76A` | **Viền / Icon / Highlight:** Dấu sao, điểm nhấn huy hiệu, viền nút hover hoặc thẻ đặc biệt. |
| **Hồng sen (Lotus Pink)** | `#E8B7B2` | **Accent nhẹ:** Điểm xuyết cánh hoa, thẻ từ vựng mềm, icon thể hiện cảm xúc. |
| **Be mây (Cloud Mist)** | `#E8DFCB` | **Divider / Đường kẻ / Nền trung gian:** Phân cách nhẹ nhàng giữa các khối nội dung. |
| **Chữ chính (Main Text Dark)** | `#2C2523` | **Nội dung văn bản chính:** Sắc nâu than cổ điển, êm mắt hơn màu đen tuyền `#000000`. |
| **Chữ phụ (Muted Text)** | `#6B635B` | **Phụ đề, mô tả ngắn, meta data:** Dễ đọc, phân cấp rõ rệt so với tiêu đề chính. |
| **Nền thẻ (Card Surface)** | `#FDFBF7` | **Mặt phẳng thẻ nội dung:** Trắng ngà nhẹ nhàng, viền mỏng tinh tế. |

### Bộ Biến Toàn Cục CSS (Global CSS Tokens)

```css
:root {
  /* Color Tokens */
  --bg-primary: #fbf7ee;
  --bg-secondary: #f6eedc;
  --bg-banner: #bfe3ea;
  --bg-card: #fdfbf7;
  --bg-card-sub: #9fced8;

  --color-primary: #3d6e70;
  --color-primary-dark: #1e4b43;
  --color-teal-mountain: #6e9fa1;
  --color-accent-gold: #d9b76a;
  --color-accent-pink: #e8b7b2;
  --color-accent-red: #a33b2e;
  --divider-color: #e8dfcb;

  --text-main: #2c2523;
  --text-muted: #6b635b;
  --text-on-dark: #ffffff;

  /* Typography */
  --font-heading: 'Playfair Display', 'Lora', serif;
  --font-body: 'Be Vietnam Pro', sans-serif;
  --font-decorative: 'Dancing Script', cursive;

  /* Bo góc & Đổ bóng */
  --radius-sm: 8px;
  --radius-md: 14px;
  --radius-lg: 20px;
  --radius-pill: 9999px;
  --shadow-soft: 0 4px 20px rgba(30, 75, 67, 0.08);
  --shadow-card: 0 6px 24px rgba(44, 37, 35, 0.06);
}
```

---

## 4. Cấu Trúc Khung Toàn Trang & Đặc Tả Thành Phần (Layout & Components)

Toàn bộ trang đích (Landing Page) tuân thủ cấu trúc phân đoạn rõ ràng:

```
[ 1. Navigation Bar (Logo + Slogan + Menu + Action Icons) ]
[ 2. Hero Section: Left (Title + Taglines + CTA + Widget) | Right (Quote + Hero Art) ]
[ 3. Explore Section: "Bốn miền khám phá" (Header + 4 Topic Cards Grid) ]
```

---

### 4.1. Thanh Điều Hướng (Navigation Bar)

- **Vị trí & Nền:** Cố định đỉnh trang hoặc sticky, nền kem giấy nhẹ nhàng (`var(--bg-secondary)`) hoặc trong suốt hòa vào nền chính, đường viền đáy tinh tế với sắc be mây (`--divider-color`).
- **Cấu trúc thành phần:**
  1. **Logo & Slogan:**
     - Logo VieCultures sắc nét.
     - Slogan đặt trang nhã ngay cạnh logo: *"Khắc ghi nguồn cội, gìn giữ văn hóa"*.
  2. **Liên kết điều hướng (Nav Links):**
     - Menu căn giữa: `Khám phá` (`#kham-pha`), `Từ vựng` (`#tu-vung`), `Sổ tay của tôi` (`#so-tay`).
     - Font: `var(--font-body)`, hover đổi sắc sang xanh di sản `--color-primary-dark` với gạch chân lượn sóng hoặc hiệu ứng chuyển sắc êm.
  3. **Cụm thao tác (Nav Actions):**
     - Nút icon tìm kiếm (`icon-search`).
     - Nút icon tài khoản người dùng (`icon-user`).

> **Cần ảnh asset:** `File logo chính thức định dạng PNG trong suốt (assets/logo-viecultures.png), sắc nét, bố cục ngang cân đối kèm biểu tượng thương hiệu VieCultures.`

> **Cần ảnh asset:** `Bộ icon nét mảnh thanh lịch định dạng SVG cho thanh điều hướng: Icon Kính lúp tìm kiếm (icon-search) và Icon Tài khoản cá nhân (icon-user).`

---

### 4.2. Khối Mở Đầu (Hero Section)

Khối Hero gồm bố cục 2 cột (Desktop) hoặc xếp chồng tự nhiên (Mobile), là trái tim truyền cảm hứng cho người học:

#### Cột Trái: Cụm Nội Dung & Hành Động (Hero Content)
- **Tiêu đề thương hiệu (H1):** `VieCultures` sử dụng phông chữ nghệ thuật `var(--font-heading)`, màu xanh di sản đậm hoặc nâu than mộc.
- **Tagline chính:** *"Gom từng từ nhỏ, hiểu một Việt Nam lớn."* (Kích thước lớn, giàu chất văn học).
- **Phụ đề (Sub-tagline):** *"Học tiếng Anh qua văn hóa Việt Nam"* (Giải thích trực diện giá trị sản phẩm).
- **Nút hành động chính (Primary CTA):**
  - Nhãn: `Bắt đầu khám phá →`
  - Kiểu dáng: Bo tròn dạng viên thuốc (`border-radius: var(--radius-pill)`), nền xanh di sản đậm (`--color-primary-dark`), chữ trắng hoặc kem vàng, hiệu ứng hover nhấc nhẹ và phát sáng dịu.
- **Widget tương tác nhanh (Widget Discover):**
  - Khối nhỏ nổi bật hình chữ nhật bo tròn (`border-radius: var(--radius-md)`), nền kem giấy hoặc trắng ngà có bóng đổ mềm.
  - Chứa hình thumbnail sách từ vựng cùng dòng chữ song ngữ: `Discover` / **Khám phá**.

> **Cần ảnh asset:** `Icon Sổ từ vựng văn hóa thu nhỏ (assets/icon-book.webp) kích thước ~48x48px đến 64x64px, thể hiện quyển sổ mở ra nét vẽ hoa sen hoặc họa tiết dân gian mềm mại.`

#### Cột Phải: Không Gian Thị Giác & Thi Pháp (Hero Visual)
- **Câu danh ngôn thi pháp (Decorative Quote):**
  - Nội dung: *"Small words, wonderful worlds"*
  - Phông chữ: `var(--font-decorative)` ('Dancing Script', cursive), đặt bay bổng phía trên hoặc chếch góc tranh minh họa.
- **Tranh minh họa chính (Hero Illustration):**
  - Tác phẩm mỹ thuật trung tâm miêu tả người phụ nữ Việt Nam trong tà áo dài truyền thống và hoa sen thơm ngát, tỏa ra vẻ đẹp thanh thoát, thuần Việt.

> **Cần ảnh asset:** `Bức tranh minh họa trung tâm Hero (assets/hero-illustration.webp) vẽ người phụ nữ Việt Nam tà áo dài bên hoa sen, màu sắc trang nhã đồng bộ cùng bảng màu kem ngà và xanh di sản, độ phân giải cao tối ưu hiển thị Desktop và Mobile.`

---

### 4.3. Chuyên Mục "Bốn Miền Khám Phá" (Explore Section)

Khu vực dẫn dắt người dùng bước vào 4 trục nội dung cốt lõi của VieCultures:

#### Tiêu đề Section (Section Header)
- **Tiêu đề (H2):** `Bốn miền khám phá` (`var(--font-heading)`).
- **Mô tả dẫn nhập:** *"Mỗi vùng đất một câu chuyện, mỗi từ vựng một góc nhìn Việt Nam."*

#### Lưới Thẻ Chủ Đề (Topic Cards Grid - 4 Cột)
Mỗi thẻ được thiết kế dạng khối chữ nhật đứng bo tròn góc (`border-radius: 16px`), nền `var(--bg-card)`, viền nhẹ `1px solid var(--divider-color)`, gồm:
1. **Phần ảnh truyền cảm (Card Media):** Ảnh minh họa đại diện cho chủ đề, cắt cúp nghệ thuật tỷ lệ ~4:3.
2. **Tiêu đề chuyên đề (H3):** Phông chữ `var(--font-heading)`, màu sắc đậm nét rõ ràng.
3. **Nút hành động (Card Action):** Nút bo viền thanh lịch với nhãn `Khám phá →`.

Chi tiết 4 thẻ chủ đề và asset cần có:

#### Thẻ 1: Nếp sống & văn hóa
- Nội dung: Các bài học về phong tục tập quán, nếp nhà, tình làng nghĩa xóm, phong cách sống đậm chất Việt.
- Nút bấm: `Khám phá →`

> **Cần ảnh asset:** `Ảnh minh họa chủ đề Nếp sống & văn hóa (assets/card-van-hoa.webp) thể hiện cảnh sinh hoạt mộc mạc, mái đình, nếp nhà xưa hoặc chén trà đầu làng.`

#### Thẻ 2: Truyền thuyết
- Nội dung: Kho tàng thần thoại, truyền thuyết dân gian (Sơn Tinh Thủy Tinh, Lạc Long Quân - Âu Cơ, Thánh Gióng, Bánh chưng bánh giầy) song ngữ Anh - Việt.
- Nút bấm: `Khám phá →`

> **Cần ảnh asset:** `Ảnh minh họa chủ đề Truyền thuyết (assets/card-truyen-thuyet.webp) phong cách huyền sử, hào khí dân gian giàu tính biểu tượng.`

#### Thẻ 3: Ẩm thực
- Nội dung: Tinh hoa văn hóa ẩm thực Việt, phong vị 3 miền, tên gọi nguyên liệu và cách thưởng thức bằng tiếng Anh.
- Nút bấm: `Khám phá →`

> **Cần ảnh asset:** `Ảnh minh họa chủ đề Ẩm thực (assets/card-am-thuc.webp) khắc họa các món ăn truyền thống thanh nhã (bát phở bốc khói, mâm cơm gia đình, hương vị cốm non).`

#### Thẻ 4: Lễ hội & sắc màu
- Nội dung: Những ngày hội rực rỡ, sắc màu truyền thống (Tết Nguyên Đán, Hội Lim, Lễ hội Đền Hùng, Hội thả đèn hoa đăng).
- Nút bấm: `Khám phá →`

> **Cần ảnh asset:** `Ảnh minh họa chủ đề Lễ hội & sắc màu (assets/card-le-hoi.webp) ngập tràn sắc thái vui tươi, đèn hoa đăng, cờ hội truyền thống hoặc tà áo tứ thân trẩy hội.`

---

## 5. Bảng Tổng Hợp Danh Mục Asset Cần Bổ Sung (Asset Checklist)

Để phục vụ lập trình giao diện và hiển thị trọn vẹn bản sắc thương hiệu, đội ngũ thiết kế cần cung cấp các file asset theo danh sách chuẩn hóa dưới đây:

| STT | Đường dẫn file dự kiến | Miêu tả chi tiết hình ảnh asset | Kích thước / Tỷ lệ kiến nghị | Định dạng | Trạng thái hiện tại |
| :---: | :--- | :--- | :--- | :---: | :---: |
| **1** | `assets/logo-viecultures.png` | Logo thương hiệu VieCultures nền trong suốt, kết hợp biểu tượng & chữ | Chiều cao `40px - 60px` | PNG / SVG | ⚠️ Cần bổ sung (`assets/logo-viecultures.png.html`) |
| **2** | `assets/icon-book.webp` | Icon cuốn sổ tay mở / sổ từ vựng cho Widget "Discover" | `64x64px` hoặc `128x128px` (1:1) | WebP / SVG | ⚠️ Cần bổ sung (`assets/icon-book.webp.html`) |
| **3** | `assets/hero-illustration.webp` | Tranh nghệ thuật chủ đạo: Người phụ nữ Việt Nam và hoa sen, phong cách nhã nhặn | `800x600px` hoặc `1200x900px` (4:3 / 16:9) | WebP | ⚠️ Cần bổ sung (`assets/hero-illustration.webp.html`) |
| **4** | `assets/card-van-hoa.webp` | Bìa thẻ chuyên đề "Nếp sống & văn hóa" (Sinh hoạt, phong tục, làng quê) | `600x450px` (4:3) | WebP | ⚠️ Cần bổ sung (`assets/card-van-hoa.webp.html`) |
| **5** | `assets/card-truyen-thuyet.webp` | Bìa thẻ chuyên đề "Truyền thuyết" (Thần thoại, huyền sử tích xưa Việt Nam) | `600x450px` (4:3) | WebP | ⚠️ Cần bổ sung (`assets/card-truyen-thuyet.webp.html`) |
| **6** | `assets/card-am-thuc.webp` | Bìa thẻ chuyên đề "Ẩm thực" (Mâm cơm Việt, phở, hương vị truyền thống) | `600x450px` (4:3) | WebP | ⚠️ Cần bổ sung (`assets/card-am-thuc.webp.html`) |
| **7** | `assets/card-le-hoi.webp` | Bìa thẻ chuyên đề "Lễ hội & sắc màu" (Hội làng, đèn lồng, sắc hoa lễ tết) | `600x450px` (4:3) | WebP | ⚠️ Cần bổ sung (`assets/card-le-hoi.webp.html`) |
| **8** | `assets/icons/*.svg` | Cặp icon chức năng nét mảnh: Kính lúp (`icon-search`) & Người dùng (`icon-user`) | `24x24px` viewport | SVG | ⚠️ Cần bổ sung |

### Quy Chuẩn Xử Lý Asset Khi Chưa Có File (Placeholder Rule)

> [!IMPORTANT]
> **Tuyệt đối tuân thủ:**
> 1. **Không tự ý tìm kiếm ảnh ngẫu nhiên trên mạng** hoặc tự sinh ảnh sai lệch với phong cách di sản.
> 2. **Nếu chưa có file asset chính thức:** Tạo file placeholder định dạng đúng tên + đuôi `.html` (Ví dụ: `assets/card-van-hoa.webp.html`), hiển thị khối chữ nhật màu nền xám mộc (`#E5E7EB` / `#F3F4F6`), ghi rõ nhãn "Cần ảnh asset: `miêu tả asset`".
> 3. Trên giao diện frontend (React): Hiển thị khung placeholder nền xám chuẩn (`bg-[#E5E7EB]` hoặc `bg-[#F6EEDC]`), có icon biểu trưng và nhãn mô tả file asset cần bổ sung để người phụ trách dễ dàng nhận diện và bổ sung file `.webp` sau này.

---

## 6. Khung Mã Nguồn Giao Diện Triển Khai (Implementation Reference)

### 6.1. Cấu Trúc HTML Chuẩn (HTML5 Semantic Wireframe)

```html
<main class="landing-page">
  
  <!-- 1. Navigation Bar -->
  <header class="navbar">
    <div class="logo">
      <img src="assets/logo-viecultures.png" alt="VieCultures Logo" />
      <span class="slogan">Khắc ghi nguồn cội, gìn giữ văn hóa</span>
    </div>
    <nav class="nav-links">
      <a href="#kham-pha">Khám phá</a>
      <a href="#tu-vung">Từ vựng</a>
      <a href="#so-tay">Sổ tay của tôi</a>
    </nav>
    <div class="nav-actions">
      <button class="btn-icon" aria-label="Tìm kiếm"><i class="icon-search"></i></button>
      <button class="btn-icon" aria-label="Tài khoản"><i class="icon-user"></i></button>
    </div>
  </header>

  <!-- 2. Hero Section -->
  <section class="hero-section">
    <div class="hero-content">
      <h1 class="hero-brand">VieCultures</h1>
      <p class="tagline">Gom từng từ nhỏ, hiểu một Việt Nam lớn.</p>
      <p class="sub-tagline">Học tiếng Anh qua văn hóa Việt Nam</p>
      <a href="#bat-dau" class="btn-cta">Bắt đầu khám phá &rarr;</a>
      
      <!-- Widget Discover -->
      <div class="widget-discover">
        <img src="assets/icon-book.webp" alt="Sổ từ vựng" class="widget-thumb" />
        <div class="widget-text">
          <span>Discover</span>
          <strong>Khám phá</strong>
        </div>
      </div>
    </div>
    
    <div class="hero-visual">
      <span class="quote-decorative">Small words, wonderful worlds</span>
      <img src="assets/hero-illustration.webp" alt="Minh họa người phụ nữ Việt Nam và hoa sen" class="hero-img" />
    </div>
  </section>

  <!-- 3. Section: Bốn miền khám phá -->
  <section class="explore-section" id="kham-pha">
    <div class="section-header">
      <h2>Bốn miền khám phá</h2>
      <p>Mỗi vùng đất một câu chuyện, mỗi từ vựng một góc nhìn Việt Nam.</p>
    </div>

    <div class="cards-grid">
      <!-- Card 1 -->
      <article class="topic-card">
        <div class="card-media">
          <img src="assets/card-van-hoa.webp" alt="Nếp sống & văn hóa" />
        </div>
        <h3>Nếp sống & văn hóa</h3>
        <button class="btn-card">Khám phá &rarr;</button>
      </article>

      <!-- Card 2 -->
      <article class="topic-card">
        <div class="card-media">
          <img src="assets/card-truyen-thuyet.webp" alt="Truyền thuyết" />
        </div>
        <h3>Truyền thuyết</h3>
        <button class="btn-card">Khám phá &rarr;</button>
      </article>

      <!-- Card 3 -->
      <article class="topic-card">
        <div class="card-media">
          <img src="assets/card-am-thuc.webp" alt="Ẩm thực" />
        </div>
        <h3>Ẩm thực</h3>
        <button class="btn-card">Khám phá &rarr;</button>
      </article>

      <!-- Card 4 -->
      <article class="topic-card">
        <div class="card-media">
          <img src="assets/card-le-hoi.webp" alt="Lễ hội & sắc màu" />
        </div>
        <h3>Lễ hội & sắc màu</h3>
        <button class="btn-card">Khám phá &rarr;</button>
      </article>
    </div>
  </section>

</main>
```

### 6.2. Bộ Khung CSS Tham Khảo (CSS Reference Stylesheet)

```css
/* ==========================================================================
   GOOGLE FONTS
   ========================================================================== */
@import url('https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700&family=Dancing+Script:wght@600;700&family=Lora:ital,wght@0,500;0,600;0,700;1,500&family=Playfair+Display:ital,wght@0,600;0,700;1,500&display=swap');

/* ==========================================================================
   RESET & BASE TOKENS
   ========================================================================== */
:root {
  --bg-primary: #fbf7ee;
  --bg-secondary: #f6eedc;
  --bg-banner: #bfe3ea;
  --bg-card: #fdfbf7;
  --bg-card-sub: #9fced8;

  --color-primary: #3d6e70;
  --color-primary-dark: #1e4b43;
  --color-teal-mountain: #6e9fa1;
  --color-accent-gold: #d9b76a;
  --color-accent-pink: #e8b7b2;
  --color-accent-red: #a33b2e;
  --divider-color: #e8dfcb;

  --text-main: #2c2523;
  --text-muted: #6b635b;
  --text-on-dark: #ffffff;

  --font-heading: 'Playfair Display', 'Lora', Georgia, serif;
  --font-body: 'Be Vietnam Pro', sans-serif;
  --font-decorative: 'Dancing Script', cursive;

  --radius-sm: 8px;
  --radius-md: 14px;
  --radius-lg: 20px;
  --radius-pill: 9999px;
  --shadow-soft: 0 4px 20px rgba(30, 75, 67, 0.08);
  --shadow-card: 0 6px 24px rgba(44, 37, 35, 0.06);
  --transition-smooth: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

body {
  margin: 0;
  padding: 0;
  background-color: var(--bg-primary);
  color: var(--text-main);
  font-family: var(--font-body);
  line-height: 1.6;
}

/* ==========================================================================
   1. NAVBAR
   ========================================================================== */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 48px;
  background-color: var(--bg-primary);
  border-bottom: 1px solid var(--divider-color);
}

.logo {
  display: flex;
  align-items: center;
  gap: 16px;
}

.logo img {
  height: 42px;
  object-fit: contain;
}

.logo .slogan {
  font-size: 0.85rem;
  color: var(--text-muted);
  font-style: italic;
  border-left: 1px solid var(--divider-color);
  padding-left: 14px;
}

.nav-links {
  display: flex;
  gap: 32px;
}

.nav-links a {
  text-decoration: none;
  color: var(--text-main);
  font-weight: 500;
  font-size: 0.95rem;
  transition: var(--transition-smooth);
}

.nav-links a:hover {
  color: var(--color-primary-dark);
}

.nav-actions {
  display: flex;
  gap: 12px;
}

.btn-icon {
  background: transparent;
  border: 1px solid var(--divider-color);
  border-radius: 50%;
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: var(--text-main);
  transition: var(--transition-smooth);
}

.btn-icon:hover {
  background-color: var(--bg-secondary);
  border-color: var(--color-accent-gold);
}

/* ==========================================================================
   2. HERO SECTION
   ========================================================================== */
.hero-section {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  align-items: center;
  gap: 48px;
  padding: 64px 48px;
  max-width: 1280px;
  margin: 0 auto;
}

.hero-brand {
  font-family: var(--font-heading);
  font-size: 3.5rem;
  font-weight: 700;
  color: var(--color-primary-dark);
  margin: 0 0 12px;
  line-height: 1.1;
}

.tagline {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text-main);
  margin: 0 0 8px;
}

.sub-tagline {
  font-size: 1.1rem;
  color: var(--text-muted);
  margin: 0 0 32px;
}

.btn-cta {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background-color: var(--color-primary-dark);
  color: var(--text-on-dark);
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  padding: 14px 32px;
  border-radius: var(--radius-pill);
  box-shadow: var(--shadow-soft);
  transition: var(--transition-smooth);
}

.btn-cta:hover {
  background-color: var(--color-primary);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(30, 75, 67, 0.2);
}

.widget-discover {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  margin-top: 40px;
  padding: 10px 20px;
  background: var(--bg-card);
  border: 1px solid var(--divider-color);
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-card);
}

.widget-thumb {
  width: 36px;
  height: 36px;
  object-fit: contain;
}

.widget-text span {
  display: block;
  font-size: 0.75rem;
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.widget-text strong {
  display: block;
  font-size: 0.95rem;
  color: var(--color-primary-dark);
}

.hero-visual {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.quote-decorative {
  font-family: var(--font-decorative);
  font-size: 1.85rem;
  color: var(--color-accent-gold);
  margin-bottom: -16px;
  z-index: 2;
  text-align: center;
}

.hero-img {
  width: 100%;
  max-width: 500px;
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-soft);
  object-fit: cover;
}

/* ==========================================================================
   3. EXPLORE SECTION ("BỐN MIỀN KHÁM PHÁ")
   ========================================================================== */
.explore-section {
  padding: 80px 48px;
  max-width: 1280px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 48px;
}

.section-header h2 {
  font-family: var(--font-heading);
  font-size: 2.3rem;
  color: var(--color-primary-dark);
  margin: 0 0 10px;
}

.section-header p {
  font-size: 1.05rem;
  color: var(--text-muted);
  margin: 0;
}

.cards-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.topic-card {
  background: var(--bg-card);
  border: 1px solid var(--divider-color);
  border-radius: var(--radius-md);
  padding: 16px;
  box-shadow: var(--shadow-card);
  display: flex;
  flex-direction: column;
  transition: var(--transition-smooth);
}

.topic-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 28px rgba(44, 37, 35, 0.1);
  border-color: var(--color-accent-gold);
}

.card-media {
  width: 100%;
  height: 180px;
  border-radius: var(--radius-sm);
  overflow: hidden;
  margin-bottom: 16px;
}

.card-media img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: var(--transition-smooth);
}

.topic-card:hover .card-media img {
  transform: scale(1.05);
}

.topic-card h3 {
  font-family: var(--font-heading);
  font-size: 1.2rem;
  color: var(--color-primary-dark);
  margin: 0 0 16px;
  flex-grow: 1;
}

.btn-card {
  align-self: flex-start;
  background: transparent;
  color: var(--color-primary-dark);
  border: 1px solid var(--color-primary-dark);
  padding: 8px 18px;
  border-radius: var(--radius-pill);
  font-size: 0.88rem;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition-smooth);
}

.btn-card:hover {
  background-color: var(--color-primary-dark);
  color: var(--text-on-dark);
}

/* ==========================================================================
   RESPONSIVE
   ========================================================================== */
@media (max-width: 1024px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .hero-section {
    grid-template-columns: 1fr;
    padding: 40px 24px;
    gap: 32px;
  }

  .navbar {
    padding: 14px 20px;
    flex-wrap: wrap;
    gap: 12px;
  }

  .logo .slogan {
    display: none;
  }

  .cards-grid {
    grid-template-columns: 1fr;
  }
}
```
