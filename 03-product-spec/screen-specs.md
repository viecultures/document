# 🖥️ Đặc Tả Giao Diện Màn Hình (Screen Specifications)

Tài liệu mô tả chi tiết bố cục, thành phần và tương tác trên các màn hình chính của ứng dụng **VN Culture Reader** trên Web App và Mobile Web App.

---

## 1. Màn Hình Reader & Shadowing Player (Reading Screen)

### 1.1. Bố Cục (Layout)
- **Top Bar**: Tên bài đọc, danh mục (Lịch sử/Văn hóa/Danh lam), nút lưu bài học, thanh tiến độ.
- **Shadowing Audio Sticky Player**: Cố định ở đầu hoặc đáy màn hình, gồm nút Play/Pause, tua 5s, chỉnh tốc độ (0.75x, 1x, 1.25x), thanh thời gian.
- **Khu Vực Bài Đọc Song Ngữ**:
  - **Desktop**: 2 cột song song (Cột trái: Tiếng Anh, Cột phải: Tiếng Việt tương ứng).
  - **Mobile Web App**: Dạng khối bài viết xếp chồng (Stacked). Mỗi đoạn tiếng Anh đi kèm 1 toggle *"Xem bản dịch"* bên dưới.
- **Interactive Tooltip Card**: Khi nhấp vào từ vựng học thuật (highlighted word), popup nổi lên hiển thị: Từ gốc, Phiên âm IPA, Từ loại, Nghĩa Việt, Nút nghe âm thanh từ, Nút *"Thêm vào danh sách ôn"*.

---

## 2. Màn Hình Ôn Tập Flashcard (Flashcard Study Screen)

### 2.1. Bố Cục & Tương Tác
- **Thẻ Nhớ Trung Tâm (Central Card)**:
  - Hiệu ứng 3D Flip khi click/tap hoặc vuốt.
  - **Mặt trước**: Từ vựng to rõ + Câu ngữ cảnh gốc trong bài đọc (font chữ nghiêng, highlighted từ).
  - **Mặt sau**: Phiên âm IPA + Loa phát âm AI + Nghĩa tiếng Việt.
- **Thanh Đánh Giá Nhị Phân (Bottom Control Bar)**:
  - Nút 🔴 **"Cần ôn lại"** (Màu đỏ/cam nhẹ, nằm bên trái).
  - Nút 🟢 **"Đã nhớ"** (Màu xanh lá nhẹ, nằm bên phải).
  - Hỗ trợ phím tắt trên Desktop: `Phím Mũi tên Trái` (Cần ôn lại) / `Phím Mũi tên Phải` (Đã nhớ) / `Space` (Lật thẻ).

---

## 3. Màn Hình Cảm Nghĩ Cộng Đồng (Reflections & UGC Screen)

### 3.1. Bố Cục
- **Khung Soạn Thảo (Editor Card)**:
  - Textarea nhập nội dung cảm nghĩ.
  - **Quick Vocab Toolbar**: Dải thẻ từ vựng nằm ngang ngay trên bàn phím/khung gõ. Click từ nào -> Tự động chèn từ đó vào vị trí con trỏ.
  - Nút **"Đăng cảm nghĩ"** (Submit button).
- **Dòng Thời Gian Tương Tác (Community Feed)**:
  - Danh sách bài đăng Reflection của người dùng khác.
  - Tự động highlight từ vựng học thuật xuất hiện trong bài viết.
  - Nút thả tim (Reaction counter) và nút Báo cáo vi phạm (Report).

---

## 4. Màn Hình Dictation & Listening (Dictation Screen)

### 4.1. Bố Cục Giao Diện (Layout Anatomy)
Mô phỏng cấu trúc trải nghiệm của DailyDictation:

- **Header Controls**:
  - Tab chuyển đổi: `[ Dictation ]` (Chế độ luyện nghe chép) \| `[ Full Transcript ]` (Xem toàn bộ bài đọc song ngữ).
  - Bộ đếm tiến độ câu: `← 4 / 12 →` (Cho phép bấm phím mũi tên hoặc tự động chuyển câu khi hoàn thành 100%).
- **Snippet Audio Sticky Player**:
  - Trình phát âm thanh độc lập chỉ phát đoạn câu hiện tại (từ `audio_start` đến `audio_end`).
  - Nút Play/Pause, Seekbar thời gian ngắn, nút chọn tốc độ đọc (`0.75x`, `1.0x`, `1.25x`).
- **Khung Nhập Liệu Chữ (Textarea Input Box)**:
  - Khung gõ văn bản mở rộng, tự động focus con trỏ khi bắt đầu câu mới.
  - Nút Micro `[🎙️]` góc dưới bên phải: Kích hoạt Web Speech API để nhập liệu bằng giọng nói (Voice Dictation).
  - Nút `[ Skip ]`: Bỏ qua câu hiện tại nếu gặp câu quá khó.
- **Dòng Đánh Giá Thời Gian Thực (Live Feedback Line)**:
  - Từ gõ đúng: Màu Xanh lá (`Green`).
  - Từ gõ sai: Gạch chân màu Cam (`Orange Underline`) trực tiếp trong ô gõ.
  - Từ chưa gõ: Che bởi dấu sao `*******` đại diện cho độ dài từ.
- **Thanh Tùy Chọn Đánh Giá (Options Checkboxes)**:
  - `[x] Show answer immediately`: So sánh và gợi ý ký tự/từ thời gian thực.
  - `[ ] Show full answer`: Hiện 100% đáp án câu khi người học bị tắc.

