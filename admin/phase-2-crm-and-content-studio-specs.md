# Phase 2.1: Chuan hoa Bang Hoc vien CRM, Bang Bai viet voi Readiness Pills, Guardrails va API Xuat du lieu

## 1. Tong quan va Muc tieu
Tai lieu nay quy dinh kien truc ky thuat, dac ta du lieu va quy tac giao dien cho Phase 2.1 thuoc he thong Quan tri VieCultures:
- Chuan hoa i18n song ngu (vi / en) cho bang Quan ly Hoc vien CRM va bang Bai viet.
- Khac phuc triet de loi tran ngang bang du lieu tren man hinh hep thong qua co che Sticky Column ben phai cho cot Thao tac (Actions).
- Bo sung he thong phan nhom marketing va chuc nang xuat du lieu nguoi dung ra tep tin CSV ho tro day du ky tu Unicode tieng Viet thong qua byte UTF-8 BOM.
- Nang cap bang Quan ly Bai viet bang bo chi so San sang (Readiness Pills) su dung 100% SVG Vector tu thu vien Lucide.
- Thiet lap quy tac Guardrail ngan chan xuat ban bai viet khi chua co noi dung doan van song ngu.

---

## 2. Kien truc Bang Hoc vien CRM

### 2.1. Khac phuc tran ngang (Table Overflow & Sticky Action Column)
- Container bao quanh bang du lieu su dung class `overflow-x-auto` ket hop voi do rong co dinh toi thieu cho cac cot thong tin (`min-w-[768px]`).
- Cot Thao tac (Actions) duoc dinh vi co dinh o bien phai voi class `sticky right-0 z-10`.
- De tranh hien tuong chu va noi dung cac cot khac bi xuyen thau khi nguoi dung cuon ngang, cot Thao tac bat buoc phai co background dong bo theo mau nen the cha:
  + Che do Sang (Light mode): `bg-rice-paper` hoac `bg-warm-ivory/95` kem lop do bong mem `shadow-[-4px_0_6px_-2px_rgba(0,0,0,0.05)]`.
  + Che do Toi (Dark mode): `dark:bg-heritage-dark/95` kem hover phu hop (`dark:group-hover:bg-slate-800`).

### 2.2. He thong Bo loc Phan nhom Marketing (Marketing Segment Filters)
Ho tro 5 nhom phan khuc marketing chinh xac thong qua tham so `filterGroup`:
1. `all` (Tat ca): Hien thi toan bo danh sach nguoi dung dang ky.
2. `recent_7d` (Moi dang ky 7 ngay): Nguoi dung co thoi diem tao tai khoan trong vong 7 ngay gan nhat (`createdAt >= now - 7 days`).
3. `inactive` (Chua hoc bai nao / Khong hoat dong): Nguoi dung co so tu vung da luu bang 0 hoac tai khoan bi disabled.
4. `active` (Tich cuc): Nguoi dung da luu tu vung (`savedVocabCount > 0`) hoac dang duoc kich hoat (`enabled == true`).
5. `admin` (Quan tri vien): Nguoi dung co vai tro he thong chua 'ADMIN' (`role` co chuoi 'ADMIN').

### 2.3. Tinh nang Xuat CSV (Export CSV)
- Cho phep quan tri vien tai ve tep CSV gom toan bo danh sach hoc vien theo bo loc tim kiem hien tai.
- Tieu de cot CSV (Header):
  `ID, Họ và tên, Email, Vai trò, Trình độ CEFR, Từ đã lưu, Phương thức đăng nhập, Ngày tạo, Trạng thái`
- Ma hoa UTF-8 kem BOM (`\uFEFF`) o dau tep de dam bao phan mem Microsoft Excel tren Windows doc va hien thi chinh xac tieng Viet co dau ma khong can thao tac chuyen doi ma thu cong.
- Co che phuc hoi: Ho tro tai tep truc tiep qua API backend, kem co che fallback xuat client-side neu he thong chay o che do Local Auth Mode.

---

## 3. Kien truc Bang Bai viet & Content Studio

