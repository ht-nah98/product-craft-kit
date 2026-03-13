---
name: Write Technical Specification
description: Skill viết Technical Specification (Tech Spec / TP) cho một feature hoặc Epic
---

# Skill: Viết Technical Specification

> Tuân thủ 100% template và quy tắc này khi viết Tech Spec

---

## Trước khi viết

1. **Đọc Epic cha**: `projects/[project]/docs/01_product_requirements/[module]/EPIC-XXX.md`
2. **Đọc User Stories liên quan** để hiểu full scope
3. **Đọc project context**: `projects/[project]/project-context.md`
4. **Đọc architecture hiện tại** (nếu có): `projects/[project]/docs/02_technical_specs/architecture.md`
5. **Đọc database schema** (nếu có): `projects/[project]/docs/02_technical_specs/database-schema.md`

---

## Khi nào cần viết Tech Spec?

Viết TP khi Epic/Feature có ít nhất 1 trong các yếu tố sau:

| Yếu tố | Ví dụ |
|--------|-------|
| Complex business logic | Tính toán lương, phân quyền động |
| New database tables | Thêm bảng mới hoặc thay đổi schema lớn |
| New/modified API endpoints | CRUD mới, webhook, external API |
| External integrations | Payment gateway, email service, 3rd party |
| Performance requirements | Caching, pagination, real-time |
| Security concerns | Auth, encryption, RBAC |

> **Rule**: Nếu Epic nhỏ và toàn CRUD đơn giản → không cần TP riêng.

---

## Template Location

> **Template File**: [`.agent/resources/templates/02_technical_specs/_template_tech_spec.md`](../../resources/templates/02_technical_specs/_template_tech_spec.md)

---

## Cấu trúc Tech Spec chuẩn

1. **Overview** — Mô tả kỹ thuật tổng quan (làm gì ở backend/system level?)
2. **API Specifications** — Endpoints, request/response, logic flow
3. **Database Design** — Tables affected, relationships, key queries
4. **Implementation Details** — Classes/files, algorithms, dependencies
5. **Security & Performance** — Auth, caching, encryption
6. **Mapping to User Stories** — Trace từng API/feature về US tương ứng

---

## Naming Convention

```
TP-[PREFIX]-[NUMBER]: Tên Tech Spec

Ví dụ:
- TP-ORG-001: Quản lý Cơ cấu Tổ chức
- TP-PAY-001: Payroll Calculation Engine
- TP-AUTH-001: JWT Authentication & RBAC
```

---

## Quy tắc viết Tech Spec

### 1. Audience: Developer, not PO
- Viết chi tiết kỹ thuật — tên class, method, table, column
- Code snippet, JSON example khi cần
- Không cần giải thích business context (đã có trong Epic)

### 2. Logic Flow là quan trọng nhất
- Mỗi API phải có Logic Flow step-by-step
- Dùng numbered list: `1. Validate → 2. Check → 3. Save → 4. Notify`
- Bao gồm error paths

### 3. Link Two Ways
- TP link đến Epic/US (parent)
- Epic/US link đến TP (child)

### 4. Keep in Sync
- Update TP khi implementation thay đổi so với spec
- Note `[IMPLEMENTED]` hoặc `[CHANGED]` nếu có deviation

---

## Lưu file

```
projects/[project]/docs/02_technical_specs/[module_name]/TP-[PREFIX]-[N].md
```

---

## Checklist trước khi hoàn thành

- [ ] Overview rõ ràng (1 đoạn mô tả kỹ thuật)
- [ ] Tất cả APIs có: endpoint, request, response, logic flow
- [ ] Database changes documented
- [ ] Error cases và HTTP status codes defined
- [ ] Security & auth requirements specified
- [ ] Mapped về User Stories tương ứng
- [ ] Tech lead/developer đã review
