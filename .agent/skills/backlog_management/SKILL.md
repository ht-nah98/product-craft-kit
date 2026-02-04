---
name: Backlog Management
description: Skill quản lý Product Backlog
---

# Skill: Quản lý Backlog

> Hướng dẫn tạo, sắp xếp và maintain Product Backlog

---

## Backlog là gì?

**Product Backlog** = Danh sách TẤT CẢ các việc cần làm cho sản phẩm, được sắp xếp theo độ ưu tiên.

---

## Template Backlog File

> **Template File**: [`.agent/resources/templates/04_plans_docs/_template_backlog.md`](../../resources/templates/04_plans_docs/_template_backlog.md)

### Backlog Structure

1. **Summary**: Thống kê nhanh trạng thái backlog
2. **Current Sprint Focus**: Sprint đang chạy
3. **Ready for Sprint**: Items đã refined, sẵn sàng pick
4. **Needs Refinement**: Items mới hoặc chưa rõ ràng
5. **Icebox**: Ý tưởng chưa làm ngay
6. **Epics Tracker**: Tiến độ các Epics


---

## Prioritization Framework

### MoSCoW Method

| Category | Meaning | Guide |
|----------|---------|-------|
| **Must Have** | Critical - phải có trong release | 60% của effort |
| **Should Have** | Important - nên có nhưng không chặn | 20% của effort |
| **Could Have** | Nice to have - làm nếu còn time | 20% của effort |
| **Won't Have** | Out of scope cho release này | Defer |

### RICE Scoring

```
RICE Score = (Reach × Impact × Confidence) / Effort

- Reach: Bao nhiêu user bị ảnh hưởng (1-10)
- Impact: Mức độ ảnh hưởng đến user (0.25/0.5/1/2/3)
- Confidence: Độ tin cậy của estimates (0-100%)
- Effort: Effort cần (person-weeks)
```

---

## Backlog Grooming/Refinement

### Mục tiêu
- Top 2 sprints của backlog luôn ở trạng thái "Ready"
- Mỗi item trong "Ready" phải có đủ:
  - [ ] Clear description
  - [ ] Acceptance Criteria
  - [ ] Story Points estimate
  - [ ] No blockers

### Quy trình
```
1. Review new items → Add to "Needs Refinement"
2. Clarify requirements → Update description
3. Break down if too big → Split into smaller stories
4. Estimate points → Team consensus
5. Prioritize → Move to "Ready for Sprint"
```

---

## Khi thêm item mới

### Từ Bug Reports
```markdown
| ID | Title | Severity | Reported | Status |
|-----|-------|----------|----------|--------|
| BUG-001 | [Description] | Critical | [Date] | [Status] |
```

### Từ Feature Requests
```markdown
1. Log request với context
2. Validate với stakeholder
3. Create User Story
4. Add to Backlog
5. Prioritize in next grooming
```

---

## Checklist quản lý Backlog

- [ ] Backlog được review weekly
- [ ] Top 10 items là highest priority
- [ ] Không có duplicates
- [ ] Old items được archive hoặc remove
- [ ] Dependencies được tracked
- [ ] Stakeholders có visibility
