# Hướng dẫn cho AI viết Tài liệu

> Đây là file hướng dẫn quan trọng nhất cho AI khi làm việc với tài liệu dự án.

---

## 1. Tổng quan Cấu trúc Tài liệu

Một dự án hoàn chỉnh nên có 5 folders tài liệu chính:

```
docs/
├── 1_business_docs/    # Nghiệp vụ: WHAT does the system do?
├── 2_features_docs/    # Tính năng: HOW does it look/behave?
├── 3_technical_docs/   # Kỹ thuật: HOW is it built?
├── 4_plans_docs/       # Kế hoạch: HOW to build it step-by-step?
└── 5_testing_docs/     # Kiểm thử: HOW to verify it works?
```

**Số thứ tự (1_, 2_, ...)**: Đảm bảo thứ tự hiển thị logic khi browse folders.

---

## 2. Thứ tự Đọc và Viết Tài liệu

### Khi ĐỌC (để hiểu dự án)
```
1_business_docs/overview.md → 3_technical_docs/architecture.md → 2_features_docs/ → 4_plans_docs/
```

### Khi VIẾT (để tạo tài liệu mới)
```
1. Business docs (nghiệp vụ trước)
2. Features docs (thiết kế UI/UX)
3. Technical docs (kiến trúc kỹ thuật)
4. Plans docs (kế hoạch triển khai)
5. Testing docs (chiến lược test)
```

---

## 3. Nguyên tắc Viết Tài liệu

### 3.1. Cấu trúc File Chuẩn

Mỗi file markdown nên có:

```markdown
# Tiêu đề chính

> Mô tả ngắn 1-2 dòng

---

## Section 1
Nội dung...

---

## Section 2
Nội dung...

---

## Tài liệu liên quan
- [Link 1](./path/to/doc1.md)
- [Link 2](./path/to/doc2.md)
```

### 3.2. README.md bắt buộc

Mỗi folder PHẢI có `README.md` bao gồm:
- Tổng quan folder
- Cấu trúc thư mục (tree view)
- Quy tắc tổ chức
- Hướng dẫn đọc/viết
- Links đến tài liệu liên quan

### 3.3. DRY - Don't Repeat Yourself

| Tình huống | Cách xử lý |
|------------|-----------|
| Nội dung xuất hiện nhiều nơi | Tách thành file riêng trong `shared/` |
| Tham chiếu nội dung khác | Dùng link: `[Xem chi tiết](./path/to/file.md)` |
| Mô tả component dùng chung | Đặt trong folder `shared/components/` |

### 3.4. Cross-References

Luôn link giữa các tài liệu liên quan:
```markdown
## Tài liệu liên quan

- [Tài liệu nghiệp vụ](../1_business_docs/)
- [Tài liệu tính năng](../2_features_docs/)
- [Tài liệu kỹ thuật](../3_technical_docs/)
- [Kế hoạch triển khai](../4_plans_docs/)
```

---

## 4. Chi tiết từng Pillar

### 4.1. Business Docs (Nghiệp vụ)

**Mục đích**: Mô tả HỆ THỐNG LÀM GÌ từ góc nhìn nghiệp vụ.

**Files chính**:
| File | Nội dung |
|------|----------|
| `overview.md` | Tổng quan hệ thống, mục tiêu, đối tượng người dùng, modules |
| `glossary.md` | Thuật ngữ và viết tắt |
| `[module_name]/` | Folder cho từng module nghiệp vụ |

**Nội dung cần có**:
- Mục tiêu dự án
- Đối tượng người dùng (vai trò)
- Quy trình nghiệp vụ (workflows)
- Kiến trúc module từ góc nhìn nghiệp vụ
- Thuật ngữ

### 4.2. Features Docs (Tính năng/UI)

**Mục đích**: Mô tả GIAO DIỆN VÀ HÀNH VI của hệ thống.

