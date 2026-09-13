# 📜 Quy Tắc Nghiệp Vụ BR-01: Bài Đọc Song Ngữ & Âm Thanh AI (Shadowing)

## 1. Mục Đích & Phạm Vi
Quy định cấu trúc dữ liệu, quy tắc lưu trữ, xuất dữ liệu và trải nghiệm người dùng đối với các bài đọc học thuật về chủ đề văn hóa Việt Nam trên nền tảng **VN Culture Reader**.

---

## 2. Các Quy Tắc Nghiệp Vụ Cốt Lõi (Core Business Rules)

### BR-01.1: Cấu Trúc Song Ngữ Cặp Đoạn Văn (Paragraph Pairing Structure)
- **Quy tắc 1.1.1**: Mọi bài đọc bắt buộc phải được lưu trữ và xuất ra dưới dạng danh sách các cặp đoạn văn song ngữ (`ParagraphPair[]`).
- **Quy tắc 1.1.2**: Trong mỗi cặp đoạn văn:
  - **Văn bản Tiếng Anh (`en_text`)**: Dữ liệu chính (Primary Data), hiển thị nổi bật để người dùng tập trung luyện đọc.
  - **Văn bản Tiếng Việt (`vi_text`)**: Dữ liệu phụ trợ (Auxiliary Data), dùng để tra cứu dịch nghĩa tương ứng theo ngữ cảnh đoạn.
- **Quy tắc 1.1.3**: Tỷ lệ 1-1 giữa đoạn tiếng Anh và tiếng Việt là **nghiêm ngặt**. Không được phép có đoạn tiếng Anh không có đoạn tiếng Việt tương ứng hoặc ngược lại.

### BR-01.2: Luồng Âm Thanh AI Shadowing (AI Audio Stream)
- **Quy tắc 1.2.1**: Mỗi bài đọc **bắt buộc phải đính kèm một luồng dữ liệu âm thanh AI** (`shadowing_audio_url`) đọc chuẩn giọng bản xứ (Native English Accent - US hoặc UK).
- **Quy tắc 1.2.2**: Đơn vị âm thanh AI phải hỗ trợ cơ chế phát toàn bài đọc và đồng bộ mốc thời gian (Timestamp Syncing) theo từng đoạn/câu để người dùng thực hiện phương pháp **Shadowing** (vừa nghe vừa nhại lại).
- **Quy tắc 1.2.3**: Trình phát âm thanh (Audio Player) phải cung cấp tùy chọn điều chỉnh tốc độ phát (0.75x - Tự nhiên chậm, 1.0x - Chuẩn, 1.25x - Nhanh) để phù hợp với nhiều trình độ người học.

---

## 3. Trải Nghiệm Giao Diện Đề Xuất (UI/UX Guidelines)

```
+-----------------------------------------------------------------------+
| 🎧 Player Audio AI: [ ▶ Play ] [ ⏩ 0.75x / 1.0x ] [ 01:25 / 03:40 ]  |
+-----------------------------------------------------------------------+
| 🇬🇧 Paragraph 1 (EN):                                                 |
| "Hue Imperial City is a UNESCO World Heritage site that reflects..."  |
|                                                                       |
| 🇻🇳 Đoạn 1 (VI - Phụ trợ/Ẩn/Hiện):                                    |
| "Quần thể Di tích Cố đô Huế là Di sản Thế giới được UNESCO..."         |
+-----------------------------------------------------------------------+
```

---

## 4. Tác Động Đến Các Bộ Phận (Cross-Functional Impact)

- 🎨 **UI/UX & Marketing**: Thiết kế giao diện rõ ràng giữa phần tiếng Anh (chính) và tiếng Việt (phụ). Cho phép bật/tắt hoặc làm mờ đoạn tiếng Việt để kích thích tư duy tiếng Anh trước khi tra dịch.
- ⚙️ **Backend Dev**: Thiết kế API trả về JSON chứa mảng `paragraphs: [{ en: "...", vi: "...", timestamp_start: 0, timestamp_end: 12 }]`.
- 🤖 **AI Agent**: Khi khởi tạo nội dung bài học mới, bắt buộc AI phải sinh dữ liệu theo đúng cặp đoạn văn và tọa độ mốc thời gian cho file âm thanh.
