# ⚠️ Các Điểm Bất Thường & Quy Tắc Xử Lý Ngoại Lệ (Edge Cases & Anomaly Rules)

> **Kế thừa từ:** `00_core`  
> **Tham chiếu hằng số:** [`system_constants.md`](./system_constants.md)  
> **Phạm vi áp dụng:** Toàn bộ Developers, Marketing và AI Agents khi triển khai logic và giao diện.

---

## 1. Mảng Bài Đọc Song Ngữ & Âm Thanh (Reader & Audio Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-01.1** | Bài đọc bị lệch số lượng đoạn văn giữa tiếng Anh và tiếng Việt (`EN.length != VI.length`). | **Hệ thống từ chối lưu bài (Validation Error)**. Bắt buộc tỷ lệ khớp 1:1 tuyệt đối để giữ trọn mạch đọc song ngữ. |
| **EC-01.2** | File âm thanh chưa khởi tạo xong hoặc URL bị lỗi (404/500). | Trình Sticky Audio hiển thị trạng thái *"Đang tải âm thanh..."* với icon loading; màn hình đọc chữ vẫn hoạt động bình thường, không gây đơ ứng dụng. |
| **EC-01.3** | Màn hình điện thoại hẹp (Mobile Web App) không đủ chỗ hiển thị 2 cột song song. | **Quy tắc Responsive**: Chuyển sang dạng **Xếp chồng (Stacked)**. Mỗi đoạn tiếng Anh đi kèm 1 toggle bật/tắt bản dịch tiếng Việt phía dưới. |

---

## 2. Mảng Trích Xuất & Quản Lý Từ Vựng (Vocab Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-02.1** | Một từ xuất hiện ở nhiều bài đọc khác nhau với các câu ngữ cảnh khác nhau. | Hệ thống lưu trữ `VocabItem` gắn với bài đọc cụ thể (`PostVocabInstance`). Khi học bài nào, Flashcard hiển thị đúng câu ngữ cảnh gốc của bài đó. |
| **EC-02.2** | Từ vựng là cụm từ (Phrasal Verbs, Collocations: *take place*, *cultural heritage*). | Hệ thống hỗ trợ lưu trữ cụm từ độc lập, không ép buộc chỉ trích xuất từ đơn lẻ. |
| **EC-02.3** | Bài đọc được tạo nhưng có từ vựng thiếu câu ngữ cảnh gốc. | **Lỗi nghiêm trọng (Blocker)**: Cấm xuất bản bài đọc nếu có từ vựng thiếu trường `context_sentence`. |

---

## 3. Mảng Cảm Nghĩ Cộng Đồng & Kiểm Duyệt UGC (UGC Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-03.1** | Bài Reflection chứa từ ngữ thù hận, spam link hoặc nội dung phản cảm. | **Kiểm duyệt Thụ động (Passive Moderation)**: Tuyệt đối không chấm điểm ngữ pháp tiếng Anh; sử dụng bộ lọc từ cấm tự động chuyển bài sang `pending_review` và cung cấp nút Report cho cộng đồng. |
| **EC-03.2** | Người dùng sử dụng dạng biến thể của từ vựng học thuật (chia thì, số nhiều: *preserved*, *cities*). | Hệ thống tích hợp thuật toán **Lemmatization** để tự động nhận diện từ gốc (`preserve`, `city`) và vẫn highlight từ vựng trong bài viết. |
| **EC-03.3** | Người dùng nhấn Đăng Reflection nhưng bài viết trống hoặc dưới 10 ký tự. | Nút "Đăng" bị disable; yêu cầu bài viết tối thiểu 10 ký tự. |

---

## 4. Mảng Flashcards & Ôn Tập (Review Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-04.1** | Người dùng liên tục nhấn 🔴 *"Cần ôn lại"* trong phiên học khiến hàng chờ bị lặp vô tận. | Nếu một thẻ bị chọn *"Cần ôn lại"* quá **3 lần trong cùng 1 phiên học**, hệ thống gợi ý: *"Từ này có vẻ khó với bạn. Hãy đọc lại câu ngữ cảnh trong bài học!"* và tạm thời hoàn thành phiên để tránh mệt mỏi nhận thức. |
| **EC-04.2** | Người dùng thoát ứng dụng khi mới học được một nửa số Flashcard. | Hệ thống tự động lưu trạng thái (Auto-save progress). Khi mở lại, cho phép người dùng tiếp tục phiên học dở dang. |

---

## 5. Mảng Trợ Lý Đàm Thoại AI Map (AI Companion Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-05.1** | Người dùng truy vấn một chủ đề/địa danh chưa có bài học chi tiết trong kho dữ liệu. | **Cơ chế Dự phòng (Fallback Mechanism)**:<br>1. AI từ chối lịch sự, nêu rõ giới hạn dữ liệu hiện tại.<br>2. Tự động lấy **đoạn tóm tắt (summary)** hoặc đề xuất chủ đề tương đương đã có bài.<br>3. Chuyển sang hiển thị **gợi ý thảo luận (discussion prompts)** để duy trì mạch hội thoại. |
| **EC-05.2** | Người dùng yêu cầu đọc toàn bộ văn bản bài báo/bài học chi tiết ngay trong khung chat AI. | Giao diện chat không phục vụ việc đọc bài viết dài. AI cung cấp 1 đoạn tóm tắt ngắn (3–4 câu), sau đó gửi link điều hướng người học mở bài đọc tại giao diện Reader (`/lessons/:id`). |
| **EC-05.3** | Người dùng chưa cấu hình Google AI Studio API key hoặc key bị hết hạn/quota. | Khung chat hiển thị thông báo trạng thái thân thiện kèm nút mở **Modal hướng dẫn 3 bước lấy key miễn phí**, tuyệt đối không gây crash ứng dụng hoặc đóng băng bản đồ. |
