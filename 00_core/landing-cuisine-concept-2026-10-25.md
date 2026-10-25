# Landing ẩm thực VieCultures — kế hoạch hai phase

Ngày: 25/10/2026. Trạng thái: phương án được người dùng xác nhận về định hướng ẩm thực; triển khai tại route xem trước `/landing-concept` trước khi cân nhắc thay trang `/`.

## Định hướng sản phẩm

Landing kể về việc học tiếng Anh qua món ăn Việt Nam: bắt đầu từ một món quen, đi sâu vào nguyên liệu, cách làm, bối cảnh đời sống và từ vựng trong từng chương. Trải nghiệm đọc thử không đòi đăng nhập, theo `presentation_product_flow.md`. Ẩm thực mọi miền là hướng phát triển nội dung; giao diện chỉ quảng bá bài đã có thật trong registry. Hiện sáu series ẩm thực đã `published` đều thuộc miền Bắc; series bánh mì Sài Gòn còn `draft`, miền Trung chưa có series ẩm thực trong registry. Không hiển thị thẻ bài học mở được cho nội dung chưa xuất bản.

Trang dùng `PublicLayout`, route `/landing-concept`, giữ `/` để so sánh. CTA đi qua `PATHS` và `paths.reader({ story })`. Dữ liệu series lấy từ `getPublishedSeries()` rồi lọc `theme === 'cuisine'`; không nhân bản danh sách nội dung bằng hằng số trong component.

## Phase 1 — Bố cục, nội dung và hình ảnh

1. **Header:** logo chung, anchor `Stories`, `How it works`, `The journey`, CTA đọc bài đầu. Menu nhỏ có nút mở/đóng, Escape và nhãn truy cập.
2. **Hero:** tiêu đề biên tập về món ăn như cánh cửa vào ngôn ngữ; mô tả ngắn, một CTA chính tới chương đầu của Phở, link phụ tới thư viện series. Dùng ảnh minh họa Phở trong `public/images/series/` làm trọng tâm cùng ảnh Bún chả/Chả cá ở lớp phụ. Bỏ video Hoi An khỏi bản xem trước vì nội dung hiện tập trung ẩm thực.
3. **Giá trị học tập:** ba nhịp `Taste the story` → `Hear the language` → `Keep the words`; mô tả đúng tính năng đọc song ngữ, audio, lưu từ và ôn flashcard đã có.
4. **Series:** thẻ biên tập cho series ẩm thực đã published, ảnh lấy từ metadata. Mỗi thẻ mở chương đầu tương ứng; tên món, tên vùng và số chương từ registry. Trình bày lần lượt món nổi bật rồi các món tiếp theo, tránh carousel tự đổi khi người dùng đang đọc.
5. **Đào sâu một món:** lấy Phở làm ví dụ để thể hiện ba chương liên tiếp, minh họa chiều sâu nội dung thay vì nhiều chủ đề rời rạc. CTA trực tiếp tới từng chương.
6. **Hành trình vùng miền:** cho thấy sản phẩm dự định mở rộng vào Trung và Nam bằng nhãn trạng thái trung thực, không dựng bài hoặc số liệu chưa có. Miền Bắc có thể dẫn tới các series đã xuất bản.
7. **Kết trang:** lời mời bắt đầu đọc và link khám phá thêm; dùng Footer chung. Không thêm testimonial, kết quả học tập hoặc số liệu chuyển đổi không có nguồn.

Visual sử dụng token trong `frontend/src/index.css`: nền `surface`, chữ `ink`/`ink-soft`, CTA `action`, điểm nhấn `accent-ink`, viền `line`; heading biên tập Playfair Display, giao diện Be Vietnam Pro. Hình vòm và đường dẫn mảnh gợi hành trình ẩm thực, không sao chép thương hiệu The Forum. Chữ hướng dẫn quan trọng từ 14px, nút từ 44px, focus rõ, ảnh có kích thước giữ chỗ và alt phù hợp.

## Phase 2 — Chuyển động kể chuyện

- Hero vào theo thứ tự: nhãn và tiêu đề 0,55–0,8 giây, mô tả và CTA chậm hơn 0,12–0,18 giây, mảng ảnh 0,9–1,2 giây. Nội dung vẫn hiển thị nếu animation không chạy.
- Khi cuộn, mỗi section mở theo nhịp tiêu đề → ảnh → nội dung → CTA trong 0,65–1 giây. Chỉ chạy một lần, không che nội dung đọc lâu.
- Đường dẫn mảnh và thanh tiến trình theo section giúp nhận biết vị trí trong câu chuyện; chuyển động dựa trên transform/opacity, không khóa cuộn và không tạo parallax mạnh.
- Series phản hồi hover/focus trong 180–300ms; chuyển đổi do người dùng chọn, không tự chạy carousel. Ảnh đổi trạng thái nhẹ, CTA giữ vị trí ổn định.
- Với `prefers-reduced-motion: reduce`, bỏ reveal, dịch chuyển và cuộn mượt; tất cả nội dung ở trạng thái đọc được ngay. Nút/anchor vẫn dùng được bằng bàn phím và chạm.

## Tiêu chí hoàn thành

- Route riêng hoạt động với refresh trực tiếp; trang gốc `/` không đổi.
- CTA và thẻ series chỉ dẫn tới nội dung có thật; trạng thái chưa có bài không giả thành nút.
- Bố cục thích ứng 375/768/1024/1440px, không tràn ngang; ảnh và chữ giữ thứ bậc trên di động.
- Build production thành công. Theo `frontend/AGENTS.md`, không tự chạy unit, integration hay E2E test khi người dùng chưa yêu cầu.
- Tài liệu, code được commit và push vào đúng repo tương ứng sau khi hoàn thành.

## Nguồn tham khảo

- The Forum (https://theforumcenter.com/): học cấu trúc hero, nhịp xen kẽ section và cách dẫn tới CTA.
- `frontend/docs/plans/uiux-design-system.md`: token, chữ và tương tác của VieCultures.
- `frontend/src/data/series/`: registry nội dung và đường dẫn ảnh có thật.
