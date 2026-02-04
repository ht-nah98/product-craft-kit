---
name: System Evolution
description: Meta-Agent for Continuous Improvement - Tiến hóa hệ thống
---

# SKILL: System Evolution
## Meta-Agent for Continuous Improvement

> **Mục đích**: Giám sát, đánh giá và tiến hóa hệ thống Product Building System

---

## Tổng Quan

Skill này tạo ra một **"Meta-Agent"** có khả năng:
1. **Phát hiện gaps** - Templates/Skills chưa handle được case mới
2. **Ghi nhận lessons** - Học từ mỗi project thực tế
3. **Đề xuất improvements** - Tạo skills/templates mới
4. **Tiến hóa hệ thống** - Cập nhật methodology liên tục

---

## Template Location

> **Templates**:
> - [Gap Analysis](../../resources/templates/00_meta_system/_template_gap_analysis.md)
> - [Lessons Learned](../../resources/templates/00_meta_system/_template_lessons_learned.md)
> - [Improvement Proposal](../../resources/templates/00_meta_system/_template_improvement_proposal.md)

---

## Khi Nào Trigger?

### Automatic Triggers (Mỗi prompt)

```
Sau MỖI tương tác với user, tự hỏi:

1. CÓ GAP KHÔNG?
   □ Template hiện tại có cover được use case này?
   □ Có phải "bẻ cong" template để phù hợp?
   □ User có yêu cầu gì mà system không có sẵn?

2. CÓ PATTERN MỚI KHÔNG?
   □ Cách giải quyết này có thể tái sử dụng?
   □ Có best practice nào nên document?
   □ Có anti-pattern nào cần warning?

3. CÓ CẢI TIẾN KHÔNG?
   □ Template có thể làm tốt hơn?
   □ Workflow có thể streamline?
   □ Missing information gì?
```

### Manual Triggers (Khi user yêu cầu)

- "Review system" / "Đánh giá hệ thống"
- "What's missing?" / "Thiếu gì?"
- "Improve this" / "Cải thiện"
- "Lessons learned" / "Bài học rút ra"
- Sau mỗi project kết thúc

---

## Quy Trình Gap Analysis

### Bước 1: Identify Gap

```
GAP TYPE:
□ Missing Template     - Không có template cho use case
□ Incomplete Template  - Template thiếu sections
□ Missing Skill        - Không có skill hướng dẫn
□ Missing Workflow     - Không có workflow cho task
□ Outdated Content     - Nội dung cần cập nhật
□ Structural Gap       - Cấu trúc folder chưa phù hợp
```

### Bước 2: Assess Impact

```
IMPACT ASSESSMENT:
- Frequency: Gap này gặp thường xuyên không?
- Severity: Ảnh hưởng đến quality output thế nào?
- Scope: Ảnh hưởng bao nhiêu use cases?

PRIORITY = Frequency × Severity × Scope
```

### Bước 3: Propose Solution

```
SOLUTION OPTIONS:
□ Create new template/skill
□ Update existing template/skill
□ Add to knowledge base
□ Create new workflow
□ Restructure folders
```

### Bước 4: Implement & Document

Tạo Improvement Proposal → Get approval → Implement → Document in Lessons Learned

---

## Continuous Learning Loop

```
┌─────────────────────────────────────────────────────┐
│                   OBSERVE                            │
│  - User requests                                     │
│  - Pain points encountered                           │
│  - Workarounds used                                  │
└────────────────────────┬────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────┐
│                   ANALYZE                            │
│  - Pattern recognition                               │
│  - Gap identification                                │
│  - Root cause analysis                               │
└────────────────────────┬────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────┐
│                   PROPOSE                            │
│  - Improvement suggestions                           │
│  - New templates/skills                              │
│  - Structural changes                                │
└────────────────────────┬────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────┐
│                   IMPLEMENT                          │
│  - Create/update files                               │
│  - Test with real cases                              │
│  - Document changes                                  │
└────────────────────────┬────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────┐
│                   LEARN                              │
│  - Record lessons learned                            │
│  - Update knowledge base                             │
│  - Feed into next cycle                              │
└─────────────────────────────────────────────────────┘
         │
         └──────────────► Back to OBSERVE
```

---

## System Health Check (Định kỳ)

### Weekly Check
```
□ Review các gaps đã phát sinh trong tuần
□ Có pattern nào lặp lại?
□ Có improvement nào cần prioritize?
```

### Per-Project Review
```
□ Project nào vừa hoàn thành?
□ Lessons learned là gì?
□ Có gì cần thêm vào system?
```

### Quarterly Review
```
□ Overall system effectiveness
□ Major gaps cần address?
□ Methodology cần update?
```

---

## Output Location

```
.agent/resources/
├── system_evolution/
│   ├── gaps/               # Gap analysis records
│   ├── improvements/       # Improvement proposals
│   └── lessons/            # Lessons learned
```

---

## Integration với Daily Work

Khi làm việc với bất kỳ project nào:

1. **Before**: Check có gap/improvement từ trước không
2. **During**: Note lại difficulties, workarounds
3. **After**: Quick reflection - có gì học được?

---

## Checklist: Khi Phát Hiện Gap

```
□ Document gap (dùng Gap Analysis template)
□ Assess priority (High/Medium/Low)
□ Propose solution
□ If High priority → Implement ngay
□ If Medium/Low → Add to improvement backlog
□ Record in Lessons Learned log
```

---

## Next Steps

Sau khi sử dụng skill này:
- Gaps được document tại `.agent/resources/system_evolution/gaps/`
- Improvements được track tại `.agent/resources/system_evolution/improvements/`
- Lessons được aggregate tại `.agent/resources/system_evolution/lessons/`
