---
description: Viết Definition of Done cho User Story, Sprint, hoặc Release
---

# Workflow: Viết Definition of Done

## Khi nào dùng
Khi cần define tiêu chí "hoàn thành" cho một Story, Sprint, hoặc Release.

## Steps

### 1. Xác định cấp độ DoD
Hỏi user:
- **Story DoD** — Khi nào 1 User Story được coi là done?
- **Sprint DoD** — Checklist trước khi close sprint?
- **Release DoD** — Checklist trước khi deploy production?

### 2. Đọc context
Đọc các file:
1. `.agent/skills/write_dod/SKILL.md`
2. `projects/[project]/project-context.md` (để hiểu tech stack và team)
3. File User Story nếu viết Story DoD

### 3. Thu thập thông tin từ user (nếu cần)
- Team dùng tech stack gì? (ảnh hưởng đến test coverage requirements)
- Có CI/CD pipeline không?
- Có staging environment không?
- Test coverage target?

### 4. Viết DoD

**Story DoD** — Thêm vào cuối file User Story:
```markdown
## Definition of Done
- [ ] Code viết và self-tested
- [ ] Code review đã approve
- [ ] Unit tests pass (coverage >= X%)
- [ ] Manual test theo AC hoàn thành
- [ ] PO đã review và accept
- [ ] Documentation cập nhật (nếu cần)
```

**Sprint DoD** — Tạo file mới trong `03_plans/`:
```
projects/[project]/docs/03_plans/dod-sprint-[N].md
```

**Release DoD** — Tạo file mới trong `03_plans/`:
```
projects/[project]/docs/03_plans/dod-release-[version].md
```

### 5. Validate
Kiểm tra mỗi item trong DoD:
- Cụ thể và đo lường được (không mơ hồ)
- Phù hợp với team's capacity
- Không quá nhiều items (Story: 5-8, Sprint: 8-12, Release: 10-15)

## Output
- DoD rõ ràng, đo lường được
- Phù hợp với cấp độ (Story/Sprint/Release)
- Thể hiện tiêu chuẩn chất lượng của team
