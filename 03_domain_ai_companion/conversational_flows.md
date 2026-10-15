# 💬 Luồng Hội Thoại & Trải Nghiệm Đàm Thoại AI (Conversational Flows)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Interface: [`interface_ai_companion.md`](./interface_ai_companion.md)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`ReadingPost.summary`)
- Căn cứ thực tế: Buổi họp kỹ thuật ngày 14/10/2026 ghi nhận trong `record-meeting.md`.

---

## 2. Luồng Hội Thoại Chuẩn (Standard Dialogue Lifecycle)

```mermaid
flowchart TD
    A["1. Onboarding & Xưng danh Companion"] --> B["2. Mood & Interest Check (Nắm bắt sở thích)"]
    B --> C["3. Macro-to-Micro Navigation (Phân tầng địa lý)"]
    C --> D["4. Vivid Contextual Imagination (Tạo bối cảnh tưởng tượng)"]
    D --> E["5. English Practice & Cultural Explanation"]
```

### Bước 1: Mở đầu luồng (Onboarding & Identity)
- AI luôn chủ động xưng danh và khẳng định rõ vai trò là **"Người bạn đồng hành văn hóa Việt Nam"**.
- Tránh phong cách trợ lý hành chính thô ráp; dùng ngôn từ ấm áp, tôn vinh bản sắc.

### Bước 2: Nắm bắt tâm trạng & sở thích (Mood & Interest Check)
- AI không đổ dồn kiến thức ngay mà đặt 1–2 câu hỏi mở để lắng nghe tâm trạng hiện tại của người học:
  - *Ví dụ:* *"Hôm nay bạn thấy thế nào? Bạn đang thèm một món ăn nóng hổi miền Bắc hay muốn nghe về một truyền thuyết biển đảo miền Trung?"*
- Gợi ý 3 nhóm chủ đề chính: Ẩm thực (Cuisine), Di sản (Heritage), Làng nghề truyền thống (Handicrafts).

### Bước 3: Phân tầng thông tin (Macro to Micro Navigation)
- Điều hướng cuộc trò chuyện từ vùng vĩ mô xuống vi mô cực kỳ chi tiết:
  - *Vĩ mô:* Vùng Nam Bộ ➔ Thành phố Hồ Chí Minh.
  - *Vi mô:* Chợ hoa Tết Bến Bình Đông, quán cà phê vợt lâu năm ở quận 5.

### Bước 4: Tạo bối cảnh trải nghiệm sinh động (Contextual Imagination)
- Kích thích phản xạ tư duy bằng cách yêu cầu người học tưởng tượng:
  - *Ví dụ:* *"Imagine you are sitting on a small plastic stool by the sidewalk on a rainy afternoon, holding a warm bowl of Pho..."*
- Giúp người học tự tin dùng tiếng Anh diễn đạt cảm xúc chân thật thay vì học vẹt.
