---
description: Viết Epic Specification cho một nhóm tính năng lớn
---

# Workflow: Viết Epic

## Khi nào dùng
Khi cần define một tính năng lớn (2-4 sprints) bao gồm nhiều User Stories.

## Steps

### 1. Xác định project và module
- Xác định project đang làm việc
- Hỏi user: Epic này thuộc module nào?

### 2. Đọc context
Đọc các file:
1. `.agent/skills/write_epic/SKILL.md`
2. `projects/[project]/project-context.md`
3. `projects/[project]/glossary.md`
4. PRD liên quan (nếu có)
5. Các Epic đã có trong cùng module (để tránh trùng lặp)

### 3. Thu thập thông tin từ user
- Tên Epic và module cha
- Context và pain points hiện tại
- Mục tiêu của Epic
- Business value (metric đo được)
- Scope: In-scope và out-of-scope
- Target users và roles/permissions
- Dependencies với Epic khác (nếu có)

### 4. Xác định ID
Theo convention:
```
EPIC-[PREFIX]-[NUMBER]
Ví dụ: EPIC-ORG-001, EPIC-EMP-002
```

### 5. Viết Epic
Tuân thủ 100% template:
1. Thông tin chung (ID, module, status, priority)
2. Tổng quan (bối cảnh, mục tiêu, business value, metrics)
3. Phạm vi (in-scope / out-of-scope)
4. Đối tượng sử dụng
5. User Stories list (có thể draft trước, link sau)
6. Dependencies
7. Definition of Done
8. Risks

### 6. Lưu file
```
projects/[project]/docs/01_product_requirements/[module_name]/EPIC-[PREFIX]-[N].md
```

### 7. Suggest next steps
- Break down User Stories → dùng `/write-user-story`
- Viết Tech Spec nếu phức tạp → dùng `/write-tech-spec`
- Estimate và thêm vào backlog

## Output
- File Epic hoàn chỉnh trong đúng module folder
- Linked đến PRD và sẵn sàng để breakdown thành User Stories
