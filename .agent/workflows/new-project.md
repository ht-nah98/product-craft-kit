---
description: Tạo project mới từ template - Copy cấu trúc chuẩn và khởi tạo thông tin dự án
---

# Workflow: Tạo Project Mới

## Khi nào dùng
Khi cần bắt đầu quản lý tài liệu cho một dự án mới.

## Steps

### 1. Hỏi thông tin dự án
Thu thập từ user:
- Tên dự án (sẽ dùng làm folder name, lowercase với dashes)
- Mô tả ngắn gọn
- Đối tượng người dùng chính
- Business goals
- Tech stack (nếu biết)
- Constraints/limitations (nếu có)

### 2. Tạo folder structure
Copy từ template:
```bash
cp -r projects/_project-template projects/[project-name]
```

### 3. Cập nhật CLAUDE.md trong project
Điền thông tin vào:
- `projects/[project-name]/CLAUDE.md`

Section cần update:
- Project Overview (tên và mô tả)
- Tech stack

### 4. Cập nhật project-context.md
Điền thông tin vào:
- `projects/[project-name]/project-context.md`

Sections cần điền:
- Project name và description
- Problem Statement
- Business Goals
- Success Metrics
- Stakeholders
- Primary Users
- Product Scope (In/Out)
- Tech Stack
- Timeline

### 5. (Optional) Khởi tạo glossary
Nếu user cung cấp thuật ngữ domain, cập nhật:
- `projects/[project-name]/glossary.md`

### 6. Xác nhận và hướng dẫn next steps
Thông báo project đã được tạo, suggest next steps:
- Viết PRD → dùng `/write-prd`
- Bắt đầu Discovery → dùng `/discovery`
- Viết Epic đầu tiên → dùng `/write-epic`

## Output
- Folder project mới tại `projects/[project-name]/`
- `CLAUDE.md` đã được cập nhật
- `project-context.md` đã được điền thông tin cơ bản
