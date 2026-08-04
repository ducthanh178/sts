# BÁO CÁO DỰ ÁN

## Hệ thống Quản lý Điểm Rèn luyện Sinh viên  
### Student Training Score (STS)

---

| Mục | Nội dung |
|-----|----------|
| **Tên dự án** | Hệ thống Quản lý Điểm Rèn luyện Sinh viên (STS) |
| **Mã dự án** | STS |
| **Phiên bản tài liệu** | 1.0 |
| **Ngày lập** | 04/08/2026 |
| **Trạng thái** | Bản nháp |

---

## Mục lục

1. [Tóm tắt](#1-tóm-tắt)
2. [Giới thiệu](#2-giới-thiệu)
3. [Phân tích yêu cầu](#3-phân-tích-yêu-cầu)
4. [Thiết kế hệ thống](#4-thiết-kế-hệ-thống)
5. [Mô hình dữ liệu](#5-mô-hình-dữ-liệu)
6. [Chức năng chính](#6-chức-năng-chính)
7. [Công nghệ đề xuất](#7-công-nghệ-đề-xuất)
8. [Kế hoạch triển khai](#8-kế-hoạch-triển-khai)
9. [Rủi ro và biện pháp](#9-rủi-ro-và-biện-pháp)
10. [Kết luận và hướng phát triển](#10-kết-luận-và-hướng-phát-triển)
11. [Phụ lục](#11-phụ-lục)

---

## 1. Tóm tắt

Dự án **STS (Student Training Score)** xây dựng hệ thống quản lý **điểm rèn luyện sinh viên**, hỗ trợ nhà trường theo dõi, đánh giá và tổng hợp kết quả rèn luyện theo học kỳ/năm học một cách minh bạch, thống nhất và dễ kiểm soát.

Hệ thống hướng tới các mục tiêu:

- Số hóa quy trình đánh giá điểm rèn luyện.
- Giảm thao tác thủ công, sai sót và trùng lặp dữ liệu.
- Tăng tính minh bạch giữa sinh viên, cố vấn học tập và phòng công tác sinh viên.
- Cung cấp báo cáo, thống kê phục vụ quản lý đào tạo.

---

## 2. Giới thiệu

### 2.1. Bối cảnh

Điểm rèn luyện là chỉ số quan trọng phản ánh ý thức, thái độ và kết quả tham gia hoạt động của sinh viên trong quá trình học tập tại trường. Quy trình đánh giá thường gồm nhiều bước: tự đánh giá của sinh viên, xác nhận của lớp/cố vấn, và phê duyệt của khoa/phòng CTSV.

Hiện nay, nhiều đơn vị vẫn thực hiện bằng Excel hoặc form giấy, dẫn đến:

- Khó đối chiếu và truy vết lịch sử chỉnh sửa.
- Tốn thời gian tổng hợp theo lớp, khoa, toàn trường.
- Thiếu kênh phản hồi rõ ràng khi sinh viên khiếu nại điểm.

### 2.2. Mục tiêu dự án

| STT | Mục tiêu | Mô tả |
|-----|----------|-------|
| 1 | Quản lý tập trung | Lưu trữ điểm rèn luyện theo học kỳ, năm học, lớp, khoa |
| 2 | Phân quyền rõ ràng | Sinh viên, cố vấn, cán bộ khoa, admin có vai trò riêng |
| 3 | Quy trình chuẩn hóa | Tự đánh giá → xác nhận → phê duyệt |
| 4 | Báo cáo & thống kê | Xuất báo cáo theo lớp/khoa/toàn trường |
| 5 | Minh bạch | Sinh viên xem được điểm và lý do điều chỉnh |

### 2.3. Phạm vi

**Trong phạm vi (MVP):**

- Đăng nhập / phân quyền người dùng.
- Quản lý danh mục: khoa, lớp, năm học, học kỳ, tiêu chí đánh giá.
- Sinh viên tự chấm / gửi phiếu đánh giá.
- Cố vấn xác nhận / điều chỉnh điểm.
- Khoa / CTSV phê duyệt.
- Xem lịch sử và xuất báo cáo cơ bản (CSV/Excel/PDF).

**Ngoài phạm vi (giai đoạn sau):**

- Tích hợp SSO trường / LMS.
- App mobile chuyên biệt.
- AI gợi ý điểm / phát hiện bất thường nâng cao.

---

## 3. Phân tích yêu cầu

### 3.1. Đối tượng sử dụng (Actors)

| Vai trò | Mô tả | Nhu cầu chính |
|---------|-------|---------------|
| Sinh viên | Người được đánh giá | Tự đánh giá, xem điểm, khiếu nại |
| Cố vấn học tập / GVCN | Quản lý lớp | Xác nhận, điều chỉnh, nhận xét |
| Cán bộ khoa | Quản lý cấp khoa | Phê duyệt, thống kê theo khoa |
| Phòng CTSV / Admin | Quản trị hệ thống | Cấu hình tiêu chí, phê duyệt cuối, báo cáo toàn trường |
| Lãnh đạo | Người ra quyết định | Xem dashboard, xuất báo cáo tổng hợp |

### 3.2. Yêu cầu chức năng

1. **Xác thực & phân quyền:** đăng nhập, phân role, giới hạn thao tác theo quyền.
2. **Quản lý danh mục:** khoa, ngành, lớp, sinh viên, năm học, học kỳ.
3. **Cấu hình khung điểm rèn luyện:** nhóm tiêu chí, điểm tối đa, quy tắc cộng/trừ.
4. **Phiếu tự đánh giá:** sinh viên nhập điểm theo tiêu chí, đính kèm minh chứng (nếu có).
5. **Quy trình phê duyệt nhiều cấp:** cố vấn → khoa → CTSV.
6. **Điều chỉnh điểm có lý do:** ghi nhận người sửa, thời gian, nội dung thay đổi.
7. **Thống kê & báo cáo:** theo lớp, khoa, xếp loại (Xuất sắc / Tốt / Khá / Trung bình / Yếu).
8. **Thông báo:** nhắc hạn nộp, kết quả phê duyệt, yêu cầu bổ sung minh chứng.

### 3.3. Yêu cầu phi chức năng

| Nhóm | Yêu cầu |
|------|---------|
| Hiệu năng | Truy vấn danh sách lớp ~200 SV dưới 2 giây |
| Bảo mật | Mã hóa mật khẩu, phân quyền chặt, ghi audit log |
| Khả dụng | Giao diện tiếng Việt, responsive trên desktop/mobile |
| Độ tin cậy | Sao lưu định kỳ, khôi phục dữ liệu khi sự cố |
| Khả mở rộng | Dễ thêm tiêu chí / cấp phê duyệt mới |

---

## 4. Thiết kế hệ thống

### 4.1. Kiến trúc tổng quan

```
┌─────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Web Client │────▶│   API Backend    │────▶│    Database     │
│  (Browser)  │◀────│  (REST / Auth)   │◀────│  (PostgreSQL)   │
└─────────────┘     └──────────────────┘     └─────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  File Storage    │
                    │  (minh chứng)    │
                    └──────────────────┘
```

### 4.2. Luồng nghiệp vụ chính

```
Sinh viên tự đánh giá
        │
        ▼
Cố vấn xác nhận / điều chỉnh
        │
        ▼
Khoa phê duyệt
        │
        ▼
CTSV / Admin chốt điểm
        │
        ▼
Công bố kết quả + xuất báo cáo
```

### 4.3. Phân quyền thao tác (tóm tắt)

| Chức năng | SV | Cố vấn | Khoa | Admin |
|-----------|----|--------|------|-------|
| Tự đánh giá | ✓ | | | |
| Xác nhận lớp | | ✓ | | |
| Phê duyệt khoa | | | ✓ | |
| Cấu hình tiêu chí | | | | ✓ |
| Xuất báo cáo toàn trường | | | ✓ | ✓ |

---

## 5. Mô hình dữ liệu

### 5.1. Các thực thể chính

| Thực thể | Mô tả |
|----------|-------|
| `User` | Tài khoản người dùng (role, trạng thái) |
| `Student` | Hồ sơ sinh viên (MSSV, lớp, khoa) |
| `Faculty` / `Class` | Khoa, lớp học |
| `AcademicTerm` | Năm học / học kỳ |
| `CriteriaGroup` / `Criterion` | Nhóm tiêu chí và tiêu chí chấm điểm |
| `EvaluationSheet` | Phiếu đánh giá của 1 SV trong 1 học kỳ |
| `EvaluationItem` | Điểm từng tiêu chí trong phiếu |
| `ApprovalStep` | Các bước phê duyệt / trạng thái |
| `Evidence` | File minh chứng đính kèm |
| `AuditLog` | Lịch sử thay đổi |

### 5.2. Trạng thái phiếu đánh giá

| Trạng thái | Ý nghĩa |
|------------|---------|
| `DRAFT` | Sinh viên đang soạn |
| `SUBMITTED` | Đã gửi, chờ cố vấn |
| `ADVISOR_REVIEWED` | Cố vấn đã xử lý |
| `FACULTY_APPROVED` | Khoa đã duyệt |
| `FINALIZED` | CTSV chốt điểm |
| `REJECTED` | Trả lại để chỉnh sửa |

### 5.3. Xếp loại điểm rèn luyện (tham chiếu phổ biến)

| Khoảng điểm | Xếp loại |
|-------------|----------|
| 90 – 100 | Xuất sắc |
| 80 – < 90 | Tốt |
| 65 – < 80 | Khá |
| 50 – < 65 | Trung bình |
| < 50 | Yếu |

> *Lưu ý: khung điểm/xếp loại cần cấu hình theo quy chế thực tế của từng trường.*

---

## 6. Chức năng chính

### 6.1. Module quản trị

- Quản lý người dùng, gán vai trò.
- Import danh sách sinh viên (CSV/Excel).
- Cấu hình năm học, học kỳ, khung tiêu chí.
- Mở / khóa đợt đánh giá.

### 6.2. Module sinh viên

- Xem khung tiêu chí và hướng dẫn chấm.
- Điền phiếu tự đánh giá, upload minh chứng.
- Theo dõi trạng thái phê duyệt.
- Xem điểm cuối và lịch sử điều chỉnh.

### 6.3. Module cố vấn / khoa / CTSV

- Duyệt danh sách phiếu theo lớp/khoa.
- Điều chỉnh điểm kèm lý do.
- Phê duyệt hàng loạt.
- Thống kê tỷ lệ xếp loại, sinh viên chưa nộp.

### 6.4. Module báo cáo

- Báo cáo theo lớp / khoa / toàn trường.
- Danh sách xếp loại Xuất sắc → Yếu.
- Xuất file Excel / PDF phục vụ lưu trữ và họp xét.

---

## 7. Công nghệ đề xuất

| Lớp | Đề xuất | Lý do |
|-----|---------|-------|
| Frontend | React / Next.js | UI hiện đại, dễ bảo trì |
| Backend | NestJS hoặc Spring Boot | API rõ ràng, phân quyền tốt |
| Database | PostgreSQL | Đáng tin cậy, hỗ trợ quan hệ phức tạp |
| Auth | JWT + refresh token (hoặc SSO sau) | Bảo mật, mở rộng được |
| File | Object storage (S3-compatible) | Lưu minh chứng |
| Deploy | Docker + CI/CD | Triển khai ổn định |

---

## 8. Kế hoạch triển khai

| Giai đoạn | Nội dung chính | Kết quả bàn giao |
|-----------|----------------|------------------|
| **Giai đoạn 1** | Khảo sát quy chế, chốt yêu cầu MVP | Tài liệu SRS |
| **Giai đoạn 2** | Thiết kế DB, API, UI wireframe | Bản thiết kế kỹ thuật |
| **Giai đoạn 3** | Phát triển core: auth, danh mục, phiếu đánh giá | Bản demo nội bộ |
| **Giai đoạn 4** | Phê duyệt nhiều cấp, báo cáo, audit log | Bản UAT |
| **Giai đoạn 5** | Kiểm thử, sửa lỗi, triển khai production | Hệ thống chính thức |
| **Giai đoạn 6** | Vận hành, thu thập phản hồi, tối ưu | Báo cáo nghiệm thu |

---

## 9. Rủi ro và biện pháp

| Rủi ro | Mức độ | Biện pháp |
|--------|--------|-----------|
| Quy chế điểm thay đổi theo năm | Cao | Thiết kế tiêu chí cấu hình được, không hard-code |
| Dữ liệu import sai từ Excel | Trung bình | Validate chặt, cho phép rollback theo đợt |
| Quá tải vào cuối đợt đánh giá | Trung bình | Cache danh mục, tối ưu truy vấn, giới hạn upload |
| Tranh chấp điểm / khiếu nại | Cao | Lưu audit log đầy đủ, bắt buộc nhập lý do chỉnh sửa |
| Người dùng chưa quen quy trình số | Trung bình | Hướng dẫn trong app, video ngắn, hỗ trợ theo lớp |

---

## 10. Kết luận và hướng phát triển

Dự án **STS** hướng tới số hóa toàn bộ vòng đời đánh giá điểm rèn luyện sinh viên: từ tự đánh giá, xác nhận nhiều cấp, đến báo cáo và lưu trữ lịch sử. Khi hoàn thành MVP, hệ thống sẽ giúp nhà trường giảm công sức vận hành, tăng minh bạch và tạo nền tảng dữ liệu cho công tác sinh viên.

**Hướng phát triển tiếp theo:**

1. Tích hợp hệ thống thông tin sinh viên / SSO của trường.
2. Thông báo real-time (email / Zalo OA / app).
3. Dashboard phân tích xu hướng rèn luyện theo khóa, ngành.
4. Module khiếu nại – phúc khảo online.
5. Ứng dụng di động cho sinh viên và cố vấn.

---

## 11. Phụ lục

### A. Thuật ngữ

| Thuật ngữ | Giải thích |
|-----------|------------|
| Điểm rèn luyện | Điểm đánh giá ý thức, thái độ, hoạt động của sinh viên |
| Phiếu đánh giá | Bản ghi điểm theo tiêu chí của 1 SV trong 1 học kỳ |
| Cố vấn học tập | Giảng viên phụ trách lớp, xác nhận điểm cấp lớp |
| CTSV | Phòng Công tác Sinh viên |
| MVP | Minimum Viable Product – phiên bản tối thiểu có thể dùng |

### B. Cấu trúc thư mục đề xuất (khi bắt đầu code)

```
sts/
├── docs/                 # Tài liệu, báo cáo
├── apps/
│   ├── web/              # Frontend
│   └── api/              # Backend
├── packages/             # Shared libs (nếu monorepo)
└── README.md
```

### C. Lịch sử tài liệu

| Phiên bản | Ngày | Người lập | Nội dung |
|-----------|------|-----------|----------|
| 1.0 | 04/08/2026 | — | Khởi tạo báo cáo dự án STS |

---

*Tài liệu này là bản nháp khung báo cáo dự án. Có thể bổ sung thêm: quy chế điểm cụ thể của trường, sơ đồ ER chi tiết, mockup UI, và kết quả kiểm thử khi hệ thống được phát triển.*
