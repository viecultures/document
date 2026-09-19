# Quy Tắc Nghiệp Vụ BR-01: Bài Đọc Song Ngữ & Âm Thanh AI (Shadowing)

## 1. Mục Đích & Phạm Vi

Quy định cấu trúc dữ liệu, phân loại bài học và luồng âm thanh AI Shadowing trên nền tảng VN Culture Reader.

---

## 2. Các Quy Tắc Nghiệp Vụ Cốt Lõi (Core Business Rules)

### BR-01.1: Phân Loại Bài Đọc Đa Chiều (Topic x Band Leveling)

- Mọi bài đọc bắt buộc phải được gắn 2 chỉ số phân loại: **Chủ đề (Topic)** và **Trình độ (Band/CEFR Level: A2, B1, B2, C1)**.
- Một chủ đề văn hóa (ví dụ: _Cố đô Huế_) có thể có nhiều bài đọc ở các cấp độ trình độ khác nhau để phù hợp với nhiều nhóm người học.

---
### BR-01.2: Cấu Trúc Song Ngữ Cặp Đoạn Văn (Paragraph Pairing Structure)

- Mọi bài đọc lưu trữ dưới dạng danh sách các cặp đoạn văn song ngữ (`ParagraphPair[]`).
- Đoạn tiếng Anh (`en_text`) là dữ liệu chính. Đoạn tiếng Việt (`vi_text`) là dữ liệu dịch phụ trợ.
- Tỷ lệ 1-1 giữa đoạn tiếng Anh và tiếng Việt là nghiêm ngặt.

### BR-01.3: Luồng Âm Thanh AI & Trình Phát Theo Câu (Sentence-Level Audio Player)

- Trình phát âm thanh hỗ trợ 2 chế độ:
  1. Phát toàn bộ bài đọc (`shadowing_audio_url`).
  2. **Phát âm thanh từng câu (Sentence Audio)**: Khi người dùng bấm trực tiếp vào một câu hoặc đoạn tiếng Anh, hệ thống tự động phát âm thanh của riêng câu đó.

  ### BR-01.4: Quy Tắc Nghiệp Vụ Dictation (Nghe Chép Chính Tả Từng Câu)
- **Quy tắc 1.4.1**: Mọi câu trong bài đọc tiếng Anh bắt buộc phải được gắn mốc thời gian bắt đầu (`audio_start`) và kết thúc (`audio_end`) tính bằng giây.
- **Quy tắc 1.4.2**: Trình phát Dictation (Dictation Snippet Player) chỉ phát âm thanh trong phạm vi mốc thời gian của câu hiện tại và hỗ trợ lặp tự động (Loop) hoặc lặp thủ công bằng phím tắt.
- **Quy tắc 1.4.3**: Hệ thống phải hỗ trợ cơ chế so sánh ký tự/từ thời gian thực (Real-time Word Matching):
  - Từ gõ đúng: Hiển thị màu xanh lá (Green).
  - Từ gõ sai: Đổi màu/Gạch chân cam trong ô nhập dữ liệu.
  - Từ chưa gõ: Che bởi ký tự đại diện (`*`).

- **Quy tắc 1.4.4**: Bắt buộc cung cấp các tùy chọn giao diện: `Show answer immediately` (So sánh thời gian thực), `Show full answer` (Hiện toàn bộ đáp án khi tắc), nút `Skip` (Bỏ qua câu), và nút Micro (Nhập liệu bằng giọng nói qua Web Speech API).

```
SHADOWING MODE:
+-----------------------------------------------------------------------+
| 🎧 Player Audio AI: [ ▶ Play ] [ ⏩ 0.75x / 1.0x ] [ 01:25 / 03:40 ]  |
+-----------------------------------------------------------------------+
| 🇬🇧 Paragraph 1 (EN):                                                 |
| "Hue Imperial City is a UNESCO World Heritage site that reflects..."  |
|                                                                       |
| 🇻🇳 Đoạn 1 (VI - Phụ trợ/Ẩn/Hiện):                                    |
| "Quần thể Di tích Cố đô Huế là Di sản Thế giới được UNESCO..."         |
+-----------------------------------------------------------------------+

DICTATION MODE (Mô phỏng DailyDictation):
+-----------------------------------------------------------------------+
| [ Dictation ]   [ Full Transcript ]                 < 4 / 12 >        |
| [ ▶ Play 0:01/0:01 ] ----------------------------- [🔊] [ 1x ▾ ]      |
+-----------------------------------------------------------------------+
| I am cook dinner.                                                     |
|       ~~~~ (Orange Underline)                             [🎙️] [Skip] |
+-----------------------------------------------------------------------+
| ⚠️ Incorrect                                                          |
| I am cooking *******                                                  |
| [x] Show answer immediately     [ ] Show full answer                  |
+-----------------------------------------------------------------------+
```

