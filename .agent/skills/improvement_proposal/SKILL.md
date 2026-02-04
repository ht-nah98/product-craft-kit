---
name: Improvement Proposal
description: Skill đề xuất và thực hiện cải tiến hệ thống
---

# SKILL: Improvement Proposal
## Đề Xuất và Thực Hiện Cải Tiến Hệ Thống

> **Trigger**: Sau khi có Gap Analysis hoặc Lessons Learned

---

## Mục Đích

Skill này hướng dẫn cách **đề xuất và implement** cải tiến cho hệ thống một cách có hệ thống.

---

## Improvement Types

| Type | Description | Example |
|------|-------------|---------|
| **NEW** | Tạo mới hoàn toàn | New template cho API spec |
| **ENHANCE** | Cải tiến existing | Thêm section vào Epic template |
| **REFACTOR** | Tổ chức lại | Restructure skill folders |
| **DEPRECATE** | Loại bỏ obsolete | Remove unused template |
| **DOCUMENT** | Thêm docs | Add examples, clarify instructions |

---

## Proposal Process

### Step 1: Define Improvement

```
IMPROVEMENT: [Tên]
TYPE: NEW / ENHANCE / REFACTOR / DEPRECATE / DOCUMENT

PROBLEM:
[Gap/issue mà improvement này giải quyết]

SOLUTION:
[Mô tả cách giải quyết]

AFFECTED FILES:
- [ ] [File 1]
- [ ] [File 2]
```

### Step 2: Impact Assessment

```
BENEFITS:
- [Benefit 1]
- [Benefit 2]

RISKS:
- [Risk 1] → Mitigation: [...]

EFFORT:
□ Small (< 1 hour)
□ Medium (1-4 hours)
□ Large (> 4 hours)

PRIORITY:
□ Critical (blocks work)
□ High (significantly improves)
□ Medium (nice to have)
□ Low (future consideration)
```

### Step 3: Get Approval

```
For SMALL + HIGH priority: Self-approve, inform user
For others: Ask user for approval
```

### Step 4: Implement

```
1. Create/modify files
2. Update references (SKILL.md, GEMINI.md)
3. Test with example
4. Commit with clear message
```

### Step 5: Document

```
1. Add to Lessons Learned
2. Update knowledge base if needed
3. Communicate change to user
```

---

## Quick Implementation Checklist

```
□ Improvement clearly defined
□ Impact assessed
□ Approval obtained (if needed)
□ Files created/modified
□ Router updated (if new skill/template)
□ GEMINI.md updated (if major change)
□ Tested with example
□ Committed to git
□ User informed
□ Lessons learned updated
```

---

## Templates to Create/Update

Khi tạo NEW template:
```
1. Follow naming: _template_[name].md
2. Include YAML frontmatter
3. Add to appropriate folder (01-07)
4. Reference in related skill
5. Add to router if needed
```

Khi tạo NEW skill:
```
1. Follow naming: SKILL_[name].md
2. Include template reference
3. Add to appropriate folder (0-3)
4. Update SKILL.md router
5. Create workflow if user-facing
```

---

## Self-Improvement Heuristics

### Khi nào tự quyết định?
- Small changes với clear benefit
- Fixing obvious bugs/typos
- Adding missing examples
- Clarifying ambiguous instructions

### Khi nào hỏi user?
- Major structural changes
- New methodology concepts
- Changes affecting multiple files
- Removing existing content

---

## Output Location

Improvement proposals stored at:
`.agent/resources/system_evolution/improvements/IMP-[YYYY-MM-DD]-[name].md`

---

## Linked Skills

- [SKILL_gap-detection.md](SKILL_gap-detection.md) - Trước đó
- [SKILL_lessons-learned.md](SKILL_lessons-learned.md) - Sau đó
