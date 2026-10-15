# 🤖 [Interface] Domain Bản Đồ Khám Phá & Trợ Lý AI Companion

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Bước 6)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md) (`TIER_FREE`: 3 lượt/ngày, `TIER_PREMIUM`: không giới hạn)
- Tham chiếu Ngoại lệ: [`edge_cases_and_validation.md`](../00_core/edge_cases_and_validation.md) (`EC-05.1`, `EC-05.2`, `EC-05.3`)

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `03_domain_ai_companion` chịu trách nhiệm:
1. Quản lý bản đồ khám phá văn hóa tương tác theo vùng miền (Bắc, Trung, Nam).
2. Tích hợp mô hình ngôn ngữ lớn (Google Gemini API qua Google AI Studio API Key).
3. Đóng vai trò là **"Người bạn đồng hành văn hóa" (Cultural Learning Companion)** hỗ trợ giải thích từ vựng, mở rộng kiến thức và đàm thoại tiếng Anh vừa sức.
4. Điều phối luồng chào hỏi, nắm bắt tâm trạng (mood check) và cơ chế dự phòng (Fallback Mechanism) khi kho bài học chưa có nội dung chi tiết.

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`conversational_flows.md`](./conversational_flows.md): Luồng hội thoại chuẩn, Onboarding, kiểm tra tâm trạng/sở thích và phân tầng thông tin Macro-to-Micro.
2. [`fallback_mechanisms.md`](./fallback_mechanisms.md): Cơ chế dự phòng xử lý khi người dùng yêu cầu chủ đề chưa có bài đọc chi tiết (Summary + Discussion Prompts).

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Nhận từ `01_domain_reader` & `00_core`:** Nhận `lessonId`, `topic`, `title_en`, `summary`, `counter_perspective` để làm ngữ cảnh hội thoại sâu bám sát bài đọc người học vừa hoàn thành.
- **Kích hoạt sau nâng cấp Pro (Pro Onboarding Chat):** Nhận event từ `07_domain_startup_business` khi nâng cấp Pro thành công, tự động khởi tạo tin nhắn chào mừng và 2–3 gợi ý đàm thoại nhanh (Quick Prompts) bằng tiếng Anh.
- **Giao tiếp với `07_domain_startup_business`:** Kiểm tra hạn mức tương tác (Free User: 3 requests/ngày; Premium/Trial: Unlimited).
- **Tính toán chi phí COGS:** Mỗi lượt chat tiêu tốn token đầu vào/đầu ra, được hạch toán vào mô hình chi phí của `07_domain_startup_business`.
