# 🎙️ [Interface] Domain Luyện Nói & Phản Hồi Phát Âm

## 1. Phụ Thuộc & Kế Thừa (Dependencies)
- Kế thừa Core Loop: [`interface_learning_loop.md`](../00_core/interface_learning_loop.md) (Bước 4)
- Tham chiếu Hằng số (SSOT): [`system_constants.md`](../00_core/system_constants.md)
- Tham chiếu Dữ liệu: [`system_data_dictionary.md`](../00_core/system_data_dictionary.md) (`ParagraphPair.en_text`)

---

## 2. Ranh Giới Trách Nhiệm (Responsibilities)
Domain `04_domain_speaking_voice` chịu trách nhiệm:
1. Thu âm trực tiếp giọng đọc của người học thông qua Web Speech API trên trình duyệt.
2. So sánh và đối soát chuỗi âm thanh/văn bản nhận diện được với câu tiếng Anh chuẩn của bài học.
3. Cung cấp phản hồi trực quan (từ đúng màu xanh lá, từ phát âm chưa rõ/nuốt âm màu vàng cam).
4. Giúp người học giải tỏa rào cản e ngại (nỗi sợ sai khi nói đã được kiểm chứng 49% ở CP2).

---

## 3. Danh Sách Triển Khai Con (Implementations)
1. [`pronunciation_feedback.md`](./pronunciation_feedback.md): Đặc tả luồng ghi âm, cơ chế đối soát chuỗi từ và giao diện thẻ chấm điểm trực quan.

---

## 4. Hợp Đồng Giao Tiếp Liên Domain (Events & Contracts)
- **Nhận từ `01_domain_reader`:** Nhận câu văn bản mục tiêu (`targetSentence`) và mốc âm thanh để người học nghe mẫu trước khi thu âm.
- **Gửi sự kiện sang `05_domain_gamification`:** Bắn event `onSpeakingChallengeCompleted(sentenceId, accuracyScore)` để cộng điểm tiến bộ.
