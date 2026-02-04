# AI Agent Problem Canvas
## [Agent Name]

---

## Document Info

| Field | Value |
|-------|-------|
| **Agent Name** | [Name] |
| **Date** | YYYY-MM-DD |
| **Owner** | [Name] |
| **Phase** | 1. Discovery |
| **Status** | Draft / Reviewed / Approved |

---

## 1. Problem Statement

### 1.1 Current State

```
Hiện tại, [WHO - ai]
đang phải [DO WHAT - làm gì]
mất [HOW LONG - bao lâu] để [ACHIEVE - đạt được gì].

Điều này gây ra [PAIN POINTS - vấn đề gì]
và tốn [COST - chi phí/thời gian bao nhiêu].
```

### 1.2 Desired Outcome

```
AI Agent sẽ giúp [WHO]
có thể [DO WHAT]
trong [TIME - thời gian mới]
với độ chính xác [ACCURACY]
và tiết kiệm [SAVINGS].
```

---

## 2. AI Agent Validation

### 2.1 Why AI Agent?

Tick all that apply:

- [ ] Task đòi hỏi reasoning/judgment
- [ ] Input không có format cố định (natural language)
- [ ] Cần xử lý nhiều edge cases khó enumerate
- [ ] Task có tính sáng tạo/generative
- [ ] Cần hiểu context phức tạp

> **Threshold**: Cần ít nhất 2 items. Nếu không, consider rule-based system.

**Items checked**: [X]/5

### 2.2 Why NOT Traditional Software?

[Explain why rule-based/traditional approach won't work]

---

## 3. User Analysis

### 3.1 Primary Users

| Field | Value |
|-------|-------|
| **User Persona** | [Name/Role] |
| **Role** | [Description] |
| **Technical Level** | ⬜ Non-tech ⬜ Semi-tech ⬜ Technical |
| **Usage Frequency** | ⬜ Daily ⬜ Weekly ⬜ Occasional |
| **Current Workflow** | [Description] |
| **Pain Points** | [List] |
| **Success Criteria** | [What makes them happy] |

### 3.2 Secondary Stakeholders

| Stakeholder | Interest |
|-------------|----------|
| Data/Content Owners | [Interest] |
| IT/Security Team | [Interest] |
| Management/Sponsor | [Interest] |

### 3.3 Interaction Channels

How will users interact?

- [ ] Web App
- [ ] Mobile App
- [ ] Slack/Teams
- [ ] IDE Plugin
- [ ] CLI
- [ ] API
- [ ] Email
- [ ] Other: [Specify]

---

## 4. Success Metrics

### 4.1 Efficiency Metrics

| Metric | Baseline | Target | Method |
|--------|----------|--------|--------|
| Time per task | [X] min | [Y] min | Tracking |
| Tasks completed/day | [X] | [Y] | Logging |
| Manual effort saved | [X] hrs/mo | [Y] hrs/mo | Survey |

### 4.2 Quality Metrics

| Metric | Baseline | Target | Method |
|--------|----------|--------|--------|
| Accuracy rate | N/A | [X]% | Eval set |
| Error rate | [X]% | < [Y]% | Logging |
| User satisfaction | N/A | [X]/5 | Survey |

### 4.3 Adoption Metrics

| Metric | Baseline | Target | Method |
|--------|----------|--------|--------|
| Daily active users | 0 | [X] | Analytics |
| Adoption rate | 0% | [X]% | Analytics |
| 7-day retention | N/A | [X]% | Analytics |

### 4.4 Cost Metrics

| Metric | Budget | Alert At | Method |
|--------|--------|----------|--------|
| LLM cost per query | $[X] | > $[Y] | Gateway |
| Monthly operational | $[X] | > $[Y] | Billing |
| Cost per user | $[X] | > $[Y] | Calculate |

---

## 5. Constraints

### 5.1 Technical Constraints

**Response Time:**
- [ ] Real-time (< 2s)
- [ ] Near real-time (< 10s)
- [ ] Async OK

**Availability:**
- [ ] 99.9% uptime required
- [ ] 99% OK
- [ ] Best effort

**Scale:**
- [ ] < 100 queries/day
- [ ] 100-10K/day
- [ ] > 10K/day

**Integration Requirements:**
- Must integrate with: [Systems]
- Data sources: [Sources]

### 5.2 Security & Compliance

- [ ] PII handling required
- [ ] Data cannot leave organization
- [ ] Audit logging required
- [ ] Role-based access control needed
- [ ] Compliance: [Regulation]

### 5.3 Resource Constraints

| Resource | Value |
|----------|-------|
| Development budget | $[X] over [Y] months |
| Monthly operational | $[X]/month |
| Available engineers | [N] |
| AI/ML expertise | ⬜ Yes ⬜ Limited ⬜ No |
| MVP deadline | [Date] |
| Production deadline | [Date] |

---

## 6. Completion Checklist

```
□ Problem Definition Canvas completed
□ AI Agent necessity validated (2+ items checked)
□ User Analysis Matrix filled out
□ At least 3 user interviews conducted
□ Success Metrics defined with baselines
□ Constraints documented and validated
□ Go/No-Go decision made
```

### Gate Questions

- [ ] Is the problem specific enough? (Solvable in 6-8 weeks?)
- [ ] Is AI Agent the right solution? (Not just rules?)
- [ ] Are success metrics measurable?
- [ ] Are constraints realistic given resources?

---

## 7. Decision

### 7.1 Go / No-Go

- [ ] **GO** - Proceed to Architecture design
- [ ] **NO-GO** - Reconsider approach

**Rationale:**
[Explain decision]

### 7.2 If No-Go, Alternatives

- [ ] Traditional software
- [ ] Simpler automation
- [ ] Revisit with more resources
- [ ] Kill the initiative

---

## Approvals

| Role | Name | Decision | Date |
|------|------|----------|------|
| Product Owner | | Go / No-Go | |
| Tech Lead | | Go / No-Go | |
| Stakeholder | | Go / No-Go | |

---

## Next Step

→ If GO, proceed to Phase 2: Architecture Design
