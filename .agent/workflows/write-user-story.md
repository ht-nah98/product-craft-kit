---
description: Viết User Story theo chuẩn PO - Tự động đọc template và skill
---

# Workflow: Viết User Story

## Khi nào dùng
Khi user yêu cầu viết User Story cho một tính năng.

## Steps

### 1. Xác định project
- Nếu user không specify project → Hỏi: "Bạn muốn viết User Story cho dự án nào?"
- Nếu đang trong folder `projects/[name]` → Dùng project đó

### 2. Đọc context
Đọc các file theo thứ tự:
1. `.agent/skills/write_user_story/SKILL.md`
2. `projects/[project]/project-context.md`
3. `projects/[project]/glossary.md`
4. Các User Story liên quan đã có (nếu có)

### 3. Thu thập thông tin từ user
- Tính năng là gì?
- User nào sẽ sử dụng?
- Giá trị mang lại?
- Có liên quan đến US nào khác không?

### 4. Viết User Story
Tuân thủ 100% format trong template (được link trong skill):
- Đúng ID convention: `US-[PREFIX]-[NUMBER]`
- Đủ: As a / I want / So that
- Có Acceptance Criteria
- Có Story Points estimate
- Có Priority

### 5. Lưu file
Lưu vào:
- `projects/[project]/docs/01_product_requirements/[module_name]/[US-ID].md`

### 6. (Optional) Hỏi user có muốn viết thêm
- Viết thêm AC chi tiết?
- Viết DoD?
- Tạo thêm User Story liên quan?

## Output
- File User Story tại đúng vị trí trong project
- Link đến các tài liệu liên quan
