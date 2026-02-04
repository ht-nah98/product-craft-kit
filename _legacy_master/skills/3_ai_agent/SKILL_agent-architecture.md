# SKILL: AI Agent Architecture
## AI Agent Building Phase 2 - Pattern Selection & Design

> **Reference Methodology**: [AI Agent Building Methodology](../../knowledge/ai-agent-methodology.md)

---

## Mục Đích

Skill này hướng dẫn thực hiện Phase 2 của AI Agent development - Architecture Design, chọn pattern phù hợp và thiết kế components.

### Goals của Phase này:
- ✓ Select appropriate agent pattern
- ✓ Design component specifications
- ✓ Document data flow end-to-end
- ✓ Make technology decisions

**OUTPUT**: Architecture diagram + Component specs + Tech decision record

---

## Template Location

> **Template File**: [_master/templates/07_ai_agent/_template_agent_architecture.md](../../templates/07_ai_agent/_template_agent_architecture.md)

---

## Agent Pattern Selection

### Decision Tree

```
START: Analyze your task
    │
    ▼
┌─────────────────────────────────────┐
│ Task có workflow step-by-step rõ?   │
└─────────────────────────────────────┘
    │
    ├── YES → PATTERN A: Sequential Pipeline
    │         (Input → Step1 → Step2 → Output)
    │
    └── NO → Continue...
              │
              ▼
┌─────────────────────────────────────┐
│ Có nhiều domain/skill khác nhau?    │
└─────────────────────────────────────┘
    │
    ├── YES → PATTERN B: Supervisor + Sub-Agents
    │         (Router dispatches to specialists)
    │
    └── NO → Continue...
              │
              ▼
┌─────────────────────────────────────┐
│ Có thể parallel processing?         │
│ (Không cần human-in-the-loop)       │
└─────────────────────────────────────┘
    │
    ├── YES → PATTERN C: Parallel + Merge
    │         (Fan-out → Process → Merge)
    │
    └── NO → PATTERN D: Single Agent + Tools
             (Simple ReAct with 1-5 tools)
```

---

## Pattern Details

### Pattern A: Sequential Pipeline
**Use when:** Clear step-by-step workflow

```
┌────────┐   ┌────────┐   ┌────────┐   ┌────────┐
│ Step 1 │──▶│ Step 2 │──▶│ Step 3 │──▶│ Step 4 │
│(Intent)│   │(Enrich)│   │(Generate)  │(Validate)
└────────┘   └────────┘   └────────┘   └────────┘
```

**Example**: Text-to-SQL (Intent → Table Selection → SQL Generation → Validation)

**Typical steps:**
1. Intent Classification (LLM)
2. Context Enrichment (RAG/Lookup)
3. Generation (LLM)
4. Validation (Deterministic + LLM)
5. Output Formatting (Deterministic)

---

### Pattern B: Supervisor + Sub-Agents
**Use when:** Multiple domains, routing needed

```
           ┌────────────┐
           │ SUPERVISOR │
           │  (Router)  │
           └────────────┘
                 │
     ┌───────────┼───────────┐
     ▼           ▼           ▼
┌─────────┐ ┌─────────┐ ┌─────────┐
│ Agent A │ │ Agent B │ │ Agent C │
│  (SQL)  │ │  (Doc)  │ │ (Chart) │
└─────────┘ └─────────┘ └─────────┘
```

**Key components:**
1. Supervisor: Intent classification + routing
2. Sub-Agents: Specialized per domain
3. Response Aggregator: Combine if needed

---

### Pattern C: Parallel + Merge
**Use when:** Batch processing, no human-in-loop

```
           ┌────────────┐
           │ SCAFFOLDER │
           │  (Prepare) │
           └────────────┘
                 │
    ┌────────────┼────────────┐
    ▼            ▼            ▼
┌─────────┐ ┌─────────┐ ┌─────────┐
│ Gen #1  │ │ Gen #2  │ │ Gen #N  │ (Parallel)
└─────────┘ └─────────┘ └─────────┘
    │            │            │
    └────────────┼────────────┘
                 ▼
           ┌────────────┐
           │   MERGE    │
           └────────────┘
```

**Example**: Auto-generate test cases in parallel, merge best

---

### Pattern D: Single Agent + Tools
**Use when:** Simple task, few tools

```
           ┌────────────┐
           │   AGENT    │
           │  (ReAct)   │
           └────────────┘
                 │
    ┌────────────┼────────────┐
    ▼            ▼            ▼
┌─────────┐ ┌─────────┐ ┌─────────┐
│ Tool 1  │ │ Tool 2  │ │ Tool 3  │
└─────────┘ └─────────┘ └─────────┘
```

---

## Component Design

Với mỗi component, specify:

| Field | Description |
|-------|-------------|
| **Name** | Component identifier |
| **Type** | □ LLM-based □ Deterministic □ Hybrid |
| **Purpose** | What it does |
| **Input** | Data, format, source |
| **Output** | Data, format, destination |
| **Dependencies** | Upstream/downstream |
| **Error Handling** | Failure mode, fallback |
| **Performance** | Latency, throughput requirements |

### LLM vs Deterministic Decision

| Task Type | Use | Why |
|-----------|-----|-----|
| Intent classification | LLM | Natural language |
| Text generation | LLM | Creative |
| Format validation | Deterministic | Known rules |
| Calculation | Deterministic | Accuracy |
| Entity extraction | Hybrid | LLM + validate |
| SQL generation | Hybrid | LLM + syntax check |

**Rule**: If regex/rules can do it → Deterministic. If needs understanding → LLM.

---

## Technology Stack

### By Team Size

**Solo/Small (1-3 people, MVP):**
- LLM: OpenAI (GPT-4o-mini / GPT-4o)
- Orchestration: LangGraph or simple Python
- Vector DB: Chroma (local) / Pinecone
- Backend: FastAPI
- Frontend: Streamlit / Gradio / Slack bot
- Hosting: Railway / Render

**Medium (3-10 people, production):**
- LLM: OpenAI + Anthropic
- Orchestration: LangGraph + LangSmith
- Vector DB: Pinecone / Weaviate
- Backend: FastAPI + Redis + PostgreSQL
- Frontend: React / Next.js
- Hosting: AWS / GCP

**Enterprise (10+ people, scale):**
- LLM: Custom Gateway + Multi-provider
- Orchestration: Custom framework
- Vector DB: Elasticsearch
- Backend: Go / Java microservices
- Infrastructure: Kubernetes

---

## Completion Checklist

```
□ Agent Pattern selected with rationale
□ Architecture diagram completed
□ All components specified
□ Data flow documented end-to-end
□ Technology decisions recorded
□ Security considerations addressed
□ Cost estimation completed
□ Architecture reviewed

GATE QUESTIONS:
□ Is architecture simple enough for team?
□ Are interfaces between components clear?
□ Is tech stack appropriate for constraints?
□ Have we considered failure modes?
```

---

## Output Documents

1. **Architecture Template** (filled)
2. **Component Specifications**
3. **Technology Decision Record**
4. **Data Flow Diagram**

---

## Next Phase

Sau Phase 2 → tiến hành Build (Phase 3) theo patterns guide
