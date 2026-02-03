---
name: Write User Story
description: Skill viết User Story theo chuẩn PO
---

# Skill: Viết User Story

> Tuân thủ 100% template và quy tắc này khi viết User Story

---

## Trước khi viết

1. **Đọc Epic cha**: `projects/[project]/docs/2_features_docs/epics/EPIC-XXX.md`
2. **Đọc project context**: `projects/[project]/project-context.md`
3. **Đọc glossary**: `projects/[project]/glossary.md`
4. **Xem các User Story liên quan** đã có

---

## Template User Story

### 1. Template Location
> **Template File**: [`_master/templates/02_features_docs/_template_user_story.md`](../../templates/02_features_docs/_template_user_story.md)

### 2. Cấu trúc User Story

1. **Information**: ID, Epic, Priority, Points
2. **Statement**: As a / I want / So that (INVEST)
3. **Context**: Pre-conditions, Business Rules
4. **Acceptance Criteria**: Given / When / Then (Happy path + Edge cases)
5. **UI/UX**: Design references
6. **Definition of Done**: Checklist hoàn thành


---

## Quy tắc viết

### 1. INVEST Criteria
| Criteria | Mô tả | Check |
|----------|-------|-------|
| **I**ndependent | Story độc lập, có thể develop riêng | ☐ |
| **N**egotiable | Có thể thương lượng chi tiết | ☐ |
| **V**aluable | Mang lại giá trị cho user | ☐ |
| **E**stimable | Có thể estimate effort | ☐ |
| **S**mall | Đủ nhỏ để hoàn thành trong 1 sprint | ☐ |
| **T**estable | Có thể test được với AC | ☐ |

### 2. Naming Convention
```
US-[PREFIX]-[NUMBER]: Tên ngắn gọn

Ví dụ:
- US-ORG-001: Tạo đơn vị tổ chức
- US-EMP-002: Xem thông tin hồ sơ nhân sự
- US-ATT-003: Check-in bằng mobile app
```

### 3. Story Points (Fibonacci)
| Points | Complexity | Time estimate |
|--------|------------|---------------|
| 1 | Trivial | < 2 hours |
| 2 | Simple | 2-4 hours |
| 3 | Medium | 1 day |
| 5 | Complex | 2-3 days |
| 8 | Very complex | 1 week |
| 13 | Epic-level | Cần chia nhỏ |

### 4. Acceptance Criteria Guidelines
- Mỗi AC phải **độc lập** và **testable**
- Cover: Happy path, Validation, Edge cases
- Format: **Given/When/Then**
- Số lượng AC: 3-7 per story (nếu > 7 → chia story)

### 5. Priority (MoSCoW)
| Priority | Meaning | Guide |
|----------|---------|-------|
| 🔴 Must Have | Critical - phải có | MVP |
| 🟠 Should Have | Important - nên có | High value |
| 🟡 Could Have | Nice to have | If time permits |

---

## Lưu file

```
projects/[project]/docs/2_features_docs/user-stories/US-[PREFIX]-[NUMBER].md
```

---

## Checklist trước khi hoàn thành

- [ ] Thuộc 1 Epic (có link)
- [ ] User Story Statement đầy đủ (As a / I want / So that)
- [ ] Có Bối cảnh
- [ ] AC đúng format Given/When/Then
- [ ] AC cover happy path + validation + edge cases
- [ ] Có Story Points và Priority
- [ ] Dependencies identified
- [ ] Definition of Done cụ thể
