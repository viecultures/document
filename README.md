# 📚 VN Culture Reader - Hệ Thống Tài Liệu Dự Án (Project Documentation)

Chào mừng bạn đến với kho tài liệu chính thức của dự án **VN Culture Reader** - Nền tảng EdTech học tiếng Anh qua ngữ cảnh văn hóa Việt Nam.

Tài liệu này được thiết kế nhằm mục đích **đồng bộ góc nhìn toàn diện** cho tất cả các thành viên trong team: **Business, Marketing, Developers (FE/BE) và các AI Agents**.

---

## 📂 Cấu Trúc Thư Mục Tài Liệu

```
document/
├── 01-overview/                   # Tổng quan dự án, tầm nhìn & đối tượng người dùng
│   ├── vision-and-goals.md        # Tầm nhìn, mục tiêu sản phẩm & Personas
│   ├── product-roadmap.md         # Lộ trình phát triển (Web MVP -> Mobile Web App)
│   └── glossary.md                # Từ điển thuật ngữ dùng chung (Glossary)
│
├── 02-business-rules/             # Quy tắc nghiệp vụ chi tiết (Core Business Rules)
│   ├── BR-01-reading-content.md   # Bài đọc song ngữ & Âm thanh AI (Shadowing)
│   ├── BR-02-vocab-extraction.md  # Trích xuất & Quản lý từ vựng trong ngữ cảnh
│   ├── BR-03-reflections-ugc.md   # Cảm nghĩ cộng đồng (UGC, Không chấm điểm/sửa lỗi)
│   ├── BR-04-flashcard-spaced.md  # Ôn tập Flashcard 2 mặt & Đánh giá nhị phân
│   └── BR-05-user-journey.md      # Luồng trải nghiệm người dùng & Luồng dữ liệu
│
├── 03-product-spec/               # Mô tả sản phẩm & Giao diện (UI/UX Specification)
│   ├── sitemap-and-navigation.md  # Điều hướng sitemap & Chiến lược Mobile-First Responsive
│   ├── screen-specs.md            # Chi tiết từng màn hình chính (Reader, Cards, Community)
│   └── content-management.md      # Quy trình biên soạn/nhập liệu bài học (CMS/Admin Workflow)
│
└── 04-agent-and-dev-guidelines/   # Hướng dẫn Kỹ thuật & AI Agent
    ├── system-data-dictionary.md  # Từ điển dữ liệu hệ thống (Entities & Schemas)
    ├── edge-cases-and-validation.md# Danh sách các điểm bất thường & Quy tắc ngoại lệ
    └── prompt-engineering-specs.md# Hướng dẫn Prompt AI (Audio & Trích xuất từ vựng)
```

---

## 🎯 Hướng Dẫn Đọc Tài Liệu Theo Vai Trò

- 📊 **Business / Marketing**: Đọc trước [`01-overview/vision-and-goals.md`](./01-overview/vision-and-goals.md) và toàn bộ thư mục [`02-business-rules/`](./02-business-rules/) để nắm rõ triết lý sản phẩm, thông điệp truyền thông và luồng người dùng.
- 💻 **Developers (FE / BE)**: Tập trung vào [`02-business-rules/`](./02-business-rules/), [`03-product-spec/`](./03-product-spec/), và [`04-agent-and-dev-guidelines/`](./04-agent-and-dev-guidelines/) để nắm rõ cấu trúc dữ liệu, giao diện và các trường hợp ngoại lệ.
- 🤖 **AI Agents**: Đọc [`02-business-rules/`](./02-business-rules/) và [`04-agent-and-dev-guidelines/edge-cases-and-validation.md`](./04-agent-and-dev-guidelines/edge-cases-and-validation.md) trước khi thực hiện viết code, sinh nội dung hoặc phân tích dữ liệu.

---

## 📌 Nguyện Tắc Cốt Lõi Nghiệp Vụ (Core Rules Summary)
1. **Nội dung song ngữ**: Bài đọc chính tiếng Anh, bài dịch tiếng Việt hỗ trợ, khớp theo từng cặp đoạn văn (Paragraph Pairing).
2. **Ngữ cảnh là số 1**: Từ vựng học thuật không đứng độc lập mà luôn đính kèm **câu ngữ cảnh gốc**.
3. **Môi trường an toàn (Reflections)**: Tuyệt đối **không chấm điểm, không sửa lỗi ngữ pháp** bài viết cảm nghĩ của người dùng nhằm xóa bỏ rào cản tâm lý.
4. **Flashcard nhị phân**: Ôn tập chủ động 2 mặt, tiến độ dựa trên 2 trạng thái tự đánh giá: *"Đã nhớ"* hoặc *"Cần ôn lại"*.
