# Kiến trúc Quản lý Hành trình học và Bài đọc song ngữ

Tài liệu đặc tả kiến trúc dữ liệu và API quản lý nội dung giữa Hành trình học (Learning Journey) và Bài đọc thông thường (Standalone Reading Post).

## 1. Phân loại nội dung

Hệ thống chia nội dung thành 2 hình thức:

1. **Hành trình học (Learning Journey / Series):**
   - Đại diện cho chuỗi trải nghiệm học tập gắn liền với một địa phương (`provinceId`, `region`) và chủ đề (`theme`).
   - Một hành trình chứa danh sách các chặng bài đọc có thứ tự (`chapterOrder: 1, 2, 3...`). Khuyến nghị tiêu chuẩn 3 chặng để hiển thị tối ưu trên bản đồ Discovery.
   - Hiển thị trên `/discovery` ở chế độ Bản đồ/Hành trình (`<DiscoveryJourney />`).

2. **Bài đọc thông thường (Standalone Reading Post / Editorial Story):**
   - Các bài đọc đơn lẻ không thuộc chuỗi bài nào (`journey_id = null`).
   - Phân loại theo trình độ CEFR (`level`), chủ đề (`topic`), địa phương (`region`/`provinceId`).
   - Hiển thị trên `/discovery?view=stories` dạng lưới thẻ xã luận (`<EditorialStory />`).

---

## 2. Mô hình Thực thể Quan hệ (Entity-Relationship)

```mermaid
erDiagram
    LEARNING_JOURNEY ||--o{ READING_POST : "chứa (chapter_order)"
    READING_POST ||--o{ PARAGRAPH_PAIR : "chia đoạn song ngữ"
    READING_POST ||--o{ VOCAB_ITEM : "trích xuất từ vựng"
    READING_POST ||--o{ QUIZ_QUESTION : "câu hỏi ôn tập"

    LEARNING_JOURNEY {
        string id PK "Slug (ví dụ: pho-hanoi) hoặc chuỗi định danh"
        string title_en "Tiêu đề tiếng Anh"
        string title_vi "Tiêu đề tiếng Việt"
        string theme "cuisine | places | crafts | festivals | history"
        string province_id "Mã định danh tỉnh (ví dụ: ha-noi)"
        string region "north | central | south"
        string description "Mô tả hành trình"
        string image_url "Ảnh đại diện"
        string status "published | draft | upcoming"
        timestamp created_at "Thời gian tạo"
    }

    READING_POST {
        string id PK "UUID"
        string journey_id FK "Khóa ngoại tới LEARNING_JOURNEY (nullable)"
        int chapter_order "Thứ tự chặng trong hành trình (1, 2, 3...) - nullable nếu độc lập"
        string province_id "Mã tỉnh gắn liền (nullable)"
        string topic_group "Nhóm bài viết đa cấp độ"
        string title_en "Tiêu đề EN"
        string title_vi "Tiêu đề VI"
        string topic "Chủ đề văn hóa"
        string region "Vùng miền"
        string image_url "Ảnh bìa"
        string level "Trình độ CEFR: A1, A2, B1, B2, C1, C2"
        string read_time "Thời lượng đọc"
    }
```

---

## 3. Danh mục API

### 3.1. Hành trình học (`/api/journeys`)
- `GET /api/journeys`: Danh sách hành trình kèm bộ lọc theo `region`, `provinceId`, `theme`, `status`, `query`.
- `GET /api/journeys/{id}`: Chi tiết hành trình kèm danh sách chặng bài đọc theo thứ tự (`chapterOrder`).
- `POST /api/journeys`: Tạo mới hành trình (tự sinh slug hoặc nhận slug tùy chỉnh).
- `PUT /api/journeys/{id}`: Cập nhật thông tin hành trình và danh sách thứ tự chặng bài đọc.
- `DELETE /api/journeys/{id}`: Xóa hành trình (tách bài đọc liên kết thành độc lập hoặc xóa phụ thuộc).

### 3.2. Bài đọc (`/api/posts`)
- Hỗ trợ thêm tham số truy vấn:
  - `standalone=true`: Lọc bài đọc độc lập (chưa gán vào hành trình).
  - `journeyId={id}`: Lọc các bài đọc trực thuộc một hành trình cụ thể.
- Request payload hỗ trợ `journeyId`, `chapterOrder`, `provinceId`.