### 3.1. Readiness Pills (Bo chi so do hoan thien hoc lieu)
Thay the hien thi doan van don dieu bang 4 chi bao nho gon su dung 100% Lucide SVG (tuyet doi khong su dung emoji):
1. **Bai doc (Reading)**:
   - Icon: `FileText`
   - Dieu kien: Xanh luc (`text-emerald-700 bg-emerald-100`) neu `paragraphs.length > 0` hoac `wordCount > 0`; Do (`text-rose-700 bg-rose-100`) neu chua co doan van nao.
   - Hien thi: So doan van song ngu hoac so tu.
2. **Tu vung (Vocabulary)**:
   - Icon: `Type`
   - Dieu kien: Xanh lam (`text-blue-700 bg-blue-100`) neu `vocabularies.length > 0`; Xam nhat neu chua co tu nao.
   - Hien thi: So luong tu vung chuyen sau kem nghia.
3. **Audio TTS (Audio track)**:
   - Icon: `Volume2`
   - Dieu kien: Vang kim/Xanh (`text-amber-800 bg-amber-100`) neu co `audioTracks` hoac `shadowingAudioUrl`; Xam neu chua tao audio.
   - Hien thi: Trang thai am thanh luyen doc.
4. **Quiz trac nghiem (Quiz questions)**:
   - Icon: `HelpCircle`
   - Dieu kien: Tim/Cham (`text-purple-700 bg-purple-100`) neu `questions.length > 0`; Xam neu chua co cau hoi doc hieu.
   - Hien thi: So luong cau hoi trac nghiem van hoa.

### 3.2. Quy tac Guardrail Xuat ban (Publish Guardrail)
- **Quy tac bat buoc**: Neu mot bai viet chua co bat ky doan van song ngu nao (`!post.paragraphs || post.paragraphs.length === 0`), he thong phai:
  + Khoa nut 'Xuat ban' (disabled state).
  + Giam opacity xuong 50% va ap dung cursor `not-allowed`.
  + Hien thi chu thich (tooltip / aria-label): "Bai viet phai co it nhat mot doan van song ngu truoc khi xuat ban".
- Ap dung dong bo tai:
  + Cot thao tac cua bang danh sach Bai viet tren `AdminPage`.
  + Form chinh sua bai viet `PostFormModal`.

### 3.3. Bo loc Trang thai Bai viet (Post Status Filter)
Ho tro 4 che do loc danh sach bai viet:
- `all`: Tat ca bai viet trong he thong.
- `published`: Cac bai viet da hoan thien noi dung doan van (`paragraphs.length > 0`).
- `draft`: Cac bai viet dang soan thao hoac chua co doan van (`!paragraphs || paragraphs.length === 0`).
- `missing_materials`: Cac bai viet thieu mot trong cac thanh phan hoc lieu bo tro (thieu Audio TTS hoac thieu Tu vung hoac thieu Quiz).

---

## 4. API Contracts

### 4.1. GET /api/v1/admin/users
- **Phuong thuc**: `GET`
- **Quyen truy cap**: `@PreAuthorize("hasRole('ADMIN')")`
- **Tham so truy van (Query Parameters)**:
  + `query` (string, tuy chon): Tu khoa tim kiem theo ten hoac email.
  + `role` (string, tuy chon): Vai tro nguoi dung (`ROLE_USER`, `ROLE_ADMIN`).
  + `enabled` (boolean, tuy chon): Trang thai kich hoat (`true`, `false`).
  + `filterGroup` (string, tuy chon): Nhom tiep thi (`all`, `recent_7d`, `inactive`, `active`, `admin`).
  + `page` (int, mac dinh: 0): So trang.
  + `size` (int, mac dinh: 10): So ban ghi tren moi trang.
- **Phan hoi (Response)**:
  + `ApiResponse<Page<AdminUserSummaryDto>>`

### 4.2. GET /api/v1/admin/users/export
- **Phuong thuc**: `GET`
- **Quyen truy cap**: `@PreAuthorize("hasRole('ADMIN')")`
- **Tham so truy van (Query Parameters)**:
  + `query` (string, tuy chon)
  + `role` (string, tuy chon)
  + `enabled` (boolean, tuy chon)
  + `filterGroup` (string, tuy chon)
- **Phan hoi (Response)**:
  + Status: `200 OK`
  + Headers:
    * `Content-Disposition: attachment; filename="viecultures_users.csv"`
    * `Content-Type: text/csv; charset=UTF-8`
  + Body: Chuoi bytes CSV dinh dang UTF-8 bat dau bang byte BOM `\uFEFF`.
