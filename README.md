# VieCultures – Hệ Thống Tài Liệu Dự Án (Project Documentation)

> **Dự án:** VieCultures  
> **Slogan / Tagline:** *"Learn the language. Tell the culture."* (Gom từng từ nhỏ, hiểu một Việt Nam lớn)  
> **Khách hàng mục tiêu:** Sinh viên đại học và người trẻ Việt Nam 18–25 tuổi (CEFR A2–B2)  
> **Giai đoạn hiện tại:** Chuẩn bị Checkpoint 1 (CP1) – Capstone Startup Project (Kỳ 7)

Chào mừng bạn đến với kho tài liệu chính thức của dự án **VieCultures** – Nền tảng học tiếng Anh qua bản sắc văn hóa Việt Nam. Tài liệu này được thiết kế nhằm đồng bộ góc nhìn toàn diện cho toàn bộ đội ngũ liên ngành: Kinh doanh quốc tế, Kỹ thuật phần mềm và Marketing.

---

## 👥 Đội Ngũ Sáng Lập (Team VieC)

| Thành viên | Chuyên ngành | Vai trò trong dự án |
| :--- | :--- | :--- |
| **Trần Nguyễn Minh Bảo** | Kinh doanh Quốc tế | Trưởng nhóm / Chiến lược Sản phẩm & Mô hình Kinh doanh |
| **Ninh Thiện Luân** | Kỹ thuật Phần mềm | Phát triển Kiến trúc Frontend & Dịch vụ Backend |
| **Nguyễn Phú Cường** | Kỹ thuật Phần mềm | Lập trình Fullstack & Kiểm thử Kỹ thuật |
| **Nguyễn Thị Thảo Tâm** | Marketing | Nghiên cứu Khách hàng Mục tiêu & Phân tích Đối thủ |
| **Phan Phục Trinh** | Marketing | Quản lý Nội dung Song ngữ & Đảm bảo Tính Chuẩn xác Văn hóa |
| **Nguyễn Trung Nam** | Marketing | Nghiên cứu Thị trường & Kế hoạch Thu hút Người dùng |

---

## 📁 Cấu Trúc Thư Mục Tài Liệu

```
document/
├── presentation.md                # Bản thuyết trình CP1 chuẩn 14 slide (English)
├── presentation_vn.md             # Bản thuyết trình CP1 chuẩn 14 slide (Tiếng Việt kèm Speaker Notes)
├── conceptual-diagram.md          # Sơ đồ thực thể quan niệm & đặc tả ngữ nghĩa (Entities Only)
├── conceptual-diagram.mmd         # File mã nguồn Mermaid ERD quan niệm
├── design.md                      # Hệ thống quy chuẩn thiết kế UI & Design Tokens
├── ideas.md                       # Ý tưởng sản phẩm & Dữ liệu so sánh FPT Idea Checklist
├── questions.md                   # Ngân hàng câu hỏi Q&A và giải đáp phản biện
│
├── 01-overview/                   # Tổng quan dự án, tầm nhìn & đối tượng người dùng
│   ├── vision-and-goals.md        # Tầm nhìn, sứ mệnh, mục tiêu & Persona Minh (20 tuổi)
│   ├── features-list.md           # Phân định phạm vi cốt lõi MVP vs Lộ trình mở rộng
│   ├── product-roadmap.md         # Kế hoạch hành động thực tế sau CP1 & Mô hình Freemium
│   └── glossary.md                # Từ điển thuật ngữ nghiệp vụ và kỹ thuật chuẩn hóa
│
├── 02-business-rules/             # Quy tắc nghiệp vụ chi tiết (Core Business Rules)
│   ├── BR-01-reading-content.md   # Bài đọc song ngữ cặp đoạn & Âm thanh câu
│   ├── BR-02-vocab-extraction.md  # Trích xuất từ vựng ngữ cảnh (Bắt buộc câu gốc)
│   ├── BR-03-reflections-ugc.md   # Cảm nghĩ cộng đồng (Chính sách không phán xét)
│   ├── BR-04-flashcard-spaced.md  # Ôn tập Flashcard 2 mặt & Đánh giá nhị phân
│   ├── BR-05-user-journey.md      # Luồng trải nghiệm 5 bước cốt lõi của MVP
│   └── BR-06-gamification-habits.md # Cơ chế Streak & Game hóa (Giai đoạn mở rộng)
│
├── 03-product-spec/               # Mô tả sản phẩm & Giao diện (UI/UX Specification)
│   ├── sitemap-and-navigation.md  # Điều hướng sitemap & Chiến lược Responsive
│   ├── screen-specs.md            # Chi tiết từng màn hình chính (Reader, Flashcards)
│   └── content-management.md      # Quy trình biên soạn/nhập liệu bài học (CMS/Admin Workflow)
│
└── 04-agent-and-dev-guidelines/   # Hướng dẫn Kỹ thuật & AI Agent
    ├── system-data-dictionary.md  # Từ điển dữ liệu hệ thống (Entities & Schemas)
    └── edge-cases-and-validation.md# Danh sách các điểm bất thường & Quy tắc ngoại lệ
```

---

## 🎯 Nguyên Tắc Cốt Lõi Nghiệp Vụ (Core Rules Summary)

1. **Nội dung song ngữ cặp đoạn (1:1):** Bài đọc chính tiếng Anh đối xứng với bản dịch tiếng Việt hỗ trợ, duy trì mạch đọc liền mạch không bị gián đoạn.
2. **Ngữ cảnh là số 1:** Tuyệt đối không học từ vựng trơ trọi; mọi từ vựng trích xuất bắt buộc phải gắn liền với câu ngữ cảnh gốc (`context_sentence`).
3. **Thao tác 1 chạm (1-Click Save):** Tra cứu từ vựng popup trực tiếp trên bài đọc và lưu ngay vào sổ tay ôn tập mà không phải mở từ điển ngoài.
4. **Flashcard nhị phân đơn giản:** Luyện nhớ chủ động 2 mặt với 2 lựa chọn: 🟢 *"Đã nhớ"* hoặc 🔴 *"Cần ôn lại"*, loại bỏ áp lực nhận thức.
5. **Khám phá ẩm thực & văn hóa 54 dân tộc / các tỉnh thành:** Đem lại sự hào hứng và vốn từ thực tế để người học tự tin giới thiệu bản sắc quê hương.
