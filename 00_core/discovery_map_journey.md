# Bản đồ hành trình đọc: xem tỉnh và mảng ảnh bài viết

## Phạm vi bản thử

Trang Khám phá (`/discovery`, chế độ Journey) giữ luồng ba mức: toàn quốc → miền → tỉnh. Ở bản thử này chỉ Hà Nội có màn hình chi tiết tỉnh dạng ảnh ghép. Các tỉnh khác giữ cách chọn tỉnh và danh sách series hiện có. Miền Trung và miền Nam giữ trạng thái chưa mở của Journey.

## Luồng tương tác

1. Chọn Miền Bắc trên bản đồ hoặc trong danh sách vùng để xem các tỉnh thuộc miền Bắc.
2. Chọn Hà Nội để chuyển từ bản đồ miền sang hình Hà Nội phóng lớn, chiếm diện tích chính của khung bản đồ. Hình giữ đường bao tỉnh từ dữ liệu bản đồ hiện hành.
3. Bên trong đường bao có đúng ba mảng ảnh ghép mang tính minh họa, **không đại diện ranh giới quận/huyện**. Ba mảng lấy ảnh và nhãn từ các series đã xuất bản: Phở Hà Nội (`pho`), Chả cá Lã Vọng (`cha-ca-la-vong`), Bún chả (`bun-cha`). Mỗi mảng có tên và thứ tự rõ ràng.
4. Chọn một mảng bằng chuột, chạm hoặc bàn phím để mở bước chọn nội dung của series tương ứng bằng luồng chương và bài đọc hiện có. Không tạo bài viết hoặc đường dẫn mới. Phần series bên cạnh vẫn phản ánh tỉnh đang chọn.
5. Nút quay lại đưa người dùng về bản đồ các tỉnh Miền Bắc; nút quay về toàn quốc vẫn hoạt động. URL `region=north&place=ha-noi` tái tạo màn hình chi tiết khi tải lại hoặc chia sẻ.

## Quy tắc hiển thị

- Ba ảnh là ảnh hiện có trong registry của series; nếu ảnh tải lỗi, mảng vẫn có nhãn và thao tác chọn được.
- Mảng ảnh có viền phân tách, lớp phủ giúp đọc chữ và trạng thái hover/focus rõ ràng. Nội dung quan trọng không chỉ dựa vào màu sắc hay ảnh.
- Ở màn hình hẹp, hình Hà Nội vẫn xem được trọn vẹn và ba mục vẫn là mục tiêu chạm riêng biệt. Có nhãn truy cập cho mỗi mục.
- Phần ghép là minh họa bài viết trong Hà Nội, không khẳng định vị trí địa lý của món ăn hay di sản trong tỉnh.
