# 📑 Cấu Trúc Cặp Đoạn Song Ngữ (Paragraph Pairing Specification)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_reader.md`](./interface_reader.md)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`ParagraphPair`)
- Tham chiếu Ngoại lệ: [`edge_cases_and_validation.md`](../00_core/edge_cases_and_validation.md) (`EC-01.1`, `EC-01.3`)

---

## 2. Quy Tắc Đối Xứng Cặp Đoạn 1:1 Nghiêm Ngặt

1. **Nguyên tắc không đứt gãy tư duy:** Mỗi đoạn văn tiếng Anh (`en_text`) được đặt tương ứng trực tiếp với đúng một đoạn dịch tiếng Việt (`vi_text`).
2. **Quy định biên dịch:**
   - Bản dịch tiếng Việt đóng vai trò hỗ trợ giải nghĩa, không dịch phóng tác quá đà làm lệch vị trí các từ vựng mục tiêu.
   - Tuyệt đối không gộp 2 đoạn tiếng Anh vào 1 đoạn tiếng Việt hoặc ngược lại.

---

## 3. Chiến Lược Hiển Thị Responsive (Desktop vs Mobile)

### A. Giao Diện Desktop Web (Màn hình >= 1024px)
- **Bố cục 2 cột song song (Side-by-Side Split View):**
  - Cột trái (50% chiều rộng): Văn bản tiếng Anh với cỡ chữ 18px, khoảng cách dòng `line-height: 1.8`, font có chân thanh lịch (Merriweather / Playfair Display).
  - Cột phải (50% chiều rộng): Bản dịch tiếng Việt hỗ trợ với tone màu xám di sản nhẹ hơn (`#4A5568`), giúp mắt người đọc ưu tiên tập trung vào văn bản tiếng Anh.
  - Các đoạn văn ngang hàng tự động căn chỉnh chiều cao để người học dễ dàng đối soát mắt khi gặp câu khó.

### B. Giao Diện Mobile Web (Màn hình < 1024px)
- **Bố cục dạng Khối Xếp Chồng (Stacked Card View):**
  - Khối tiếng Anh hiển thị trước.
  - Phía dưới mỗi đoạn tiếng Anh có một nút thu gọn/mở rộng dạng toggle: `[👁️ Xem bản dịch tiếng Việt]`.
  - Mặc định bản dịch được ẩn để kích thích người học nỗ lực đọc hiểu tiếng Anh trước khi kiểm tra nghĩa tiếng Việt.
