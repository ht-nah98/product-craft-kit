---
description: Tạo project mới từ template - Copy cấu trúc chuẩn và khởi tạo thông tin dự án
---

# Workflow: Tạo Project Mới

## Khi nào dùng
Khi PO cần bắt đầu quản lý tài liệu cho một dự án mới.

## Steps

### 1. Hỏi thông tin dự án
Thu thập từ user:
- Tên dự án (sẽ dùng làm folder name, lowercase với dashes)
- Mô tả ngắn gọn
- Đối tượng người dùng chính
- Business goals
- Constraints/limitations (nếu có)

### 2. Tạo folder structure
// turbo
```bash
cp -r /home/user/Desktop/PO-WriteDoc/projects/_project-template /home/user/Desktop/PO-WriteDoc/projects/[project-name]
```

### 3. Cập nhật project-context.md
Điền thông tin vào file:
- `projects/[project-name]/project-context.md`

### 4. Tạo README.md
Cập nhật file:
- `projects/[project-name]/README.md`

### 5. (Optional) Tạo glossary ban đầu
Nếu user cung cấp thuật ngữ, cập nhật:
- `projects/[project-name]/glossary.md`

### 6. Xác nhận với user
Thông báo project đã được tạo và hướng dẫn next steps:
- Bắt đầu viết PRD
- Hoặc thêm User Stories

## Output
- Folder project mới tại `/projects/[project-name]/`
- Files đã được khởi tạo với thông tin cơ bản
