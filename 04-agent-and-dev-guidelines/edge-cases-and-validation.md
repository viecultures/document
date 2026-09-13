# ⚠️ Các Điểm Bất Thường & Quy Tắc Xử Lý Ngoại Lệ (Edge Cases & Anomaly Rules)

Tài liệu này tổng hợp toàn bộ các **khoảng trống nghiệp vụ, trường hợp ngoại lệ (Edge Cases) và điểm có thể gây xung đột** để Developers, Marketing và AI Agents phát hiện và xử lý sớm, tránh lỗi hệ thống hoặc xung đột trải nghiệm.

---

## 1. Mảng Bài Đọc Song Ngữ & Âm Thanh AI (BR-01 Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-01.1** | Bài đọc bị lệch số lượng đoạn văn giữa tiếng Anh và tiếng Việt (`EN.length != VI.length`). | **Hệ thống từ chối lưu bài (Validation Error)**. Biên tập viên hoặc AI Generator bắt buộc phải chia lại đoạn sao cho tỷ lệ đoạn 1:1 tuyệt đối. |
| **EC-01.2** | File âm thanh AI Shadowing chưa được khởi tạo xong hoặc bị lỗi URL (404/500). | Trình nghe Audio hiển thị trạng thái *"Đang khởi tạo âm thanh..."* với icon loading. Màn hình đọc vẫn cho phép người dùng đọc chữ bình thường, không làm nghẽn ứng dụng. |
| **EC-01.3** | Màn hình điện thoại quá hẹp (Mobile Web App) không đủ chỗ hiển thị 2 cột song song. | **Quy tắc Responsive**: Tự động chuyển giao diện từ 2 cột song song (Desktop) sang dạng **Xếp chồng (Stacked)**. Đoạn tiếng Việt hiển thị phía dưới đoạn tiếng Anh với nút bật/tắt (Toggle) Ẩn/Hiện bài dịch. |

---

## 2. Mảng Trích Xuất & Quản Lý Từ Vựng (BR-02 Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-02.1** | Một từ vựng học thuật xuất hiện ở nhiều bài đọc khác nhau với các câu ngữ cảnh khác nhau. | Hệ thống lưu trữ `VocabItem` dưới dạng danh thể gắn với bài đọc (`PostVocabInstance`). Mỗi khi học bài đọc nào, Flashcard sẽ hiển thị đúng câu ngữ cảnh gốc của bài đọc đó. |
| **EC-02.2** | Từ vựng là cụm từ (Phrasal Verbs, Cụm từ cố định như *take place*, *cultural heritage*). | Hệ thống hỗ trợ lưu trữ cụm từ (Multi-word Expressions) làm 1 thực thể từ vựng độc lập, không ép buộc chỉ trích xuất từ đơn. |
| **EC-02.3** | Bài đọc được tạo nhưng không có câu ngữ cảnh cho từ vựng trích xuất. | **Lỗi nghiêm trọng (Blocker)**: Cấm xuất bản bài đọc nếu có từ vựng thiếu trường `context_sentence`. |

---

## 3. Mảng Cảm Nghĩ Cộng Đồng & Kiểm Duyệt UGC (BR-03 Edge Cases)

> [!IMPORTANT]
> **Xung đột nghiệp vụ quan trọng**: Làm sao duy trì triết lý *"Không chấm điểm / Không sửa lỗi ngữ pháp"* nhưng vẫn bảo vệ môi trường cộng đồng khỏi *"Nội dung độc hại, Spam, Vi phạm văn hóa/lịch sử"*?

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-03.1** | Người dùng đăng bài Reflection chứa từ ngữ thù hận, spam link, hoặc nội dung vi phạm thuần phong mỹ tục. | **Quy tắc Kiểm duyệt Thụ động (Passive Moderation)**:<br>1. Tuyệt đối **không** dùng AI để chấm điểm tiếng Anh.<br>2. **CÓ** dùng bộ lọc từ cấm (Automated Keyword Moderation) để tự động chuyển bài viết có dấu hiệu vi phạm vào hàng chờ kiểm duyệt (Pending Review).<br>3. Cung cấp nút **"Báo cáo vi phạm" (Report)** cho cộng đồng. |
| **EC-03.2** | Người dùng sử dụng các dạng biến thể của từ vựng học thuật trong bài viết (chia thì, số nhiều: *preserved*, *cities*). | Hệ thống tích hợp thuật toán **Lemmatization** để tự động nhận diện từ gốc (`preserve`, `city`) và vẫn highlight/gạch chân từ vựng học thuật trong bài Reflection đó. |
| **EC-03.3** | Người dùng nhấn Đăng Reflection nhưng bài viết trống hoặc chỉ có ký tự trắng. | Nút "Đăng" bị disable. Hệ thống yêu cầu bài Reflection phải có tối thiểu 10 ký tự. |

---

## 4. Mảng Flashcards & Ôn Tập (BR-04 Edge Cases)

| Mã ngoại lệ | Trường hợp bất thường | Quy tắc xử lý hệ thống (Validation & Handling Rule) |
| :--- | :--- | :--- |
| **EC-04.1** | Người dùng liên tục nhấn 🔴 *"Cần ôn lại"* trong phiên học khiến hàng chờ bị lặp vô tận. | Nếu một thẻ bị chọn *"Cần ôn lại"* quá **3 lần trong cùng 1 phiên học**, hệ thống sẽ hiển thị gợi ý: *"Từ này có vẻ khó với bạn. Hãy đọc lại câu ngữ cảnh trong bài học!"* và tạm thời hoàn thành phiên để tránh gây mệt mỏi nhận thức. |
| **EC-04.2** | Người dùng thoát ứng dụng khi mới học được một nửa số Flashcard. | Hệ thống tự động lưu trạng thái (Auto-save progress). Khi mở lại, cho phép người dùng tiếp tục phiên học dở dang. |

---

## 5. Danh Sách Câu Hỏi Nghiệp Vụ Cần Ban Quản Lý (Business) Chốt Thêm

1. **Huy hiệu & Điểm thưởng (Gamification)**: Có nên tích hợp chuỗi ngày học (Streak) hoặc điểm thưởng khi viết Reflection không?
2. **Offline Mode trên Mobile Web**: Khi mất kết nối Internet, ứng dụng có hỗ trợ tiếp tục học Flashcard offline hay không?
