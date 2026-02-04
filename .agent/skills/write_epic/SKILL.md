---
name: Write Epic Specification
description: Skill viết Epic Spec cho nhóm tính năng lớn
---

# Skill: Viết Epic Specification

> Tuân thủ 100% template này khi viết Epic Spec

---

## Trước khi viết

1. **Đọc project context**: `projects/[project]/project-context.md`
2. **Đọc glossary**: `projects/[project]/glossary.md`
3. **Xem các Epic đã có** trong `projects/[project]/docs/2_features_docs/[module_name]/`

---

## Epic là gì?

```
Module (Nhóm tính năng lớn - VD: Quản lý Nhân sự Gốc)
└── Epic (Tính năng lớn - VD: Quản lý Cơ cấu Tổ chức)
    └── User Story (Chức năng đơn lẻ - VD: Tạo đơn vị tổ chức)
```

**Epic** = Một tính năng lớn cần nhiều sprint để hoàn thành, bao gồm nhiều User Stories liên quan.

---

## Template Epic Specification

### 1. Template Location
> **Template File**: [`.agent/resources/templates/02_features_docs/_template_epic.md`](../../resources/templates/02_features_docs/_template_epic.md)

### 2. Cấu trúc Epic

1. **Information**: ID, Module, Status, Figma Link
2. **Overview**: Context, Pain Points, Goals, Business Value
3. **Scope**: In-scope / Out-of-scope (Quan trọng)
4. **Target Users**: Roles & Permissions
5. **User Stories List**: List các story con
6. **Dependencies**: Blocking & Blocked by
7. **Definition of Done**: Criteria hoàn thành Epic
8. **Risks**: Quản lý rủi ro


---

## Quy tắc viết Epic

### 1. Naming Convention
```
EPIC-[PREFIX]-[NUMBER]: Tên Epic

Ví dụ:
- EPIC-ORG-001: Quản lý Cơ cấu Tổ chức
- EPIC-EMP-001: Quản lý Hồ sơ Nhân viên
- EPIC-ATT-001: Hệ thống Chấm công
```

### 2. Size Guideline
- 1 Epic = 2-4 Sprints để complete
- Mỗi Epic nên có 5-15 User Stories
- Nếu lớn hơn → chia thành nhiều Epic

### 3. Sections bắt buộc
- Overview (Bối cảnh, Mục tiêu, Business Value)
- Scope (In-scope, Out-of-scope)
- Target Users (với quyền)
- User Stories (linked)
- Dependencies
- Definition of Done

### 4. Liên kết
- Link đến tất cả User Stories trong Epic
- Link đến Project Context và Glossary
- Link đến Figma/Design nếu có

---

## Lưu file

```
projects/[project]/docs/2_features_docs/[module_name]/EPIC-[PREFIX]-[NUMBER].md
```

> [!CAUTION]
> Luôn đặt trong folder của module tương ứng. KHÔNG để file trực tiếp trong `2_features_docs/`.

---

## Checklist trước khi hoàn thành

- [ ] Bối cảnh và Pain Points rõ ràng
- [ ] Business Value có metric đo được
- [ ] Scope In/Out rõ ràng
- [ ] Target Users có quyền cụ thể
- [ ] User Stories đã breakdown và linked
- [ ] Dependencies identified
- [ ] Definition of Done defined
- [ ] Risks assessed
