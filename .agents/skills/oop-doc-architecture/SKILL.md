---
name: oop-doc-architecture
description: >-
  Hướng dẫn thiết kế và tổ chức tài liệu kỹ thuật theo kiến trúc Hướng Đối Tượng (OOP-style Documentation): phân tách Domain, Interface cha, Implementation con, và Single Source of Truth. Kích hoạt khi khởi tạo dự án mới, viết docs hệ thống hoặc refactor tài liệu kỹ thuật.
---

# Hướng Dẫn Thiết Kế OOP Docs Architecture (OOP-Style Documentation)

Skill này cung cấp phương pháp tổ chức tài liệu kỹ thuật theo triết lý Lập trình hướng đối tượng (OOP), đảm bảo tài liệu rõ ràng, dễ bảo trì, tránh phình to token và ngăn ngừa xóa nhầm thông tin.

## 1. Cấu Trúc Thư Mục Mẫu (Standard Directory Trees)

### A. Cấu Trúc Cho Sản Phẩm Web Startup / SaaS / EdTech (Khuyến nghị cho Web Product)
```text
docs/
├── README.md                      # [Root Index] Bảng điều hướng toàn hệ thống & Map Domain
├── 00_core/                       # Nền tảng cốt lõi, Single Source of Truth & Contracts
│   ├── system_constants.md        # [SSOT] Hằng số dùng chung (Enums, Tốc độ, Bảng giá, Level)
│   ├── interface_learning_loop.md # [Core Loop] Chu trình trải nghiệm người dùng trọng tâm
│   ├── system_data_dictionary.md  # Thực thể dữ liệu trung tâm (Entities & Relations)
│   └── edge_cases_and_validation.md # Xử lý ngoại lệ & quy tắc biên hệ thống
├── 01_domain_<feature_a>/         # Domain tính năng A (VD: reader, catalog, checkout)
│   ├── interface_<feature_a>.md   # Interface cha: Ranh giới trách nhiệm, props, events
│   ├── concrete_flow_1.md         # File con triển khai chi tiết
│   └── concrete_rules.md          # Quy tắc nghiệp vụ chuyên biệt
├── 02_domain_<feature_b>/         # Domain tính năng B (VD: ai_companion, flashcards)
│   ├── interface_<feature_b>.md
│   └── ...
└── 07_domain_startup_business/    # Domain Kinh doanh & Vận hành Startup
    ├── interface_business.md      # Phân tầng người dùng (Roles & Subscriptions)
    ├── financial_model_cogs.md    # Dự phóng tài chính, biến phí COGS, P&L
    └── user_testing_plan.md       # Kế hoạch kiểm thử người dùng & hoàn thiện sản phẩm
```

### B. Cấu Trúc Cho Dự Án Game / Interactive Systems
```text
docs/
├── README.md                      # [Root Index] Mục lục điều hướng toàn hệ thống
├── 00_core/                       # Kiến trúc cốt lõi, Game Loop / App Loop
│   ├── interface_core.md          # Interface: Luồng đời sống & contract chung
│   └── architecture.md            # Triển khai chi tiết kiến trúc client-server
├── 01_domain_a/                   # Domain nghiệp vụ 1 (VD: mechanics, auth, user)
│   ├── interface_domain_a.md      # Interface cha: Phạm vi & quy chuẩn chung
│   ├── concrete_item_1.md         # File con 1: Chi tiết từng đối tượng cụ thể
│   └── concrete_item_2.md         # File con 2
└── 02_domain_b/                   # Domain nghiệp vụ 2 (VD: economy, billing)
    ├── interface_domain_b.md
    └── ...
```

---

## 2. Quy Chuẩn Nội Dung Từng Cấp Độ

### A. Root Index (`docs/README.md`)
- Là điểm chạm đầu tiên khi agent hoặc lập trình viên đọc dự án.
- Chứa:
  1. Tóm tắt ngắn gọn tầm nhìn dự án.
  2. Bảng mục lục các Domain kèm đường dẫn link markdown click được (`[Tên Domain](./01_domain/interface_domain.md)`).
  3. Sơ đồ liên kết tổng thể (Mermaid diagram hoặc text graph).

### B. Interface Cha (`interface_<domain>.md`)
- Đóng vai trò như một **Class Interface**:
  1. Định nghĩa ranh giới trách nhiệm (Responsibilities).
  2. Danh sách các file con triển khai (Implementations).
  3. Danh sách các Event / API / Hợp đồng dữ liệu mà domain này giao tiếp với các domain khác.

### C. File Triển Khai Con (Child Implementations)
- Luôn mở đầu bằng mục:
  ```markdown
  ## 1. Phụ Thuộc & Tham Chiếu (Dependencies)
  - Kế thừa từ: [interface_<domain>.md](./interface_<domain>.md)
  - Phụ thuộc dữ liệu: [Tên File](../path/to/file.md)
  ```
- Định nghĩa chi tiết các thông số, trạng thái, công thức tính toán.
- **Quy tắc bất biến:** Không copy-paste định nghĩa của domain khác; chỉ dẫn link tới file gốc.

---

## 3. Workflow Áp Dụng Khi Làm Việc
1. **Khi nhận yêu cầu mới:** Đọc `docs/README.md` -> đi vào `interface_<domain>.md` -> đọc file chi tiết liên quan.
2. **Khi thay đổi logic:** Cập nhật file con cụ thể trước, sau đó đồng bộ interface cha nếu có thay đổi về hợp đồng/API.
3. **Khi bổ sung tính năng mới:** Tạo file con mới trong đúng domain, đăng ký file con đó vào `interface_<domain>.md` và `docs/README.md`.
