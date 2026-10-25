# Thiết kế lại trang đăng nhập VieCultures

Ngày: 25/10/2026. Phạm vi: giao diện route `/login`, giữ nguyên luồng xác thực hiện tại và tham số `redirect` nội bộ.

## Mục tiêu

- Đồng nhất với hướng landing ẩm thực: nền kem/rice paper, xanh di sản, điểm nhấn vàng ấm, Be Vietnam Pro cho tiêu đề và nội dung; logo chung giữ nhận diện hiện tại.
- Đưa biểu mẫu làm trọng tâm. Cột minh họa dùng ảnh Phở đã có trong `frontend/public/images/series/pho-hanoi.jpg`, lời giới thiệu ngắn về học tiếng Anh qua câu chuyện món ăn. Bỏ nền xanh lam, danh sách hứa hẹn dài, số liệu và tuyên bố chưa được kiểm chứng.
- Hai chế độ Đăng nhập/Đăng ký cùng một khung biểu mẫu; người dùng hiểu rõ đang ở chế độ nào. Trên màn hình nhỏ, ưu tiên biểu mẫu, ẩn cột minh họa.

## Nội dung và tương tác

1. Logo dẫn về `/`; link quay về trang chủ hiện rõ ở đầu biểu mẫu.
2. Tab đăng nhập/đăng ký giữ trạng thái hiện có, không đổi API. Email, mật khẩu, họ tên khi đăng ký, ghi nhớ đăng nhập, quên mật khẩu, thông báo lỗi và trạng thái đang xử lý tiếp tục hoạt động.
3. Trường nhập, nút và link quan trọng có vùng bấm tối thiểu 44px; nhãn từ 14px, nội dung từ 16px; focus rõ, lỗi dễ đọc trên nền sáng.
4. Ở chế độ local, chỉ hiển thị một nút `Dùng thử tài khoản mẫu` gọi `localAuthService.loginDemo()`. Không gắn nhãn Google/Facebook lên cùng hành động demo. Ở chế độ backend, dùng Google chính thức khi được cấu hình; không hiển thị nút Facebook chưa hỗ trợ.
5. Kết quả đăng nhập tiếp tục đi tới đường dẫn `redirect` nội bộ hợp lệ hoặc `/home`. Modal quên mật khẩu giữ nguyên.
6. Chuyển động chỉ là phản hồi hover/focus ngắn, tôn trọng `prefers-reduced-motion`.

## Kiểm tra hoàn thành

- Bố cục đọc được ở 375, 768, 1024, 1440px và chiều cao màn hình thấp; không khóa cuộn biểu mẫu.
- Build production thành công. Không tự chạy unit/integration/E2E test theo `frontend/AGENTS.md`.
- Commit và push thay đổi vào `origin main` của đúng repo.
