# Quy Tắc Nghiệp Vụ BR-01: Bài Đọc Song Ngữ & Âm Thanh AI (Shadowing)

## 1. Mục Đích & Phạm Vi

Quy định cấu trúc dữ liệu, phân loại bài học và luồng âm thanh AI Shadowing trên nền tảng VN Culture Reader.

---

## 2. Các Quy Tắc Nghiệp Vụ Cốt Lõi (Core Business Rules)

### BR-01.1: Phân Loại Bài Đọc Đa Chiều (Topic x Band Leveling)

- Mọi bài đọc bắt buộc phải được gắn 2 chỉ số phân loại: **Chủ đề (Topic)** và **Trình độ (Band/CEFR Level: A2, B1, B2, C1)**.
- Một chủ đề văn hóa (ví dụ: _Cố đô Huế_) có thể có nhiều bài đọc ở các cấp độ trình độ khác nhau để phù hợp với nhiều nhóm người học.

### BR-01.2: Cấu Trúc Song Ngữ Cặp Đoạn Văn (Paragraph Pairing Structure)

- Mọi bài đọc lưu trữ dưới dạng danh sách các cặp đoạn văn song ngữ (`ParagraphPair[]`).
- Đoạn tiếng Anh (`en_text`) là dữ liệu chính. Đoạn tiếng Việt (`vi_text`) là dữ liệu dịch phụ trợ.
- Tỷ lệ 1-1 giữa đoạn tiếng Anh và tiếng Việt là nghiêm ngặt.

### BR-01.3: Luồng Âm Thanh AI & Trình Phát Theo Câu (Sentence-Level Audio Player)

- Trình phát âm thanh hỗ trợ 2 chế độ:
  1. Phát toàn bộ bài đọc (`shadowing_audio_url`).
  2. **Phát âm thanh từng câu (Sentence Audio)**: Khi người dùng bấm trực tiếp vào một câu hoặc đoạn tiếng Anh, hệ thống tự động phát âm thanh của riêng câu đó.
