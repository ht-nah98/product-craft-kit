# SKILL: AI Agent Patterns Reference
## Pattern Library & Implementation Guidelines

> **Reference Methodology**: [AI Agent Building Methodology](../../knowledge/ai-agent-methodology.md)

---

## Mục Đích

Đây là **reference guide** về các Agent Patterns phổ biến với hướng dẫn implementation chi tiết. Dùng khi cần dive deep vào một pattern cụ thể.

---

## Template Location

> **Template File**: [.agent/resources/templates/07_ai_agent/_template_agent_component.md](../../resources/templates/07_ai_agent/_template_agent_component.md)

---

## Pattern A: Sequential Pipeline

### Overview
Xử lý tuần tự qua các bước, output của bước trước là input của bước sau.

### When to Use
- Clear step-by-step workflow
- Need validation between steps
- Predictable flow

### Architecture

```
┌─────────────┐
│   INPUT     │
└──────┬──────┘
       │
       ▼
┌─────────────┐     May be LLM
│   STEP 1    │     or Deterministic
│   Intent    │
└──────┬──────┘
       │
       ▼
┌─────────────┐     Usually Deterministic
│   STEP 2    │     (RAG, API, DB)
│   Enrich    │
└──────┬──────┘
       │
       ▼
┌─────────────┐     Usually LLM
│   STEP 3    │
│  Generate   │
└──────┬──────┘
       │
       ▼
┌─────────────┐     Hybrid recommended
│   STEP 4    │
│  Validate   │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   OUTPUT    │
└─────────────┘
```

### Implementation Checklist

```
□ Define each step's responsibility
□ Define data contract between steps
□ Implement error handling at each step
□ Add logging/tracing
□ Decide LLM vs Deterministic for each
□ Implement retries for LLM steps
□ Add circuit breaker for failures
```

### Best Practices

1. **Keep steps focused**: Một step = một responsibility
2. **Validate between steps**: Early fail is better
3. **Log step inputs/outputs**: Debug được
4. **Make steps testable independently**

---

## Pattern B: Supervisor + Sub-Agents

### Overview
Supervisor agent phân loại và route requests đến specialized sub-agents.

### When to Use
- Multiple domains/skills
- Different processing logic per domain
- Need flexibility to add new domains

### Architecture

```
┌─────────────────────────────────────────────┐
│                 SUPERVISOR                   │
│                                             │
│  1. Receive user request                    │
│  2. Classify intent                         │
│  3. Route to appropriate sub-agent          │
│  4. (Optional) Aggregate responses          │
└──────────────────┬──────────────────────────┘
                   │
      ┌────────────┼────────────┐
      │            │            │
      ▼            ▼            ▼
┌───────────┐ ┌───────────┐ ┌───────────┐
│ SUB-AGENT │ │ SUB-AGENT │ │ SUB-AGENT │
│     A     │ │     B     │ │     C     │
│ (Domain1) │ │ (Domain2) │ │ (Domain3) │
└───────────┘ └───────────┘ └───────────┘
```

### Supervisor Design

**Responsibilities:**
1. Intent classification (LLM)
2. Route to correct sub-agent
3. Handle fallback (no match)
4. (Optional) Aggregate multi-agent responses

**Routing Strategies:**
- **Keyword-based**: Fast, but rigid
- **LLM classification**: Flexible, but latency
- **Embedding similarity**: Balance

### Sub-Agent Design

Each sub-agent is specialized:
- Deep domain context in prompt
- Specific tools for domain
- Custom output format
- Own evaluation metrics

### Implementation Checklist

```
□ Define clear domain boundaries
□ Design supervisor routing logic
□ Implement each sub-agent independently
□ Define fallback behavior
□ Add tracing for routing decisions
□ Test routing accuracy
□ Monitor domain distribution
```

---

## Pattern C: Parallel + Merge

### Overview
Fan-out requests xử lý parallel, sau đó merge results.

### When to Use
- Batch processing
- Generate multiple variations
- No human-in-the-loop needed
- Speed matters

### Architecture

```
┌─────────────────────────────────────────────┐
│               SCAFFOLDER                     │
│                                             │
│  1. Prepare batch of tasks                  │
│  2. Split into N parallel jobs              │
└──────────────────┬──────────────────────────┘
                   │
      ┌────────────┼────────────┐
      │            │            │
      ▼            ▼            ▼
┌───────────┐ ┌───────────┐ ┌───────────┐
│   JOB 1   │ │   JOB 2   │ │   JOB N   │
│ (Parallel)│ │ (Parallel)│ │ (Parallel)│
└─────┬─────┘ └─────┬─────┘ └─────┬─────┘
      │            │            │
      └────────────┼────────────┘
                   ▼
┌─────────────────────────────────────────────┐
│                MERGER                        │
│                                             │
│  1. Collect all results                     │
│  2. Validate/score each                     │
│  3. Select best / combine                   │
└─────────────────────────────────────────────┘
```

### Considerations

**Parallelism:**
- Rate limiting (API quotas)
- Cost control
- Error handling (partial failures)

**Merging:**
- How to select best result?
- How to handle conflicts?
- What if all fail?

### Implementation Checklist

```
□ Define parallelization strategy
□ Implement rate limiting
□ Handle partial failures gracefully
□ Design merge/selection logic
□ Monitor cost per batch
□ Add timeout handling
□ Implement result validation
```

---

## Pattern D: Single Agent + Tools

### Overview
Một agent với capability sử dụng multiple tools (ReAct pattern).

### When to Use
- Simple task
- Less than 5 tools
- Need flexibility

### Architecture

```
┌─────────────────────────────────────────────┐
│                 AGENT                        │
│                                             │
│  While not done:                            │
│    1. THINK: What should I do?              │
│    2. ACT: Call a tool                      │
│    3. OBSERVE: Get tool result              │
│    4. Decide: Continue or respond?          │
└──────────────────┬──────────────────────────┘
                   │
      ┌────────────┼────────────┐
      │            │            │
      ▼            ▼            ▼
┌───────────┐ ┌───────────┐ ┌───────────┐
│   TOOL    │ │   TOOL    │ │   TOOL    │
│  Search   │ │   Calc    │ │    API    │
└───────────┘ └───────────┘ └───────────┘
```

### Tool Design Principles

1. **Clear description**: Agent needs to understand khi nào dùng
2. **Well-defined input/output**: Typed schemas
3. **Error handling**: Return helpful errors
4. **Idempotent when possible**: Safe to retry

### Implementation Checklist

```
□ Define tool set (keep minimal)
□ Write clear tool descriptions
□ Implement tool input validation
□ Add tool usage logging
□ Set max iterations limit
□ Implement timeout
□ Test tool selection accuracy
```

---

## Choosing Between Patterns

| Scenario | Recommended Pattern |
|----------|-------------------|
| ETL pipeline with fixed steps | Sequential |
| Multi-skill chatbot | Supervisor |
| Test generation at scale | Parallel |
| Simple Q&A with tools | Single Agent |
| Complex multi-step reasoning | Sequential + Tools |

---

## Combining Patterns

Patterns can be combined:

**Supervisor → Sequential**
- Route to specialized pipelines

**Sequential with Parallel step**
- One step fans out to parallelize

**Supervisor with Parallel merge**
- Multiple agents run, merge best

---

## Anti-Patterns to Avoid

1. **Over-engineering**: Start simple, add complexity as needed
2. **Too many tools**: Keep tools focused (3-5 max)
3. **No validation**: Always validate LLM outputs
4. **No fallbacks**: Handle failures gracefully
5. **Ignoring latency**: Users expect speed
