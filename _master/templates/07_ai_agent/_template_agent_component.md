# AI Agent Component Specification
## [Component Name]

---

## Document Info

| Field | Value |
|-------|-------|
| **Component** | [Name] |
| **Agent** | [Parent Agent Name] |
| **Date** | YYYY-MM-DD |
| **Owner** | [Name] |

---

## 1. Overview

### 1.1 Basic Info

| Field | Value |
|-------|-------|
| **Name** | [Component Name] |
| **Type** | ⬜ LLM-based ⬜ Deterministic ⬜ Hybrid |
| **Purpose** | [One-line description] |

### 1.2 Detailed Description

[Multi-line description of what this component does and why it exists]

---

## 2. Input Specification

### 2.1 Input Data

| Field | Value |
|-------|-------|
| **Data Type** | [Type] |
| **Format** | [JSON / Text / Other] |
| **Source** | [From where] |

### 2.2 Input Schema

```json
{
  "field1": "string",
  "field2": "number",
  "field3": {
    "nested": "object"
  }
}
```

### 2.3 Input Example

```json
{
  "field1": "example value",
  "field2": 123
}
```

### 2.4 Input Validation Rules

| Rule | Description |
|------|-------------|
| Required fields | [List] |
| Max length | [Limits] |
| Format validation | [Regex/rules] |

---

## 3. Output Specification

### 3.1 Output Data

| Field | Value |
|-------|-------|
| **Data Type** | [Type] |
| **Format** | [JSON / Text / Other] |
| **Destination** | [To where] |

### 3.2 Output Schema

```json
{
  "result": "string",
  "confidence": "number",
  "metadata": {}
}
```

### 3.3 Output Example

```json
{
  "result": "processed output",
  "confidence": 0.95
}
```

---

## 4. Processing Logic

### 4.1 For LLM-based Components

**Prompt Template:**
```
[System prompt or instruction]

Context: {context}
Input: {input}

[Expected output format]
```

**Model Configuration:**
| Setting | Value |
|---------|-------|
| Model | [e.g., gpt-4o] |
| Temperature | [0.0 - 1.0] |
| Max tokens | [Number] |
| Top P | [0.0 - 1.0] |

### 4.2 For Deterministic Components

**Logic Description:**
1. Step 1: [Description]
2. Step 2: [Description]
3. Step 3: [Description]

**Business Rules:**
| Rule | Description |
|------|-------------|
| Rule 1 | [Description] |
| Rule 2 | [Description] |

### 4.3 For Hybrid Components

**LLM Part:**
[What the LLM handles]

**Deterministic Part:**
[What traditional code handles]

**Interaction:**
[How they work together]

---

## 5. Dependencies

### 5.1 Upstream

| Component | Data Received |
|-----------|---------------|
| [Component Name] | [Data description] |

### 5.2 Downstream

| Component | Data Sent |
|-----------|-----------|
| [Component Name] | [Data description] |

### 5.3 External Services

| Service | Purpose | Required? |
|---------|---------|-----------|
| [Service 1] | [Purpose] | Yes / No |
| [Service 2] | [Purpose] | Yes / No |

---

## 6. Error Handling

### 6.1 Failure Modes

| Scenario | Handling |
|----------|----------|
| Invalid input | [Action] |
| LLM timeout | [Action] |
| LLM error | [Action] |
| External service down | [Action] |

### 6.2 Fallback Strategy

**Primary fallback:**
[What to do when main processing fails]

**Secondary fallback:**
[What to do if primary fallback also fails]

### 6.3 Retry Policy

| Setting | Value |
|---------|-------|
| Max retries | [Number] |
| Retry delay | [ms] |
| Backoff strategy | [Linear / Exponential] |

---

## 7. Performance Requirements

### 7.1 Latency

| Metric | Target | Max Acceptable |
|--------|--------|----------------|
| P50 | [X] ms | [Y] ms |
| P95 | [X] ms | [Y] ms |
| P99 | [X] ms | [Y] ms |

### 7.2 Throughput

| Metric | Target |
|--------|--------|
| Requests/second | [X] |
| Concurrent requests | [X] |

### 7.3 Resource Limits

| Resource | Limit |
|----------|-------|
| Memory | [X] MB |
| CPU | [X] cores |
| Timeout | [X] seconds |

---

## 8. Quality Metrics

### 8.1 Accuracy (for LLM components)

| Metric | Target | Measurement |
|--------|--------|-------------|
| Overall accuracy | [X]% | Eval set |
| Precision | [X]% | [Method] |
| Recall | [X]% | [Method] |

### 8.2 Evaluation Dataset

| Dataset | Size | Purpose |
|---------|------|---------|
| [Name] | [X] examples | [Purpose] |

---

## 9. Monitoring & Logging

### 9.1 Logs

| Log Type | Level | Content |
|----------|-------|---------|
| Input | DEBUG | Full input |
| Output | DEBUG | Full output |
| Errors | ERROR | Error details |
| Latency | INFO | Processing time |

### 9.2 Metrics to Track

- [ ] Request count
- [ ] Success/failure rate
- [ ] Latency distribution
- [ ] Token usage (if LLM)
- [ ] Cost per request

### 9.3 Alerts

| Condition | Threshold | Action |
|-----------|-----------|--------|
| Error rate | > [X]% | [Action] |
| Latency P95 | > [X] ms | [Action] |
| Cost spike | > [X]$ | [Action] |

---

## 10. Testing Strategy

### 10.1 Unit Tests

| Test Case | Description | Expected |
|-----------|-------------|----------|
| [Test 1] | [Description] | [Expected] |
| [Test 2] | [Description] | [Expected] |

### 10.2 Integration Tests

| Test Case | Components | Expected |
|-----------|------------|----------|
| [Test 1] | [List] | [Expected] |

### 10.3 Evaluation Tests (LLM)

| Scenario | Input | Expected Output |
|----------|-------|-----------------|
| [Scenario 1] | [Input] | [Output] |
| [Scenario 2] | [Input] | [Output] |

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| v1.0 | [Date] | [Name] | Initial version |
