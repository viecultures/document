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
