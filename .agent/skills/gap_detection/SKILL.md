---
name: Gap Detection
description: Skill phát hiện và ghi nhận gaps trong hệ thống
---

# SKILL: Gap Detection
## Phát Hiện và Ghi Nhận Gaps trong Hệ Thống

> **Trigger**: Mỗi khi gặp case mà system không handle tốt

---

## Mục Đích

Skill này giúp **AI Assistant** tự động phát hiện và document các gaps trong hệ thống để cải tiến liên tục.

---

## Auto-Check Questions (Mỗi Prompt)

Sau mỗi tương tác, AI cần tự hỏi:

### 1. Template Fitness Check
```
□ Template hiện tại có đủ trường cho use case?
□ Có phải skip/modify sections nào?
□ User có hỏi điều gì không có trong template?
□ Output có đúng format mong đợi?
```

### 2. Skill Coverage Check
```
□ Skill có hướng dẫn đủ chi tiết?
□ Có edge case nào không được đề cập?
□ Có bước nào cần thêm giải thích?
□ Decision tree có cover hết cases?
```

### 3. Workflow Efficiency Check
```
□ Workflow có smooth không?
□ Có bước nào redundant?
□ Có bước nào missing?
□ User có phải switch context nhiều?
```

---

## Gap Categories

| Category | Description | Example |
|----------|-------------|---------|
| **MISSING** | Hoàn toàn không có | Không có template cho Technical Spec |
| **INCOMPLETE** | Có nhưng thiếu phần | Epic template thiếu dependency section |
| **OUTDATED** | Có nhưng không còn phù hợp | Workflow dùng tool cũ |
| **UNCLEAR** | Có nhưng khó hiểu | Instructions mơ hồ |
| **INFLEXIBLE** | Không adapts được | Template quá rigid |

---

## Quick Gap Report Format

Khi phát hiện gap, note nhanh:

```markdown
## Gap: [Tên ngắn gọn]
- **Type**: MISSING / INCOMPLETE / OUTDATED / UNCLEAR / INFLEXIBLE
- **Location**: [File/Folder affected]
- **Context**: [Khi nào gặp gap này]
- **Impact**: HIGH / MEDIUM / LOW
- **Suggested Fix**: [1-2 sentences]
```

---

## Gap Severity Matrix

| Frequency ↓ / Impact → | Low | Medium | High |
|------------------------|-----|--------|------|
| **Rare** | Backlog | Backlog | Schedule |
| **Occasional** | Backlog | Schedule | Urgent |
| **Frequent** | Schedule | Urgent | Critical |

**Actions:**
- **Backlog**: Log và review quarterly
- **Schedule**: Plan trong sprint tiếp theo
- **Urgent**: Address trong tuần này
- **Critical**: Fix ngay lập tức

---

## Integration Points

### Khi viết tài liệu
- Note nếu template thiếu section
- Note nếu cần thêm example

### Khi build product
- Note nếu methodology không cover case
- Note nếu workflow bị bottleneck

### Khi build AI agent
- Note nếu pattern không fit
- Note nếu architecture chưa có guide

---

## Output

Gaps được log tại:
`.agent/resources/system_evolution/gaps/GAP-[YYYY-MM-DD]-[short-name].md`

---

## Linked Skills

- [system_evolution](../system_evolution/SKILL.md) - Overview
- [improvement_proposal](../improvement_proposal/SKILL.md) - Sau khi có gap
