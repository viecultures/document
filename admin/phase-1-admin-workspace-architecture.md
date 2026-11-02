# VieCultures Admin Workspace Architecture Specification
## Phase 1.1: Core Shell, Layout Isolation & Metric Contracts

---

### 1. Architectural Motivation & Layout Isolation

#### 1.1 The Problem with Shared Layouts
Prior to Phase 1.1, the VieCultures Admin CMS (`/admin`, `/admin/*`) was mounted inside `AppLayout`, sharing the student-facing header (`Navbar`) and consumer footer (`Footer`). This posed significant operational drawbacks:
- Distracting consumer navigation elements (audio companion drawer, consumer streaks, passport shortcuts) cluttering administrative workflows.
- Excessive vertical scroll caused by consumer marketing footers on administrative data tables.
- Inconsistent spacing and z-index collisions between CMS dialogs/drawers and consumer floating widgets.

#### 1.2 Independent Admin Shell (`AdminLayout`)
Phase 1.1 introduces a completely decoupled shell hierarchy:
- **Zero Student Chrome**: `AdminLayout` explicitly excludes consumer `Navbar`, `Footer`, and `CompanionFloatingButton`.
- **High-Density Canvas**: The layout features a 56px fixed topbar (`AdminTopbar`), a 256px persistent or collapsible navigation sidebar (`AdminSidebar`), and a fluid flex main content area (`<Outlet />`).
- **Route Guarding**: All `/admin/*` child routes are guarded by `RequireRole role="ADMIN"`. Unauthorized users or guests are automatically redirected to localized login with preserving original return URLs.

```
+-------------------------------------------------------------------------------+
| AdminTopbar (Height: 56px, Sticky Top, z-30)                                  |
| [Breadcrumb: Admin > Phân hệ]   [Quick Search]   [Xem trang Học viên] [vi/en] [Admin] |
+-----------------------+-------------------------------------------------------+
| AdminSidebar (256px)  | Main Canvas (<Outlet />)                              |
|                       | +---------------------------------------------------+ |
| 1. Tổng quan          | | Compact Page Header (Height <= 68px)              | |
| 2. Hành trình học     | | [Title & Subtitle]          [Primary Action Group]| |
| 3. Kho Bài viết       | +---------------------------------------------------+ |
| 4. Marketing          | |                                                   | |
| 5. Học viên CRM       | | High-Density Tab Content / Data Grid / Forms      | |
| 6. Hệ thống           | |                                                   | |
+-----------------------+-------------------------------------------------------+
```

---

### 2. Header and Navigation Specifications

#### 2.1 AdminTopbar Specification
- **Height**: 56px (`h-14`), sticky top at `z-30`.
- **Color Palette & Styling**: Warm Heritage styling (`#FAF6EE` Ivory surface, `#1D4A43` Forest Green border accents, `#D9A05B` Antique Gold badges).
- **Sub-components**:
  1. **Breadcrumb Trail**: Dynamically computed from active route parameter (`Trang quản trị / <Tên phân hệ>`).
  2. **Quick Search Input**: Fast keyword filter for posts, users, or journeys with keyboard shortcut hint (`/`).
  3. **"Xem trang Học viên" (Switch to Learner View)**: Instant toggle button directing administrators to `/discovery` or `/home` in a new tab or direct navigation.
  4. **Language Switcher**: Seamless language toggle between Vietnamese (`vi`) and English (`en`) via `i18n.changeLanguage()`.
  5. **Admin Identity Badge**: Avatar initials, administrator name, and `ROLE_ADMIN` pill fetched from `auth-storage.ts`.

#### 2.2 AdminSidebar Specification (6 Core Sub-systems)
The sidebar organizes the back-office operations into 6 discrete functional modules:

| Sub-system | Tab Key | Route | Lucide Icon | Core Responsibility |
| :--- | :--- | :--- | :--- | :--- |
| **1. Tổng quan & Tăng trưởng** | `dashboard` / `system_stats` | `/admin/dashboard` | `LayoutDashboard` | Metric KPI cards, CEFR distribution, regional coverage, system health. |
| **2. Hành trình học** | `journeys` | `/admin/journeys` | `Map` | Management of cultural journeys, stage ordering, milestones, and provincial stops. |
| **3. Kho Bài viết & Học liệu** | `posts` | `/admin/posts` | `BookOpen` | Editorial authoring, paragraph pairing, CEFR level tagging, vocabulary extraction. |
| **4. Marketing & Đa kênh** | `marketing` | `/admin/marketing` | `Megaphone` | Campaign banners, referral tracking, social push hooks, newsletter broadcasts. |
| **5. Học viên CRM** | `users` | `/admin/users` | `Users` | User roster, role assignment (`ROLE_USER`, `ROLE_ADMIN`), status toggles. |
| **6. Hệ thống & Kiểm duyệt** | `system` / `logs` | `/admin/system` | `ShieldCheck` | Audit trail logging, backend service connection statuses, performance telemetry. |

