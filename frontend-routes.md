# Frontend Routes – Tài Liệu Chuẩn Hóa Kiến Trúc Định Tuyến

> **Trạng thái:** Đã chuẩn hóa toàn diện (Cleaned & Standardized).
> **Single Source of Truth:** `frontend/src/routes/paths.ts`
> **Kiến trúc:** React Router v6 với Nested Layouts, Route Guards (JWT Role & Auth), và Fallback Redirects.

---

## 1. Bảng Route Canonical (Chính thức)

| # | Route Path | Tên / Chức năng | Component Page | Layout | Bảo vệ (Guard) | Query Params hỗ trợ |
|---|------------|-----------------|----------------|--------|----------------|----------------------|
| 1 | `/` | Trang chủ giới thiệu | `features/landing/pages/landing.tsx` | `PublicLayout` | Public | – |
| 1a | `/landing-concept` | Bản xem trước landing chuyên sâu về ẩm thực Việt, đối chiếu với `/` | `features/landing/pages/FoodLandingPage.tsx` | `PublicLayout` | Public | – |
| 2 | `/login` | Đăng nhập / Đăng ký | `features/auth/pages/login.tsx` | `FocusLayout` | `GuestOnly` (Đã login → `/home`) | `redirect` |
| 3 | `/home` | Phòng học cá nhân (Dashboard) | `features/home/pages/home.tsx` | `FocusLayout` | `RequireAuth` (Bắt buộc login) | – |
| 4 | `/discovery` | Khám phá bài đọc & chủ đề | `features/discovery/pages/discovery.tsx` | `AppLayout` | Public | – |
| 5 | `/reader` | Không gian đọc song ngữ / Extensive | `features/reader/pages/reader.tsx` | `FocusLayout` | Public | `postId`, `level`, `mode` (`bilingual` \| `extensive`) |
| 6 | `/dictionary` | Kho từ vựng & Thư viện thẻ | `features/flashcards/pages/dictionary.tsx` | `AppLayout` | Public | – |
| 7 | `/flashcard-study` | Phòng ôn tập từ vựng SRS | `features/flashcards/pages/flashcard-study.tsx` | `StudyLayout` (Navbar, không Footer) | Public | `deck` (`postId`), `level`, `saved=1` |
| 8 | `/community` | Không gian cảm nhận thành viên | `features/community/pages/community.tsx` | `AppLayout` | Public | – |
| 9 | `/community-contest` | Đấu trường viết luận tuần | `features/community/pages/community-contest.tsx` | `AppLayout` | Public | – |
| 10 | `/playground` | AI Cultural Playground | `features/playground/pages/playground.tsx` | `FocusLayout` | Public | `story`, `topic`, `level` |
| 11 | `/pricing` | Gói hội viên & Bảng giá | `features/subscription/pages/PricingPage.tsx` | `AppLayout` | Public | – |
| 12 | `/pricing/checkout` | Xác nhận thanh toán gói | `features/subscription/pages/CheckoutPage.tsx` | `AppLayout` | `RequireAuth` (Bắt buộc login) | – |
| 13 | `/profile` | Hồ sơ học viên & Hộ chiếu Di sản | `features/profile/pages/ProfilePage.tsx` | `AppLayout` | `RequireAuth` (Bắt buộc login) | `tab` (`passport` \| `badges` \| `vocab` \| `subscription`) |
| 14 | `/admin` | Quản trị CMS | `features/admin/pages/AdminPage.tsx` | `AppLayout` | `RequireRole("ADMIN")` (JWT Claim) | – |
| 15 | `*` | Trang báo lỗi 404 | `pages/NotFoundPage.tsx` | `AppLayout` | Public | – |

---

## 2. Bảng URL Alias & Tương Thích Ngược (Legacy Redirects)

Các URL cũ vẫn được giữ chuyển hướng tự động để không làm gãy bookmark hoặc liên kết cũ:

