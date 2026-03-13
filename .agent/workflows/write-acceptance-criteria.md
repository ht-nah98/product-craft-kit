---
description: Viết Acceptance Criteria theo chuẩn Gherkin/BDD cho User Story
---

# Workflow: Viết Acceptance Criteria

## Khi nào dùng
Khi cần viết hoặc bổ sung Acceptance Criteria cho một User Story.

## Steps

### 1. Xác định User Story
- Hỏi user: AC cho User Story nào? (US ID)
- Đọc file User Story đó

### 2. Đọc context
Đọc các file:
1. `.agent/skills/write_acceptance_criteria/SKILL.md`
2. File User Story liên quan: `projects/[project]/docs/01_product_requirements/[module]/US-XXX.md`
3. `projects/[project]/glossary.md` (để dùng đúng terminology)

### 3. Phân tích User Story
Xác định các scenarios cần cover:
- Happy path (luồng thành công chính)
- Error cases (các lỗi có thể xảy ra)
- Edge cases (trường hợp biên)
- Validation rules (validate input)
- Permission scenarios (nếu có role-based logic)

### 4. Viết AC
Format chuẩn Gherkin:
```
## AC[N]: [Tên mô tả ngắn gọn]
**Given** [điều kiện ban đầu]
**When** [hành động]
**Then** [kết quả mong đợi]
**And** [kết quả bổ sung - nếu cần]
```

Đảm bảo cover đủ:
- [ ] Happy path
- [ ] Error handling
- [ ] Validation rules
- [ ] Edge cases
- [ ] Permissions (nếu có)

### 5. Lưu
Tùy theo scope:
- **Nhỏ (3-7 AC)**: Thêm trực tiếp vào file User Story
- **Lớn (>7 AC)**: Tạo file riêng:
  ```
  projects/[project]/docs/01_product_requirements/[module]/AC-[US-ID].md
  ```
  Sau đó link từ User Story vào file AC

### 6. Validate
Kiểm tra từng AC:
- Mỗi AC test đúng 1 behavior
- Ngôn ngữ rõ ràng, không mơ hồ
- Có thể test độc lập (pass/fail)
- Không quá 7 AC per story (nếu > 7 → cân nhắc chia story)

## Output
- AC hoàn chỉnh theo Gherkin format
- Đã cover đủ: happy path + errors + validation + edge cases