*Iconography Policy*: Exclusively use Lucide React SVG components. Strictly avoid Unicode emojis or informal icons in administrative code, UI labels, and logs.

#### 2.3 Compact Page Header Specification
- **Height Constraint**: Maximum 68px height (`h-[68px]` or `min-h-[56px] max-h-[68px]`).
- **Layout**: Flex row layout with space-between alignment:
  - Left: Title (font-heading, font-bold, text-lg/xl) and contextual badge or count tag.
  - Right: Horizontal button group containing contextual actions (e.g., "Tạo bài viết", "Thêm lộ trình", "Tải lại", "Xuất báo cáo").
- **Design Impact**: Replaces outdated 150px-high visual banners to ensure data tables and metric widgets render within the above-the-fold viewport.

---

### 3. Backend API Contract: Overview & Growth Metrics

#### 3.1 Endpoint Definition
- **Route**: `GET /api/v1/admin/overview`
- **Controller**: `AdminOverviewController`
- **Security**: Authenticated JWT with role `ROLE_ADMIN` (`@PreAuthorize("hasRole('ADMIN')")`).

#### 3.2 Response Payload Specification
Envelope format follows `ApiResponse<AdminOverviewStatsDto>`:

```json
{
  "success": true,
  "data": {
    "totalUsers": 1280,
    "activeLearnersWeek": 342,
    "totalPosts": 85,
    "publishedPosts": 85,
    "totalReads": 24910,
    "avgReadsPerPost": 293.1,
    "cefrCoverage": {
      "A1": 15,
      "A2": 24,
      "B1": 28,
      "B2": 12,
      "C1": 4,
      "C2": 2
    },
    "regionCoverage": {
      "Bắc Bộ": 32,
      "Trung Bộ": 26,
      "Nam Bộ": 22,
      "Tây Nguyên": 5
    },
    "systemStatus": "HEALTHY"
  },
  "message": null,
  "errorCode": null,
  "timestamp": "2026-11-02T08:00:00"
}
```

#### 3.3 Field Definition Matrix

| Field | Type | Description |
| :--- | :--- | :--- |
| `totalUsers` | `long` | Total count of registered accounts in the system. |
| `activeLearnersWeek` | `long` | Distinct users recording study activity within the last 7 days (`UserActivityLog`). |
| `totalPosts` | `long` | Total number of cultural reading articles created. |
| `publishedPosts` | `long` | Total published articles accessible to learners. |
| `totalReads` | `long` | Aggregated reading completion counters across all articles. |
| `avgReadsPerPost` | `double` | Precise floating-point average (`totalReads / totalPosts`), avoiding integer truncation. |
| `cefrCoverage` | `Map<String, Long>` | Breakdown count of articles distributed across CEFR levels (A1 through C2). |
| `regionCoverage` | `Map<String, Long>` | Breakdown count of articles across geographical regions. |
| `systemStatus` | `String` | Operational status of core services (`HEALTHY`, `DEGRADED`). |

---

### 4. Implementation Checklist for Phase 1.1

- [x] Technical Architecture Documentation (`docs/admin/phase-1-admin-workspace-architecture.md`)
- [x] Backend DTO `AdminOverviewStatsDto.java`
- [x] Backend Service Interface `AdminOverviewService.java`
- [x] Backend Service Implementation `AdminOverviewServiceImpl.java`
- [x] Backend Controller `AdminOverviewController.java` (`/api/v1/admin/overview`)
- [x] Frontend Layout `AdminLayout.tsx` (Excludes student Navbar/Footer)
- [x] Frontend Header `AdminTopbar.tsx` (56px, Breadcrumbs, Language Switcher, Learner Link)
- [x] Frontend Navigation `AdminSidebar.tsx` (6 Core Sub-systems, Lucide icons)
- [x] Frontend Router decoupling in `App.tsx` with `RequireRole role="ADMIN"`
- [x] Frontend `AdminPage.tsx` migration to Compact Page Header (<= 68px) and 6-tab support
- [x] System architecture reference update in `structure.md`
