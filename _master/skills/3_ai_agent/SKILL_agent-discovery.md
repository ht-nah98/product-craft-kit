# SKILL: AI Agent Discovery
## AI Agent Building Phase 1 - Problem & User Analysis

> **Reference Methodology**: [AI Agent Building Methodology](../../knowledge/ai-agent-methodology.md)

---

## Mục Đích

Skill này hướng dẫn thực hiện Phase 1 của AI Agent development - Discovery & Problem Definition, đảm bảo xác định đúng bài toán cần AI Agent.

### Goals của Phase này:
- ✓ Validate that AI Agent is the right solution
- ✓ Define problem clearly with measurable outcomes
- ✓ Understand users and their workflows
- ✓ Establish success metrics và constraints

**OUTPUT**: Problem Definition Canvas + User Analysis + Metrics Framework

---

## Template Location

> **Template File**: [_master/templates/07_ai_agent/_template_agent_problem.md](../../templates/07_ai_agent/_template_agent_problem.md)

---

## Core Principles (Reference)

Trước khi bắt đầu, nắm vững 6 nguyên tắc:

| # | Principle | Meaning |
|---|-----------|---------|
| 1 | Start Narrow, Scale Later | Một nhiệm vụ rõ ràng, không "super agent" |
| 2 | Hybrid Architecture | LLM cho reasoning, deterministic cho execution |
| 3 | Infrastructure First | Gateway, logging, monitoring từ đầu |
| 4 | Domain Expert > Generic | Agent chuyên biệt luôn tốt hơn |
| 5 | Reusable Components | Design for composition |
| 6 | Measure Everything | Define metrics trước khi build |

---

## Quy Trình Thực Hiện

### Bước 1: Problem Definition

**Cần trả lời:**

1. **WHO**: Ai sử dụng agent?
2. **DO WHAT**: Họ đang làm gì thủ công?
3. **HOW LONG**: Mất bao lâu?
4. **PAIN POINTS**: Vấn đề gì xảy ra?
5. **COST**: Tốn bao nhiêu thời gian/tiền?

**Desired Outcome Format:**
> AI Agent sẽ giúp [WHO] có thể [DO WHAT] trong [TIME mới] với độ chính xác [ACCURACY] và tiết kiệm [SAVINGS].

### Bước 2: Validate AI Agent Need

**Checklist - AI Agent phù hợp khi:**

```
□ Task đòi hỏi reasoning/judgment
□ Input không có format cố định (natural language)
□ Cần xử lý nhiều edge cases khó enumerate
□ Task có tính sáng tạo/generative
□ Cần hiểu context phức tạp
```

**If không tick được ít nhất 2**: Consider rule-based system thay vì AI Agent.

### Bước 3: User & Stakeholder Analysis

**Primary Users:**
- Role: ___
- Technical Level: □ Non-tech □ Semi-tech □ Technical
- Frequency: □ Daily □ Weekly □ Occasional
- Current Workflow: ___
- Pain Points: ___

**Interaction Channels:**
- □ Web App □ Mobile □ Slack/Teams
- □ IDE Plugin □ CLI □ API
- □ Email □ Other

### Bước 4: Define Success Metrics

**4 Categories:**

1. **Efficiency Metrics**
   - Time per task: ___ min → ___ min
   - Tasks completed/day: ___ → ___
   - Manual effort saved: ___ hrs/month

2. **Quality Metrics**
   - Accuracy rate: Target ____%
   - Error rate: < ____%
   - User satisfaction: ___/5

3. **Adoption Metrics**
   - Daily active users: ___
   - Adoption rate: ____%
   - 7-day retention: ____%

4. **Cost Metrics**
   - LLM cost per query: $___
   - Monthly operational cost: $___
   - Cost per user: $___

### Bước 5: Document Constraints

**Technical:**
- Response time: □ Real-time (<2s) □ Near real-time (<10s) □ Async OK
- Availability: □ 99.9% □ 99% □ Best effort
- Scale: □ <100/day □ 100-10K/day □ >10K/day

**Security:**
- □ PII handling required
- □ Data cannot leave org
- □ Audit logging required
- □ RBAC needed

**Resources:**
- Development budget: $___
- Monthly ops budget: $___
- Team size: ___ engineers
- AI/ML expertise: □ Yes □ Limited □ No
- MVP deadline: ___

---

## Completion Checklist

```
□ Problem Definition Canvas completed
□ AI Agent necessity validated
□ User Analysis Matrix filled out
□ At least 3 user interviews conducted
□ Success Metrics defined with baselines
□ Constraints documented và validated
□ Go/No-Go decision made

GATE QUESTIONS:
□ Is the problem specific enough? (6-8 weeks solvable?)
□ Is AI Agent the right solution? (Not just rules?)
□ Are success metrics measurable?
□ Are constraints realistic?
```

---

## Output Documents

1. **Agent Problem Canvas** (using template)
2. **User Analysis Matrix**
3. **Metrics Framework**
4. **Constraints Checklist**

---

## Next Phase

Sau Phase 1 → chuyển sang **SKILL_agent-architecture.md** (Phase 2: Architecture)