| URL Cũ / Phụ | URL Đích Canonical | Loại Chuyển Hướng | Ghi chú |
|--------------|-------------------|-------------------|---------|
| `/landing` | `/` | `<Navigate replace />` | Rút gọn về trang gốc |
| `/account` | `/profile` | `<Navigate replace />` | Gom về hồ sơ cá nhân |
| `/passport` | `/profile?tab=passport` | `<Navigate replace />` | Dẫn thẳng tới Hộ chiếu Mộc Son |
| `/achievements` | `/profile?tab=badges` | `<Navigate replace />` | Dẫn thẳng tới Huy hiệu thành tựu |
| `/community-1` | `/community` | `<Navigate replace />` | Bỏ hậu tố `-1` |
| `/community-2` | `/community-contest` | `<Navigate replace />` | Đổi sang tên có ý nghĩa |
| `/checkout` | `/pricing/checkout` | `<Navigate replace />` | Gom về nhóm `/pricing/` |
| `/flashcard-library` | `/dictionary` | `<Navigate replace />` | Gom về kho từ vựng |
| `/flashcards` | `/flashcard-study` | `<Navigate replace />` | Hỗ trợ link rút gọn |
| `/flashcard-study-page`| `/flashcard-study` | `<Navigate replace />` | Hỗ trợ link rút gọn |
| `/bilingual-reader` | `/reader` | Giữ nguyên Query Params | Kèm tham số bài viết |
| `/extensive-reader` | `/reader?mode=extensive` | Giữ nguyên Query Params | Gắn mặc định chế độ extensive |
| `/learning-loop` | `/reader` | Giữ nguyên Query Params | Kèm tham số bài viết |
| `/loop` | `/reader` | Giữ nguyên Query Params | Kèm tham số bài viết |
| `/subscription` | `/pricing` | `<Navigate replace />` | Gom về bảng giá |
| `/upgrade` | `/pricing` | `<Navigate replace />` | Gom về bảng giá |
| `/admin/posts` | `/admin` | `<Navigate replace />` | Gom về trang quản trị |


---

## 3. Kiến Trúc Điều Hướng & Layouts

### 3.1. Phân Tách Layout (`src/layouts/`)
- **`AppLayout`**: Header chung (`Navbar`), `<Outlet />`, `Footer`. Dành cho các trang đọc tin, cộng đồng, bảng giá, từ điển, 404.
- **`PublicLayout`**: `<Outlet />`, `Footer`. Dành riêng cho Landing Page (vì Landing có Header điều hướng riêng).
- **`StudyLayout`**: `Navbar`, `<Outlet />` (không Footer). Dành riêng cho phòng ôn tập Flashcard.
- **`FocusLayout`**: Toàn màn hình chỉ có `<Outlet />` (không Navbar/Footer chung). Dành cho Phòng học (`/home`), Không gian đọc (`/reader`), AI Playground (`/playground`), Đăng nhập (`/login`).

### 3.2. Tiêu Chuẩn Điều Hướng Trong Code
1. **Không dùng chuỗi URL viết cứng (hardcode)**: Luôn nhập và dùng `PATHS` hoặc hàm builder `paths.*()` từ `@/routes/paths`:
   ```tsx
   import { PATHS, paths } from '@/routes/paths';

   // Điều hướng bằng Link:
   <Link to={PATHS.discovery}>Khám Phá</Link>

   // Điều hướng kèm query param:
   navigate(paths.reader({ postId: 'imperial-hue', level: 'Level 2' }));
   ```
2. **Hook điều hướng chuẩn**: Dùng `useAppNavigate()` từ `@/routes/useAppNavigate` thay vì gọi thủ công để tự động cuộn trang mượt mà lên đầu trang.
3. **Link Component**: Dùng `@/components/Link` (hỗ trợ cả `to` và `href`, tự động xử lý cuộn `#anchor` nội bộ và React Router navigate).

---

## 4. Cơ Chế Bảo Vệ Tuyến Đường (Route Guards)

Nằm tại `frontend/src/routes/guards.tsx`:
- **`RequireAuth`**: Kiểm tra phiên đăng nhập từ localStorage (`vie_current_user` hoặc `vie_auth_token`). Nếu chưa đăng nhập, tự động lưu URL hiện tại vào param `?redirect=...` và chuyển đến trang `/login`. Sau khi đăng nhập xong sẽ tự động trả về đúng trang người dùng muốn vào.
- **`RequireRole({ role: "ADMIN" })`**: Tự động giải mã JWT Token (claim `role` hoặc `roles`) không cần phụ thuộc thư viện ngoài. Nếu người dùng không có quyền `ROLE_ADMIN` hoặc `ADMIN`, sẽ tự động chặn và chuyển hướng về `/home`.
- **`GuestOnly`**: Dành riêng cho trang `/login`. Nếu người dùng đã có phiên đăng nhập hợp lệ, sẽ tự động chuyển thẳng vào `/home`.
