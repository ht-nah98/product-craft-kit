# SKILL: Lessons Learned
## Ghi Nhận và Ứng Dụng Bài Học

> **Trigger**: Sau mỗi project, milestone, hoặc khi có insight quan trọng

---

## Mục Đích

Skill này giúp **capture và codify** lessons learned để hệ thống ngày càng thông minh hơn.

---

## Khi Nào Ghi Lesson?

### Automatic Moments
- ✅ Sau khi hoàn thành một Epic/Feature
- ✅ Sau khi project kết thúc (MVP, launch)
- ✅ Sau khi fix một gap quan trọng
- ✅ Khi phát hiện pattern lặp lại

### On-Demand
- User hỏi "lessons learned?"
- Retrospective session
- Knowledge sharing

---

## Lesson Categories

| Category | Description | Questions |
|----------|-------------|-----------|
| **PROCESS** | Về cách làm việc | Workflow nào hiệu quả? |
| **TECHNICAL** | Về kỹ thuật | Tech stack nào phù hợp? |
| **PRODUCT** | Về sản phẩm | User cần gì thực sự? |
| **COMMUNICATION** | Về giao tiếp | Stakeholder cần gì? |
| **METHODOLOGY** | Về phương pháp | Framework nào work? |

---

## Lesson Format

```markdown
## Lesson: [Tên ngắn gọn]

**Category**: PROCESS / TECHNICAL / PRODUCT / COMMUNICATION / METHODOLOGY
**Date**: YYYY-MM-DD
**Project**: [Project name]

### Context
[Bối cảnh khi lesson này được học]

### What Happened
[Sự kiện/quyết định cụ thể]

### Lesson Learned
[Bài học rút ra - viết như một principle]

### Actionable Insights
- [Action 1 có thể apply ngay]
- [Action 2]

### Applied To System?
□ Yes - Updated: [file/skill affected]
□ No - Reason: [why not yet]
```

---

## From Lesson to System Improvement

```
LESSON LEARNED
     │
     ▼
┌─────────────────────────────────┐
│ Is this reusable?               │
│ (Can help future projects?)     │
└──────────────┬──────────────────┘
               │
       ┌───────┴───────┐
       ▼               ▼
      YES              NO
       │               │
       ▼               ▼
  Update system    Document only
       │               │
       ▼               ▼
  - New template   - Add to log
  - Update skill   - Reference later
  - Add workflow
  - Knowledge base
```

---

## Aggregation: Pattern Recognition

Khi có nhiều lessons:

### Weekly Pattern Check
```
□ Có lessons nào similar theme?
□ Có problem nào recurring?
□ Có solution nào proven effective?
```

### Quarterly Synthesis
```
□ Top 3 lessons của quarter?
□ Nên thành principles không?
□ Cần update methodology?
```

---

## Lessons → Knowledge Base

Strong lessons should become:

1. **Best Practices** - Cách làm đã chứng minh hiệu quả
2. **Anti-Patterns** - Cách làm nên tránh
3. **Decision Frameworks** - Hướng dẫn quyết định
4. **Templates** - Formats đã proven

Location: `_master/knowledge/lessons/`

---

## Quick Capture Template

Cho việc ghi nhanh lesson:

```
[DATE] [PROJECT] [CATEGORY]
LESSON: [1 sentence]
ACTION: [What to do differently]
```

Ví dụ:
```
2026-02-03 HRM-System PRODUCT
LESSON: Users cần bulk import hơn manual entry
ACTION: Add bulk operation pattern to Epic template
```

---

## Output Location

Lessons stored at:
`_master/system_evolution/lessons/LESSON-[YYYY-MM-DD]-[name].md`

---

## Integration với Daily Work

### Before starting work
- Check recent lessons cho project type tương tự

### During work
- Quick note bất kỳ insight nào

### After work
- 5-min reflection: Learned gì hôm nay?

---

## Linked Skills

- [SKILL_gap-detection.md](SKILL_gap-detection.md) - Source of lessons
- [SKILL_improvement-proposal.md](SKILL_improvement-proposal.md) - Apply lessons
- [SKILL_system-evolution.md](SKILL_system-evolution.md) - Overview
