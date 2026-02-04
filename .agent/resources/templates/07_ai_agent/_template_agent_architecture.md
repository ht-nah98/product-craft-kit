# AI Agent Architecture
## [Agent Name]

---

## Document Info

| Field | Value |
|-------|-------|
| **Agent Name** | [Name] |
| **Date** | YYYY-MM-DD |
| **Architect** | [Name] |
| **Phase** | 2. Architecture |
| **Status** | Draft / Reviewed / Approved |

---

## 1. Pattern Selection

### 1.1 Task Analysis

| Question | Answer |
|----------|--------|
| Task có workflow step-by-step rõ ràng? | Yes / No |
| Có nhiều domain/skill khác nhau? | Yes / No |
| Có thể parallel processing? | Yes / No |
| Có human-in-the-loop? | Yes / No |

### 1.2 Selected Pattern

- [ ] **Pattern A: Sequential Pipeline** — Step-by-step workflow
- [ ] **Pattern B: Supervisor + Sub-Agents** — Multi-domain routing
- [ ] **Pattern C: Parallel + Merge** — Batch processing
- [ ] **Pattern D: Single Agent + Tools** — Simple task with tools

**Rationale:**
[Why this pattern fits our task]

---

## 2. Architecture Diagram

### 2.1 High-Level View

*(Draw or describe the architecture)*

```
[User Input]
     │
     ▼
┌─────────────┐
│ Component 1 │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Component 2 │
└──────┬──────┘
       │
       ▼
[Output]
```

### 2.2 Component List

| # | Component | Type | Purpose |
|---|-----------|------|---------|
| 1 | [Name] | LLM / Deterministic / Hybrid | [Purpose] |
| 2 | [Name] | LLM / Deterministic / Hybrid | [Purpose] |
| 3 | [Name] | LLM / Deterministic / Hybrid | [Purpose] |
| 4 | [Name] | LLM / Deterministic / Hybrid | [Purpose] |

---

## 3. Component Specifications

### Component 1: [Name]

| Field | Value |
|-------|-------|
| **Name** | [Name] |
| **Type** | ⬜ LLM-based ⬜ Deterministic ⬜ Hybrid |
| **Purpose** | [What it does] |

**Input:**
- Data: [Description]
- Format: [Format]
- Source: [Where from]

**Output:**
- Data: [Description]
- Format: [Format]
- Destination: [Where to]

**Dependencies:**
- Upstream: [Component]
- Downstream: [Component]

**Error Handling:**
- Failure mode: [What happens on failure]
- Fallback: [Alternative action]

**Performance:**
- Latency: [X] ms
- Throughput: [X] req/min

---

### Component 2: [Name]

*(Repeat structure for each component)*

| Field | Value |
|-------|-------|
| **Name** | [Name] |
| **Type** | ⬜ LLM-based ⬜ Deterministic ⬜ Hybrid |
| **Purpose** | [What it does] |

**Input/Output/Dependencies/Error Handling/Performance:**
*(Fill as above)*

---

## 4. Data Flow

### 4.1 End-to-End Flow

```
USER INPUT
┌──────────────────────────────────────────────────────┐
│ Type: [Description]                                   │
│ Format: [Format]                                      │
│ Example: [Example]                                    │
└──────────────────────────────────────────────────────┘
                         │
                         ▼
PREPROCESSING
┌──────────────────────────────────────────────────────┐
│ □ Validation                                          │
│ □ Sanitization                                        │
│ □ PII Detection/Redaction                             │
│ □ Format normalization                                │
└──────────────────────────────────────────────────────┘
                         │
                         ▼
CONTEXT ENRICHMENT
┌──────────────────────────────────────────────────────┐
│ Data Sources:                                         │
│ □ Vector DB (RAG): [Details]                          │
│ □ Database: [Details]                                 │
│ □ API: [Details]                                      │
│ □ Cache: [Details]                                    │
└──────────────────────────────────────────────────────┘
                         │
                         ▼
AGENT PROCESSING
┌──────────────────────────────────────────────────────┐
│ [Refer to selected pattern architecture]              │
└──────────────────────────────────────────────────────┘
                         │
                         ▼
POST-PROCESSING
┌──────────────────────────────────────────────────────┐
│ □ Output validation                                   │
│ □ Format transformation                               │
│ □ PII un-redaction                                    │
│ □ Logging & metrics                                   │
└──────────────────────────────────────────────────────┘
                         │
                         ▼
FINAL OUTPUT
┌──────────────────────────────────────────────────────┐
│ Type: [Description]                                   │
│ Format: [Format]                                      │
│ Delivery: [Channel]                                   │
└──────────────────────────────────────────────────────┘
```

---

## 5. Technology Stack

### 5.1 LLM Access

| Options | Pros | Cons |
|---------|------|------|
| [Option 1] | [Pros] | [Cons] |
| [Option 2] | [Pros] | [Cons] |

**Decision**: [Selected option]
**Rationale**: [Why]

### 5.2 Agent Orchestration

| Options | Pros | Cons |
|---------|------|------|
| LangGraph | Flexible, visual | Learning curve |
| Custom Python | Full control | Build from scratch |
| Other | [Pros] | [Cons] |

**Decision**: [Selected option]
**Rationale**: [Why]

### 5.3 Knowledge Base / RAG

| Options | Pros | Cons |
|---------|------|------|
| [Option 1] | [Pros] | [Cons] |
| [Option 2] | [Pros] | [Cons] |

**Decision**: [Selected option]
**Rationale**: [Why]

### 5.4 Backend / API

**Decision**: [Selected option]
**Rationale**: [Why]

### 5.5 Frontend / Interface

**Decision**: [Selected option]
**Rationale**: [Why]

### 5.6 Stack Summary

| Layer | Technology |
|-------|------------|
| LLM Provider | [Tech] |
| Orchestration | [Tech] |
| Vector DB | [Tech] |
| Backend | [Tech] |
| Frontend | [Tech] |
| Hosting | [Tech] |

---

## 6. Cost Estimation

### 6.1 Development Cost

| Item | Cost |
|------|------|
| Engineering time | [X] hours × $[Y] = $[Z] |
| Tools/services | $[X]/month |
| Total development | $[Total] |

### 6.2 Operational Cost (Monthly)

| Item | Unit Cost | Volume | Total |
|------|-----------|--------|-------|
| LLM API | $[X]/1K tokens | [X]K tokens | $[Y] |
| Vector DB | $[X]/month | - | $[X] |
| Hosting | $[X]/month | - | $[X] |
| **Total/month** | | | **$[Total]** |

---

## 7. Security Considerations

- [ ] PII handling plan documented
- [ ] Data residency requirements met
- [ ] Authentication mechanism defined
- [ ] Authorization rules defined
- [ ] Audit logging planned
- [ ] Data encryption in transit/at rest

---

## 8. Completion Checklist

```
□ Agent Pattern selected with rationale
□ Architecture diagram completed
□ All components specified
□ Data flow documented end-to-end
□ Technology decisions recorded
□ Security considerations addressed
□ Cost estimation completed
□ Architecture reviewed by stakeholders
```

### Gate Questions

- [ ] Is architecture simple enough for team?
- [ ] Are interfaces between components clear?
- [ ] Is tech stack appropriate for constraints?
- [ ] Have we considered failure modes?

---

## Approvals

| Role | Name | Date |
|------|------|------|
| Tech Lead | | |
| Architect | | |
| Security | | |

---

## Next Step

→ Proceed to Phase 3: Build & Test
