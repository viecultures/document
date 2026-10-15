# 🤝 [Interface] Domain Cảm Nghĩ Cộng Đồng (Community Reflections - UGC)

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Lớp mở rộng tùy chọn)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`UserReflection`)
- Tham chiếu Ngoại lệ: [`edge_cases_and_validation.md`](../00_core/edge_cases_and_validation.md) (`EC-03.1`, `EC-03.2`, `EC-03.3`)

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `06_domain_community` chịu trách nhiệm:
1. Cung cấp khung soạn thảo cảm nghĩ cá nhân (Reflections) sau khi đọc bài văn hóa.
2. Thực thi nghiêm ngặt triết lý **"Môi trường học tập không phán xét" (No-Judgment Policy)**: Tuyệt đối không chấm điểm ngữ pháp bài viết của người học.
3. Hỗ trợ thanh công cụ chèn nhanh từ vựng vừa học (Quick Vocab Toolbar).
4. Vận hành cơ chế kiểm duyệt nội dung thụ động (Passive Moderation) bảo vệ văn hóa và an toàn cộng đồng.

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`reflections_moderation.md`](./reflections_moderation.md): Quy định chính sách Không phán xét, bộ lọc từ cấm và cơ chế tương tác thả tim động viên.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Nhận từ `02_domain_vocab_flashcards`:** Danh sách từ vựng của bài học để hiển thị trên dải Quick Vocab Toolbar giúp người học bấm là chèn từ vào văn bản.
- **Gửi sự kiện sang `05_domain_gamification`:** Bắn event `onReflectionPosted(userId, reflectionId)` để ghi nhận điểm đóng góp cộng đồng.