**Files chính**:
| File | Nội dung |
|------|----------|
| `_template-screen.md` | Template chuẩn cho mô tả màn hình |
| `shared/layouts/` | Bố cục dùng chung (header, sidebar, footer) |
| `shared/components/` | UI components dùng chung |
| `shared/patterns/` | Patterns thiết kế (validation, pagination, ...) |
| `[module_name]/` | Màn hình của từng module |

**Nội dung cần có**:
- Wireframe (text-based hoặc diagram)
- User flow (navigation)
- Danh sách tính năng với ID
- Mô tả chi tiết từng tính năng
- Validation rules
- Business logic

### 4.3. Technical Docs (Kỹ thuật)

**Mục đích**: Mô tả CÁCH HỆ THỐNG ĐƯỢC XÂY DỰNG.

**Files chính**:
| File | Nội dung |
|------|----------|
| `architecture.md` | Kiến trúc tổng quan, stack công nghệ |
| `shared/` | Tài liệu kỹ thuật dùng chung |
| `[module_name]/` | Tài liệu kỹ thuật theo module |

**Nội dung cần có**:
- Stack công nghệ
- Kiến trúc hệ thống (diagrams)
- Database schema
- API specifications
- Authentication/Authorization
- Patterns và practices

### 4.4. Plans Docs (Kế hoạch)

**Mục đích**: Mô tả CÁCH TRIỂN KHAI từng bước.

**Files chính**:
| File | Nội dung |
|------|----------|
| `README.md` | Tổng quan tiến độ tất cả phases |
| `[module_name]/phase-X.md` | Kế hoạch phase |
| `[module_name]/phase-X/sub-X.md` | Chi tiết sub-phase |

**Nội dung cần có**:
- Bảng tiến độ (với trạng thái ✅/⬜/🔄)
- Chia thành phases
- Mỗi phase chia thành sub-phases
- Checklist tasks trong mỗi sub-phase
- Links đến tài liệu tham chiếu
- Thứ tự triển khai (dependencies)

**Quy tắc quan trọng**:
- Triển khai theo chiều DỌC (feature by feature, không horizontal layers)
- Cập nhật trạng thái sau mỗi task hoàn thành
- Không viết code chi tiết, chỉ ghi chú ngắn gọn

### 4.5. Testing Docs (Kiểm thử)

**Mục đích**: Mô tả CHIẾN LƯỢC VÀ CÁCH KIỂM THỬ.

**Files chính**:
| File | Nội dung |
|------|----------|
| `overview.md` | Chiến lược test tổng quan |
| `architecture.md` | Kiến trúc và cấu trúc thư mục test |
| `unit_tests.md` | Hướng dẫn viết unit tests |
| `integration_tests.md` | Hướng dẫn viết integration tests |
| `edge_cases.md` | Các edge cases quan trọng |
| `conventions.md` | Quy tắc đặt tên và conventions |

**Nội dung cần có**:
- Test pyramid (tỷ lệ unit/integration/e2e)
- Coverage targets
- Critical paths cần test
- Edge cases theo domain
- CI/CD integration

---

## 5. Sử dụng Tables và Diagrams

### Tables
Dùng cho: danh sách có cấu trúc, so sánh, thông số

```markdown
| Thuộc tính | Giá trị |
|------------|---------|
| Key 1 | Value 1 |
| Key 2 | Value 2 |
```

### Mermaid Diagrams
Dùng cho: flows, ERD, architecture

```mermaid
flowchart LR
    A[Start] --> B[Process] --> C[End]
```

### Text-based Diagrams (ASCII Art)
Dùng cho: wireframes, layouts, simple diagrams

```
┌─────────────────────────────────────┐
│  Header                             │
├─────────────────────────────────────┤
│  Content                            │
└─────────────────────────────────────┘
```

---

## 6. Checklist trước khi hoàn thành Tài liệu

- [ ] Mỗi folder có README.md
- [ ] Sử dụng đúng template
- [ ] Không có nội dung trùng lặp (DRY)
- [ ] Có cross-references đến tài liệu liên quan
- [ ] Cấu trúc thư mục được cập nhật trong README
- [ ] Thuật ngữ được định nghĩa trong glossary
- [ ] Diagrams rõ ràng và có ý nghĩa

