# SKILL: Problem Definition
## Product Building Phase 2 - Focus on the Right Problem

> **Reference Methodology**: [Product Building Methodology](../../knowledge/product-building-methodology.md)

---

## Mục Đích

Skill này hướng dẫn thực hiện Phase 2 "DEFINE" - giai đoạn chọn và định nghĩa rõ ràng vấn đề cần giải quyết.

### Goals của Phase này:
- ✓ Chọn một problem cụ thể để solve
- ✓ Define problem statement rõ ràng
- ✓ Xác định success metrics
- ✓ Set "appetite" - bao nhiêu effort sẵn sàng bỏ ra

**OUTPUT**: Clear problem statement + success criteria

---

## Template Location

> **Template File**: [_master/templates/06_product_building/_template_problem_canvas.md](../../templates/06_product_building/_template_problem_canvas.md)

---

## Quy Trình Thực Hiện

### Bước 1: Prioritize Problems

Từ Discovery phase, có nhiều problems. Score mỗi problem:

| Criteria | Scale | Weight |
|----------|-------|--------|
| User Impact | 1 (Nice to have) → 5 (Critical pain) | 35% |
| Business Impact | 1 (Low value) → 5 (High strategic) | 30% |
| Feasibility | 1 (Very hard) → 5 (Relatively easy) | 35% |

**Score = User Impact × Business Impact × Feasibility**

Chọn problem có score cao nhất VÀ team excited about.

### Bước 2: Write Problem Statement

**Format chuẩn:**
```
[WHO - target user]
needs a way to [DO WHAT - job to be done]
because [WHY - insight from research]

Currently, they [CURRENT BEHAVIOR]
which causes [PAIN/COST]
```

**Ví dụ:**
> "Operations analysts need a way to query business data because they lack SQL skills but need quick answers. Currently, they submit tickets to data team which takes 2-3 days, causing delayed decisions and frustration."

### Bước 3: Generate "How Might We" Questions

Reframe problem thành opportunity:
- HMW giúp analysts tự query data?
- HMW giảm thời gian từ 3 ngày xuống minutes?
- HMW eliminate bottleneck với data team?

### Bước 4: Define Success Metrics

**Primary Metric** (1 metric that matters most):
- Metric: ___
- Baseline: ___
- Target: ___
- How to measure: ___

**Secondary Metrics**:
- User metrics (satisfaction, time saved)
- Business metrics (cost, efficiency)
- Quality metrics (accuracy, errors)

**Guardrail Metrics** (things not to break):
- __ must stay above __
- __ must stay below __

### Bước 5: Set Appetite (Shape Up style)

| Batch Size | Duration | Team | Use When |
|------------|----------|------|----------|
| Small | 1-2 weeks | 1-2 people | Quick improvements |
| Medium | 3-4 weeks | 2-3 people | New features |
| Big | 5-6 weeks | 3-5 people | Major initiatives |

**Key principle**: TIME is FIXED, SCOPE is VARIABLE
- Không extend time, cut scope thay vì.

---

## Completion Checklist

```
□ Problems prioritized with clear rationale
□ Single problem selected to focus on
□ Problem statement written (WHO/WHAT/WHY format)
□ "How might we" questions generated
□ Success metrics defined with baselines and targets
□ Appetite set (time/team/budget)
□ Constraints documented
□ Scope boundaries clear (what's NOT included)
□ Stakeholder alignment achieved

GATE QUESTIONS:
□ Is the problem specific enough to solve in the appetite?
□ Can we measure success?
□ Do stakeholders agree this is the right problem?
□ Is the team excited about this problem?
```

---

## Output Documents

1. **Problem Canvas** (using template)
2. **Success Metrics Definition**
3. **Appetite & Constraints Document**

---

## Next Phase

Sau khi Define xong → chuyển sang **SKILL_solution-shaping.md** (Phase 3: Develop)
