---
name: Write Acceptance Criteria
description: Skill viết Acceptance Criteria theo chuẩn Gherkin/BDD
---

# Skill: Viết Acceptance Criteria (AC)

> Tuân thủ 100% template và quy tắc này khi viết Acceptance Criteria

---

## Trước khi viết

1. **Đọc User Story liên quan** để hiểu context
2. **Đọc project context**: `projects/[project]/project-context.md`
3. **Xem AC mẫu** trong các tài liệu đã có

---

## Format AC chuẩn (Gherkin Style)

### Cấu trúc

```markdown
## AC[N]: [Tên mô tả ngắn gọn]

**Given** [điều kiện/context ban đầu]
**When** [hành động user thực hiện]
**Then** [kết quả mong đợi]
**And** [kết quả bổ sung - optional]
```

### Giải thích

| Keyword | Mục đích | Ví dụ |
|---------|----------|-------|
| **Given** | Thiết lập điều kiện ban đầu | Given tôi đã đăng nhập vào hệ thống |
| **When** | Mô tả hành động trigger | When tôi click vào button "Tạo mới" |
| **Then** | Kết quả mong đợi | Then popup tạo mới hiển thị |
| **And** | Kết quả/điều kiện bổ sung | And button "Lưu" ở trạng thái enabled |

---

## Quy tắc viết AC

### 1. SMART Criteria
- **S**pecific: Cụ thể, không mơ hồ
- **M**easurable: Có thể đo lường/verify
- **A**chievable: Khả thi để implement
- **R**elevant: Liên quan đến User Story
- **T**estable: Có thể viết test case

### 2. Độc lập và Atomic
- Mỗi AC test MỘT behavior duy nhất
- Không phụ thuộc vào AC khác trong cùng story
- Có thể pass/fail độc lập

### 3. Cover các scenarios
Mỗi User Story nên có AC cover:
- ✅ **Happy path**: Luồng thành công chính
- ❌ **Error cases**: Các lỗi có thể xảy ra
- 🔄 **Edge cases**: Trường hợp biên
- 🚫 **Validation**: Rules validate input

---

## Các loại AC thường gặp

### 1. Functional AC
```markdown
## AC1: Tạo đơn hàng thành công
**Given** tôi đã thêm sản phẩm vào giỏ hàng
**When** tôi click "Đặt hàng" và xác nhận thông tin
**Then** đơn hàng được tạo với trạng thái "Chờ xác nhận"
**And** email xác nhận được gửi đến tôi
```

### 2. Validation AC
```markdown
## AC2: Validate số điện thoại
**Given** tôi đang điền form thông tin
**When** tôi nhập số điện thoại ít hơn 10 số
**Then** hiển thị lỗi "Số điện thoại phải có ít nhất 10 chữ số"
**And** không thể submit form
```

### 3. UI/Display AC
```markdown
## AC3: Hiển thị trạng thái đơn hàng
**Given** tôi có đơn hàng đang xử lý
**When** tôi vào trang "Đơn hàng của tôi"
**Then** đơn hàng hiển thị với badge "Đang xử lý" màu vàng
```

### 4. Permission AC
```markdown
## AC4: Chỉ Admin được xóa user
**Given** tôi đăng nhập với role "Staff"
**When** tôi vào trang quản lý user
**Then** button "Xóa" không hiển thị
```

### 5. Performance AC (nếu cần)
```markdown
## AC5: Response time tìm kiếm
**Given** database có 100,000 sản phẩm
**When** tôi tìm kiếm với keyword
**Then** kết quả hiển thị trong vòng 2 giây
```

---

## Template đầy đủ cho 1 Feature

```markdown
# Acceptance Criteria: [Tên Feature]

> Linked User Story: [US-XXX](link-to-us)

---

## Happy Path

### AC1: [Scenario thành công chính]
**Given** ...
**When** ...
**Then** ...

---

## Error Handling

### AC2: [Lỗi khi ...]
**Given** ...
**When** ...
**Then** hiển thị lỗi "..."

### AC3: [Lỗi khi ...]
**Given** ...
**When** ...
**Then** ...

---

## Validation Rules

### AC4: [Validate field X]
**Given** ...
**When** user nhập giá trị không hợp lệ
**Then** ...

---

## Edge Cases

### AC5: [Edge case]
**Given** data ở trạng thái đặc biệt
**When** ...
**Then** ...

---

## Permissions (nếu có)

### AC6: [Role X không được phép ...]
**Given** user có role X
**When** ...
**Then** không thể thực hiện action
```

---

## Checklist trước khi hoàn thành

- [ ] Mỗi AC đúng format Given/When/Then
- [ ] Cover happy path
- [ ] Cover các error cases quan trọng
- [ ] Cover validation rules
- [ ] Mỗi AC có thể test độc lập
- [ ] Ngôn ngữ rõ ràng, không ambiguous
- [ ] Link đến User Story liên quan
