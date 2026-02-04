# 🏗️ AI AGENT BUILDING METHODOLOGY
## Quy Trình Chuẩn Hóa Xây Dựng Hệ Thống AI Agent
### Đúc kết từ Uber's AI Agent Ecosystem & Industry Best Practices

---

## 📋 MỤC ĐÍCH CỦA TÀI LIỆU NÀY

Tài liệu này là **methodology chuẩn hóa** để xây dựng AI Agent systems. Được thiết kế để:
- Áp dụng cho **bất kỳ bài toán AI Agent nào** (không chỉ riêng một domain)
- Làm **reference guide** cho AI models hỗ trợ quá trình build sản phẩm
- Đảm bảo **consistency và quality** xuyên suốt quá trình phát triển
- **Có thể customize** theo context cụ thể của từng dự án

---

## 🎯 NGUYÊN TẮC CỐT LÕI (Core Principles)

Trước khi bắt đầu bất kỳ phase nào, cần nắm vững 6 nguyên tắc sau:

### Principle 1: Start Narrow, Scale Later
> "Giải quyết một vấn đề hẹp, cụ thể trước. Mở rộng sau."

- Không xây dựng "super agent" làm mọi thứ
- Mỗi agent có một nhiệm vụ rõ ràng, đo lường được
- Chỉ mở rộng khi đã chứng minh giá trị

### Principle 2: Hybrid Architecture
> "Kết hợp LLM (sáng tạo) với Deterministic (chính xác)"

- LLM cho: reasoning, generation, classification
- Deterministic cho: validation, execution, calculation
- Không phải mọi thứ đều cần LLM

### Principle 3: Infrastructure First
> "Xây nền tảng trước, agent sau"

- Gateway/abstraction layer cho LLM access
- Logging, monitoring, cost tracking từ đầu
- Security & PII handling là bắt buộc

### Principle 4: Domain Expert > Generic
> "Agent chuyên biệt luôn tốt hơn agent đa năng"

- Deep context về domain cụ thể
- Prompts được fine-tune cho use case
- Tools được customize cho workflow

### Principle 5: Reusable Components
> "Xây building blocks có thể tái sử dụng"

- Tách riêng các components độc lập
- Design for composition
- Document interfaces rõ ràng

### Principle 6: Measure Everything
> "Không đo được thì không cải thiện được"

- Define metrics trước khi build
- Track cost, latency, accuracy
- User feedback loop

---

## 📊 TỔNG QUAN QUY TRÌNH (Process Overview)

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        AI AGENT BUILDING PROCESS                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  PHASE 1          PHASE 2           PHASE 3          PHASE 4            │
│  ┌──────┐        ┌──────┐          ┌──────┐         ┌──────┐           │
│  │DISCO-│   →    │ARCHI-│    →     │ BUILD │   →    │DEPLOY│           │
│  │VERY  │        │TECTURE│          │ & TEST│        │& ITER│           │
│  └──────┘        └──────┘          └──────┘         └──────┘           │
│                                                                          │
│  Week 1-2        Week 2-3          Week 3-6         Week 6+             │
│                                                                          │
│  • Problem       • Pattern         • Foundation     • Production        │
│  • Users         • Components      • Core Agent     • Monitoring        │
│  • Metrics       • Tech Stack      • Integration    • Iteration         │
│  • Constraints   • Data Flow       • Testing        • Scaling           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 1: DISCOVERY & PROBLEM DEFINITION

## 1.1 Problem Statement

### Template: Problem Definition Canvas

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PROBLEM DEFINITION CANVAS                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PROJECT NAME: _________________________________________________    │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 1. PROBLEM STATEMENT                                         │   │
│  │                                                              │   │
│  │ Hiện tại, [WHO - ai] đang phải [DO WHAT - làm gì]           │   │
│  │ mất [HOW LONG - bao lâu] để [ACHIEVE - đạt được gì].        │   │
│  │                                                              │   │
│  │ Điều này gây ra [PAIN POINTS - vấn đề gì] và tốn            │   │
│  │ [COST - chi phí/thời gian bao nhiêu].                       │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 2. DESIRED OUTCOME                                           │   │
│  │                                                              │   │
│  │ AI Agent sẽ giúp [WHO] có thể [DO WHAT]                     │   │
│  │ trong [TIME - thời gian mới] với độ chính xác [ACCURACY]    │   │
│  │ và tiết kiệm [SAVINGS].                                     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 3. WHY AI AGENT? (Không phải traditional software)          │   │
│  │                                                              │   │
│  │ □ Task đòi hỏi reasoning/judgment                           │   │
│  │ □ Input không có format cố định (natural language)          │   │
│  │ □ Cần xử lý nhiều edge cases khó enumerate                  │   │
│  │ □ Task có tính sáng tạo/generative                          │   │
│  │ □ Cần hiểu context phức tạp                                 │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Ví dụ điền (Uber QueryGPT case):

```
PROJECT NAME: QueryGPT - Text-to-SQL Agent

1. PROBLEM STATEMENT
Hiện tại, [Operations team 36% of 1.2M queries/month] đang phải 
[viết SQL queries thủ công] mất [10 phút mỗi query] để 
[lấy data từ database].

Điều này gây ra [bottleneck trong việc ra quyết định, phụ thuộc 
vào data team] và tốn [140,000 người-giờ mỗi tháng].

2. DESIRED OUTCOME
AI Agent sẽ giúp [Operations team] có thể [query data bằng 
ngôn ngữ tự nhiên] trong [3 phút] với độ chính xác [>80%]
và tiết kiệm [~100,000 người-giờ/tháng].

3. WHY AI AGENT?
☑ Task đòi hỏi reasoning/judgment (hiểu intent)
☑ Input không có format cố định (natural language questions)
☑ Cần xử lý nhiều edge cases (various question types)
☑ Cần hiểu context phức tạp (business domain + schema)
```

---

## 1.2 User & Stakeholder Analysis

### Template: User Analysis Matrix

```
┌─────────────────────────────────────────────────────────────────────┐
│                      USER ANALYSIS MATRIX                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PRIMARY USERS (Người dùng trực tiếp)                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ User Persona 1: ________________________________________    │   │
│  │ • Role: ________________________________________________    │   │
│  │ • Technical Level: □ Non-tech  □ Semi-tech  □ Technical    │   │
│  │ • Frequency of Use: □ Daily  □ Weekly  □ Occasional        │   │
│  │ • Current Workflow: ____________________________________    │   │
│  │ • Pain Points: _________________________________________    │   │
│  │ • Success Criteria: ____________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  SECONDARY STAKEHOLDERS (Bên liên quan)                             │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ • Data/Content Owners: _________________________________    │   │
│  │ • IT/Security Team: ____________________________________    │   │
│  │ • Management/Sponsor: __________________________________    │   │
│  │ • Affected Teams: ______________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  INTERACTION CHANNELS                                                │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Web App      □ Mobile App    □ Slack/Teams               │   │
│  │ □ IDE Plugin   □ CLI           □ API                       │   │
│  │ □ Email        □ Other: ____________________________       │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 1.3 Success Metrics Definition

### Template: Metrics Framework

```
┌─────────────────────────────────────────────────────────────────────┐
│                      METRICS FRAMEWORK                               │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  CATEGORY 1: EFFICIENCY METRICS (Hiệu quả)                          │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Metric              │ Baseline    │ Target      │ Method    │   │
│  │─────────────────────│─────────────│─────────────│───────────│   │
│  │ Time per task       │ ___ min     │ ___ min     │ Tracking  │   │
│  │ Tasks completed/day │ ___         │ ___         │ Logging   │   │
│  │ Manual effort saved │ ___ hrs/mo  │ ___ hrs/mo  │ Survey    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  CATEGORY 2: QUALITY METRICS (Chất lượng)                           │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Metric              │ Baseline    │ Target      │ Method    │   │
│  │─────────────────────│─────────────│─────────────│───────────│   │
│  │ Accuracy rate       │ N/A         │ ____%       │ Eval set  │   │
│  │ Error rate          │ ____%       │ < ____%     │ Logging   │   │
│  │ User satisfaction   │ N/A         │ ___/5       │ Survey    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  CATEGORY 3: ADOPTION METRICS (Áp dụng)                             │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Metric              │ Baseline    │ Target      │ Method    │   │
│  │─────────────────────│─────────────│─────────────│───────────│   │
│  │ Daily active users  │ 0           │ ___         │ Analytics │   │
│  │ Adoption rate       │ 0%          │ ____%       │ Analytics │   │
│  │ Retention (7-day)   │ N/A         │ ____%       │ Analytics │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  CATEGORY 4: COST METRICS (Chi phí)                                 │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Metric              │ Budget      │ Alert at    │ Method    │   │
│  │─────────────────────│─────────────│─────────────│───────────│   │
│  │ LLM cost per query  │ $___        │ > $___      │ Gateway   │   │
│  │ Total monthly cost  │ $___        │ > $___      │ Billing   │   │
│  │ Cost per user       │ $___        │ > $___      │ Calculate │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 1.4 Constraints & Requirements

### Template: Constraints Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                    CONSTRAINTS CHECKLIST                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  TECHNICAL CONSTRAINTS                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Response Time                                                │   │
│  │ □ Real-time (< 2s)  □ Near real-time (< 10s)  □ Async OK   │   │
│  │                                                              │   │
│  │ Availability                                                 │   │
│  │ □ 99.9% uptime required  □ 99% OK  □ Best effort           │   │
│  │                                                              │   │
│  │ Scale                                                        │   │
│  │ □ < 100 queries/day  □ 100-10K/day  □ > 10K/day            │   │
│  │                                                              │   │
│  │ Integration Requirements                                     │   │
│  │ □ Must integrate with: _________________________________    │   │
│  │ □ Data sources: ________________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  SECURITY & COMPLIANCE                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ PII handling required (names, emails, phones, etc.)       │   │
│  │ □ Data cannot leave organization (no external LLM)          │   │
│  │ □ Audit logging required                                    │   │
│  │ □ Role-based access control needed                          │   │
│  │ □ Compliance: _________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  RESOURCE CONSTRAINTS                                                │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Budget                                                       │   │
│  │ • Development: $_________ / ___ months                      │   │
│  │ • Monthly operational: $_________ /month                    │   │
│  │                                                              │   │
│  │ Team                                                         │   │
│  │ • Available engineers: ___                                  │   │
│  │ • AI/ML expertise: □ Yes  □ Limited  □ No                  │   │
│  │                                                              │   │
│  │ Timeline                                                     │   │
│  │ • MVP deadline: ___________                                 │   │
│  │ • Production deadline: ___________                          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 1.5 Phase 1 Deliverables Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│              PHASE 1 COMPLETION CHECKLIST                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  □ Problem Definition Canvas completed                              │
│  □ User Analysis Matrix filled out                                  │
│  □ At least 3 user interviews/observations conducted                │
│  □ Success Metrics defined with baselines and targets               │
│  □ Constraints documented and validated with stakeholders           │
│  □ Go/No-Go decision made based on feasibility                      │
│                                                                      │
│  GATE REVIEW QUESTIONS:                                             │
│  □ Is the problem specific enough? (Can be solved in 6-8 weeks?)   │
│  □ Is AI Agent the right solution? (Not just rule-based system?)   │
│  □ Are success metrics measurable?                                  │
│  □ Are constraints realistic given resources?                       │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 2: ARCHITECTURE DESIGN

## 2.1 Agent Pattern Selection

### Decision Framework: Chọn Pattern Phù Hợp

```
┌─────────────────────────────────────────────────────────────────────┐
│                 AGENT PATTERN DECISION TREE                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  START: Phân tích task của bạn                                      │
│    │                                                                 │
│    ▼                                                                 │
│  ┌─────────────────────────────────────────┐                        │
│  │ Task có workflow step-by-step rõ ràng?  │                        │
│  └─────────────────────────────────────────┘                        │
│    │                                                                 │
│    ├── YES ──▶ PATTERN A: Sequential Pipeline                       │
│    │          (Uber's QueryGPT model)                               │
│    │          Input → Step1 → Step2 → Step3 → Output                │
│    │                                                                 │
│    └── NO ───▶ Tiếp tục...                                          │
│                  │                                                   │
│                  ▼                                                   │
│  ┌─────────────────────────────────────────┐                        │
│  │ Có nhiều domain/skill khác nhau?        │                        │
│  └─────────────────────────────────────────┘                        │
│    │                                                                 │
│    ├── YES ──▶ PATTERN B: Supervisor + Sub-Agents                   │
│    │          (Uber's Finch model)                                  │
│    │          Supervisor routes to specialized agents               │
│    │                                                                 │
│    └── NO ───▶ Tiếp tục...                                          │
│                  │                                                   │
│                  ▼                                                   │
│  ┌─────────────────────────────────────────┐                        │
│  │ Có thể parallel processing?             │                        │
│  │ (Không cần human-in-the-loop)           │                        │
│  └─────────────────────────────────────────┘                        │
│    │                                                                 │
│    ├── YES ──▶ PATTERN C: Parallel + Merge                          │
│    │          (Uber's AutoCover model)                              │
│    │          Fan-out → Process in parallel → Merge results         │
│    │                                                                 │
│    └── NO ───▶ PATTERN D: Single Agent + Tools                      │
│               (Simple ReAct pattern)                                │
│               Agent với 1-5 tools                                   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Pattern Details

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PATTERN A: SEQUENTIAL PIPELINE                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  USE WHEN:                                                          │
│  • Task có các bước tuần tự rõ ràng                                 │
│  • Output của bước trước là input của bước sau                      │
│  • Cần validate/transform giữa các bước                             │
│                                                                      │
│  ARCHITECTURE:                                                       │
│  ┌────────┐   ┌────────┐   ┌────────┐   ┌────────┐                 │
│  │ Step 1 │──▶│ Step 2 │──▶│ Step 3 │──▶│ Step 4 │                 │
│  │(Intent)│   │(Enrich)│   │(Generate)  │(Validate)                 │
│  └────────┘   └────────┘   └────────┘   └────────┘                 │
│                                                                      │
│  UBER EXAMPLE: QueryGPT                                             │
│  Intent → Table Selection → Column Pruning → SQL Generation         │
│                                                                      │
│  TYPICAL STEPS:                                                      │
│  1. Intent Classification (LLM)                                     │
│  2. Context Enrichment (RAG/Lookup)                                 │
│  3. Generation (LLM)                                                │
│  4. Validation (Deterministic + LLM)                                │
│  5. Output Formatting (Deterministic)                               │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                 PATTERN B: SUPERVISOR + SUB-AGENTS                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  USE WHEN:                                                          │
│  • Có nhiều domain/skill khác nhau                                  │
│  • Cần routing dựa trên intent                                      │
│  • Mỗi domain có logic xử lý riêng                                  │
│                                                                      │
│  ARCHITECTURE:                                                       │
│                    ┌────────────┐                                   │
│                    │ SUPERVISOR │                                   │
│                    │  (Router)  │                                   │
│                    └────────────┘                                   │
│                          │                                          │
│            ┌─────────────┼─────────────┐                           │
│            ▼             ▼             ▼                            │
│       ┌─────────┐  ┌─────────┐  ┌─────────┐                        │
│       │ Agent A │  │ Agent B │  │ Agent C │                        │
│       │  (SQL)  │  │  (Doc)  │  │ (Chart) │                        │
│       └─────────┘  └─────────┘  └─────────┘                        │
│                                                                      │
│  UBER EXAMPLE: Finch                                                │
│  Supervisor routes to SQL Agent, Document Agent, Chart Agent        │
│                                                                      │
│  KEY COMPONENTS:                                                     │
│  1. Supervisor: Intent classification + routing logic               │
│  2. Sub-Agents: Specialized agents for each domain                  │
│  3. Response Aggregator: Combine results if needed                  │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                   PATTERN C: PARALLEL + MERGE                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  USE WHEN:                                                          │
│  • Cần generate nhiều variations                                    │
│  • Không có human-in-the-loop (cho phép batch)                      │
│  • Cần scale và speed                                               │
│                                                                      │
│  ARCHITECTURE:                                                       │
│                    ┌────────────┐                                   │
│                    │ SCAFFOLDER │                                   │
│                    │  (Prepare) │                                   │
│                    └────────────┘                                   │
│                          │                                          │
│         ┌────────────────┼────────────────┐                        │
│         ▼                ▼                ▼                         │
│    ┌─────────┐     ┌─────────┐     ┌─────────┐                     │
│    │ Gen #1  │     │ Gen #2  │     │ Gen #N  │  (Parallel)         │
│    └─────────┘     └─────────┘     └─────────┘                     │
│         │                │                │                         │
│         └────────────────┼────────────────┘                        │
│                          ▼                                          │
│                    ┌────────────┐                                   │
│                    │   MERGE    │                                   │
│                    │ (Validate) │                                   │
│                    └────────────┘                                   │
│                                                                      │
│  UBER EXAMPLE: AutoCover                                            │
│  Run 100 test generations in parallel, merge best results           │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────┐
│                 PATTERN D: SINGLE AGENT + TOOLS                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  USE WHEN:                                                          │
│  • Task tương đối đơn giản                                          │
│  • Cần flexibility (agent tự quyết định tool nào)                   │
│  • < 5 tools                                                        │
│                                                                      │
│  ARCHITECTURE:                                                       │
│                    ┌────────────┐                                   │
│                    │   AGENT    │                                   │
│                    │  (ReAct)   │                                   │
│                    └────────────┘                                   │
│                          │                                          │
│         ┌────────────────┼────────────────┐                        │
│         ▼                ▼                ▼                         │
│    ┌─────────┐     ┌─────────┐     ┌─────────┐                     │
│    │ Tool 1  │     │ Tool 2  │     │ Tool 3  │                     │
│    │(Search) │     │ (Calc)  │     │  (API)  │                     │
│    └─────────┘     └─────────┘     └─────────┘                     │
│                                                                      │
│  EXAMPLE: Simple Q&A Bot                                            │
│  Agent với Search tool, Calculator tool, API call tool              │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2.2 Component Design

### Template: Component Specification

```
┌─────────────────────────────────────────────────────────────────────┐
│                   COMPONENT SPECIFICATION                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Với mỗi component trong architecture, điền template sau:           │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ COMPONENT NAME: ________________________________________    │   │
│  │                                                              │   │
│  │ TYPE: □ LLM-based  □ Deterministic  □ Hybrid               │   │
│  │                                                              │   │
│  │ PURPOSE:                                                     │   │
│  │ _________________________________________________________   │   │
│  │                                                              │   │
│  │ INPUT:                                                       │   │
│  │ • Data: __________________________________________________  │   │
│  │ • Format: ________________________________________________  │   │
│  │ • Source: ________________________________________________  │   │
│  │                                                              │   │
│  │ OUTPUT:                                                      │   │
│  │ • Data: __________________________________________________  │   │
│  │ • Format: ________________________________________________  │   │
│  │ • Destination: ___________________________________________  │   │
│  │                                                              │   │
│  │ DEPENDENCIES:                                                │   │
│  │ • Upstream: ______________________________________________  │   │
│  │ • Downstream: ____________________________________________  │   │
│  │                                                              │   │
│  │ ERROR HANDLING:                                              │   │
│  │ • Failure mode: __________________________________________  │   │
│  │ • Fallback: ______________________________________________  │   │
│  │                                                              │   │
│  │ PERFORMANCE REQUIREMENTS:                                    │   │
│  │ • Latency: ___ ms/s                                         │   │
│  │ • Throughput: ___ requests/min                              │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### LLM vs Deterministic Decision Matrix

```
┌─────────────────────────────────────────────────────────────────────┐
│              LLM vs DETERMINISTIC DECISION MATRIX                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Task Type                      │ Recommendation │ Why              │
│  ───────────────────────────────│────────────────│──────────────────│
│  Intent classification          │ LLM            │ Natural language │
│  Text generation                │ LLM            │ Creative         │
│  Summarization                  │ LLM            │ Understanding    │
│  Code generation                │ LLM            │ Complex patterns │
│  ───────────────────────────────│────────────────│──────────────────│
│  Format validation              │ Deterministic  │ Known rules      │
│  Calculation                    │ Deterministic  │ Accuracy         │
│  Data transformation            │ Deterministic  │ Predictable      │
│  Regex matching                 │ Deterministic  │ Pattern-based    │
│  API calls                      │ Deterministic  │ Structured I/O   │
│  ───────────────────────────────│────────────────│──────────────────│
│  Entity extraction              │ Hybrid         │ LLM + validate   │
│  SQL generation                 │ Hybrid         │ LLM + syntax chk │
│  Code review                    │ Hybrid         │ LLM + linter     │
│  Document processing            │ Hybrid         │ LLM + parser     │
│                                                                      │
│  RULE OF THUMB:                                                      │
│  • If it can be done with regex/rules → Deterministic               │
│  • If it needs understanding → LLM                                  │
│  • If accuracy is critical → Hybrid (LLM + Deterministic validate) │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2.3 Data Flow Design

### Template: Data Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                     DATA FLOW DIAGRAM                                │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Document data flow từ user input đến final output:                 │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                                                              │   │
│  │  USER INPUT                                                  │   │
│  │  ┌──────────────────────────────────────────────────────┐   │   │
│  │  │ Type: _______________                                 │   │   │
│  │  │ Format: _____________                                 │   │   │
│  │  │ Example: ____________                                 │   │   │
│  │  └──────────────────────────────────────────────────────┘   │   │
│  │                         │                                    │   │
│  │                         ▼                                    │   │
│  │  PREPROCESSING                                               │   │
│  │  ┌──────────────────────────────────────────────────────┐   │   │
│  │  │ □ Validation                                          │   │   │
│  │  │ □ Sanitization                                        │   │   │
│  │  │ □ PII Detection/Redaction                             │   │   │
│  │  │ □ Format normalization                                │   │   │
│  │  └──────────────────────────────────────────────────────┘   │   │
│  │                         │                                    │   │
│  │                         ▼                                    │   │
│  │  CONTEXT ENRICHMENT                                          │   │
│  │  ┌──────────────────────────────────────────────────────┐   │   │
│  │  │ Data Sources:                                         │   │   │
│  │  │ □ Vector DB (RAG): _______________________________   │   │   │
│  │  │ □ Database: ______________________________________   │   │   │
│  │  │ □ API: ___________________________________________   │   │   │
│  │  │ □ Cache: _________________________________________   │   │   │
│  │  └──────────────────────────────────────────────────────┘   │   │
│  │                         │                                    │   │
│  │                         ▼                                    │   │
│  │  AGENT PROCESSING                                            │   │
│  │  ┌──────────────────────────────────────────────────────┐   │   │
│  │  │ [Refer to Architecture Pattern selected]              │   │   │
│  │  └──────────────────────────────────────────────────────┘   │   │
│  │                         │                                    │   │
│  │                         ▼                                    │   │
│  │  POST-PROCESSING                                             │   │
│  │  ┌──────────────────────────────────────────────────────┐   │   │
│  │  │ □ Output validation                                   │   │   │
│  │  │ □ Format transformation                               │   │   │
│  │  │ □ PII un-redaction                                    │   │   │
│  │  │ □ Logging & metrics                                   │   │   │
│  │  └──────────────────────────────────────────────────────┘   │   │
│  │                         │                                    │   │
│  │                         ▼                                    │   │
│  │  FINAL OUTPUT                                                │   │
│  │  ┌──────────────────────────────────────────────────────┐   │   │
│  │  │ Type: _______________                                 │   │   │
│  │  │ Format: _____________                                 │   │   │
│  │  │ Delivery: ___________                                 │   │   │
│  │  └──────────────────────────────────────────────────────┘   │   │
│  │                                                              │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2.4 Technology Stack Selection

### Template: Technology Decision Record

```
┌─────────────────────────────────────────────────────────────────────┐
│                  TECHNOLOGY DECISION RECORD                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  LAYER: LLM ACCESS                                                  │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Options Considered:                                          │   │
│  │ 1. _____________ - Pros: __________ Cons: __________        │   │
│  │ 2. _____________ - Pros: __________ Cons: __________        │   │
│  │ 3. _____________ - Pros: __________ Cons: __________        │   │
│  │                                                              │   │
│  │ DECISION: _____________________________________________     │   │
│  │ RATIONALE: ____________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LAYER: AGENT ORCHESTRATION                                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Options Considered:                                          │   │
│  │ 1. LangGraph - Pros: Flexible, visual Cons: Learning curve  │   │
│  │ 2. AutoGen - Pros: Multi-agent Cons: Complex setup          │   │
│  │ 3. Custom - Pros: Full control Cons: Build from scratch     │   │
│  │                                                              │   │
│  │ DECISION: _____________________________________________     │   │
│  │ RATIONALE: ____________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LAYER: KNOWLEDGE BASE / RAG                                        │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Options Considered:                                          │   │
│  │ 1. _____________ - Pros: __________ Cons: __________        │   │
│  │ 2. _____________ - Pros: __________ Cons: __________        │   │
│  │                                                              │   │
│  │ DECISION: _____________________________________________     │   │
│  │ RATIONALE: ____________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LAYER: BACKEND / API                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ DECISION: _____________________________________________     │   │
│  │ RATIONALE: ____________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LAYER: FRONTEND / INTERFACE                                        │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ DECISION: _____________________________________________     │   │
│  │ RATIONALE: ____________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Quick Reference: Stack by Team Size

```
┌─────────────────────────────────────────────────────────────────────┐
│              RECOMMENDED STACKS BY CONTEXT                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  SOLO / SMALL TEAM (1-3 people, MVP focus)                          │
│  ──────────────────────────────────────────                         │
│  • LLM: OpenAI API (GPT-4o-mini for cost, GPT-4o for quality)      │
│  • Orchestration: LangGraph or simple Python                        │
│  • Vector DB: Chroma (local) or Pinecone (managed)                  │
│  • Backend: FastAPI + Python                                        │
│  • Frontend: Streamlit / Gradio / Slack bot                         │
│  • Hosting: Railway / Render / Vercel                               │
│                                                                      │
│  MEDIUM TEAM (3-10 people, production focus)                        │
│  ─────────────────────────────────────────                          │
│  • LLM: OpenAI + Anthropic (redundancy)                             │
│  • Orchestration: LangGraph + LangSmith (observability)             │
│  • Vector DB: Pinecone / Weaviate / Qdrant                          │
│  • Backend: FastAPI + Redis (caching) + PostgreSQL                  │
│  • Frontend: React / Next.js                                        │
│  • Hosting: AWS / GCP with proper CI/CD                             │
│                                                                      │
│  ENTERPRISE (10+ people, scale focus) - Uber's approach             │
│  ───────────────────────────────────────────────────                │
│  • LLM: Custom Gateway + Multi-provider                             │
│  • Orchestration: Custom framework (like Uber's LangEffect)         │
│  • Vector DB: Elasticsearch / OpenSearch                            │
│  • Backend: Go / Java microservices                                 │
│  • Infrastructure: Kubernetes + Internal ML platform                │
│  • Self-hosted models for sensitive data                            │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 2.5 Phase 2 Deliverables Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│              PHASE 2 COMPLETION CHECKLIST                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  □ Agent Pattern selected với rationale                             │
│  □ Architecture diagram completed                                   │
│  □ All components specified (type, I/O, dependencies)               │
│  □ Data flow documented end-to-end                                  │
│  □ Technology decisions recorded with rationale                     │
│  □ Security considerations addressed                                │
│  □ Cost estimation completed                                        │
│  □ Architecture reviewed by stakeholders                            │
│                                                                      │
│  GATE REVIEW QUESTIONS:                                             │
│  □ Is the architecture simple enough for the team?                  │
│  □ Are there clear interfaces between components?                   │
│  □ Is the tech stack appropriate for constraints?                   │
│  □ Have we considered failure modes?                                │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 3: BUILD & TEST

## 3.1 Development Approach

### Build Order Framework

```
┌─────────────────────────────────────────────────────────────────────┐
│                    BUILD ORDER FRAMEWORK                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PRINCIPLE: Build từ foundation lên, test từng layer                │
│                                                                      │
│  WEEK 1-2: FOUNDATION                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ LLM Gateway/Wrapper                                        │   │
│  │   • Connection to LLM provider(s)                            │   │
│  │   • Basic error handling & retries                           │   │
│  │   • Cost tracking                                            │   │
│  │   • Logging                                                  │   │
│  │                                                              │   │
│  │ □ Data Layer                                                 │   │
│  │   • Vector DB setup (if using RAG)                           │   │
│  │   • Database connections                                     │   │
│  │   • Initial data indexing                                    │   │
│  │                                                              │   │
│  │ MILESTONE: Can send prompt to LLM and get response          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  WEEK 2-3: CORE AGENT                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ First component (usually Intent/Router)                    │   │
│  │ □ Main generation component                                  │   │
│  │ □ Basic validation                                           │   │
│  │ □ Wire components together                                   │   │
│  │                                                              │   │
│  │ MILESTONE: End-to-end flow works for happy path             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  WEEK 3-4: ROBUSTNESS                                               │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Error handling for each component                          │   │
│  │ □ Edge cases handling                                        │   │
│  │ □ Fallback mechanisms                                        │   │
│  │ □ Input validation & sanitization                            │   │
│  │                                                              │   │
│  │ MILESTONE: Agent handles errors gracefully                  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  WEEK 4-5: INTEGRATION & INTERFACE                                  │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ API layer                                                  │   │
│  │ □ User interface                                             │   │
│  │ □ Integration with existing systems                          │   │
│  │ □ Authentication/Authorization                               │   │
│  │                                                              │   │
│  │ MILESTONE: Users can interact with agent                    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  WEEK 5-6: POLISH & OPTIMIZE                                        │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Prompt optimization                                        │   │
│  │ □ Performance tuning                                         │   │
│  │ □ Cost optimization                                          │   │
│  │ □ Monitoring & alerting setup                                │   │
│  │                                                              │   │
│  │ MILESTONE: Ready for production                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 3.2 Prompt Engineering Guidelines

### Template: Prompt Specification

```
┌─────────────────────────────────────────────────────────────────────┐
│                    PROMPT SPECIFICATION                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Với mỗi LLM component, document prompt như sau:                    │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ COMPONENT: ____________________________________________     │   │
│  │                                                              │   │
│  │ PURPOSE: ______________________________________________     │   │
│  │                                                              │   │
│  │ PROMPT STRUCTURE:                                            │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │ SYSTEM PROMPT                                          │  │   │
│  │ │ ───────────────                                        │  │   │
│  │ │ Role: [Định nghĩa vai trò của AI]                      │  │   │
│  │ │ Context: [Background information]                      │  │   │
│  │ │ Task: [Nhiệm vụ cụ thể]                                │  │   │
│  │ │ Constraints: [Giới hạn và rules]                       │  │   │
│  │ │ Output Format: [Format mong muốn]                      │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  │                                                              │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │ USER PROMPT TEMPLATE                                   │  │   │
│  │ │ ────────────────────                                   │  │   │
│  │ │ [Variables to inject: {var1}, {var2}, ...]             │  │   │
│  │ │                                                        │  │   │
│  │ │ Template:                                              │  │   │
│  │ │ ________________________________________________      │  │   │
│  │ │ ________________________________________________      │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  │                                                              │   │
│  │ FEW-SHOT EXAMPLES (nếu cần):                                │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │ Example 1:                                             │  │   │
│  │ │ Input: ___________________________________________    │  │   │
│  │ │ Output: __________________________________________    │  │   │
│  │ │                                                        │  │   │
│  │ │ Example 2:                                             │  │   │
│  │ │ Input: ___________________________________________    │  │   │
│  │ │ Output: __________________________________________    │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  │                                                              │   │
│  │ EXPECTED OUTPUT:                                             │   │
│  │ • Format: □ JSON  □ Text  □ Code  □ Structured             │   │
│  │ • Schema/Example: _____________________________________     │   │
│  │                                                              │   │
│  │ FAILURE MODES:                                               │   │
│  │ • Common failure: ________________ → Mitigation: _______    │   │
│  │ • Common failure: ________________ → Mitigation: _______    │   │
│  │                                                              │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Prompt Best Practices Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│               PROMPT BEST PRACTICES CHECKLIST                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  CLARITY                                                            │
│  □ Role được định nghĩa rõ ràng                                     │
│  □ Task được mô tả cụ thể                                           │
│  □ Output format được specify                                       │
│  □ Không có ambiguity                                               │
│                                                                      │
│  STRUCTURE                                                          │
│  □ Sử dụng sections/headers cho prompts dài                         │
│  □ Sử dụng XML tags hoặc markdown cho structure                     │
│  □ Separate concerns (context vs task vs format)                    │
│                                                                      │
│  EXAMPLES                                                           │
│  □ Có ít nhất 2-3 few-shot examples cho complex tasks              │
│  □ Examples cover edge cases                                        │
│  □ Examples show both good and bad outputs                          │
│                                                                      │
│  CONSTRAINTS                                                        │
│  □ Giới hạn output length nếu cần                                   │
│  □ Specify what NOT to do                                           │
│  □ Define boundaries clearly                                        │
│                                                                      │
│  ROBUSTNESS                                                         │
│  □ Test với nhiều input variations                                  │
│  □ Handle edge cases trong prompt                                   │
│  □ Có fallback instructions                                         │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 3.3 Testing Strategy

### Template: Test Plan

```
┌─────────────────────────────────────────────────────────────────────┐
│                        TEST PLAN                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  LEVEL 1: COMPONENT TESTING                                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Mỗi component được test độc lập:                             │   │
│  │                                                              │   │
│  │ Component: _______________                                   │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │ Test Case │ Input        │ Expected      │ Pass/Fail  │  │   │
│  │ │───────────│──────────────│───────────────│────────────│  │   │
│  │ │ Happy path│              │               │            │  │   │
│  │ │ Edge case1│              │               │            │  │   │
│  │ │ Edge case2│              │               │            │  │   │
│  │ │ Error case│              │               │            │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LEVEL 2: INTEGRATION TESTING                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Test flow giữa các components:                               │   │
│  │                                                              │   │
│  │ Flow: Component A → Component B → Component C               │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │ Scenario        │ Expected Flow    │ Pass/Fail        │  │   │
│  │ │─────────────────│──────────────────│──────────────────│  │   │
│  │ │ Normal flow     │ A → B → C → Out  │                  │  │   │
│  │ │ A fails         │ A → Error        │                  │  │   │
│  │ │ B fails         │ A → B → Fallback │                  │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LEVEL 3: END-TO-END TESTING                                        │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Test từ user input đến final output:                         │   │
│  │                                                              │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │ User Story      │ Input          │ Expected Output    │  │   │
│  │ │─────────────────│────────────────│────────────────────│  │   │
│  │ │                 │                │                    │  │   │
│  │ │                 │                │                    │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LEVEL 4: EVALUATION SET                                            │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Golden dataset để đo accuracy:                               │   │
│  │                                                              │   │
│  │ • Number of test cases: ___ (minimum 50-100)                │   │
│  │ • Coverage: ___ domains/categories                          │   │
│  │ • Ground truth source: ___________________                  │   │
│  │                                                              │   │
│  │ Evaluation Metrics:                                          │   │
│  │ □ Accuracy: ___% (Target: ___%+)                            │   │
│  │ □ Precision: ___%                                           │   │
│  │ □ Recall: ___%                                              │   │
│  │ □ F1 Score: ___%                                            │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### LLM-Specific Testing Considerations

```
┌─────────────────────────────────────────────────────────────────────┐
│              LLM-SPECIFIC TESTING CHECKLIST                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  DETERMINISM                                                        │
│  □ Set temperature = 0 for reproducible tests                       │
│  □ Seed random states where possible                                │
│  □ Accept some variance in outputs (use semantic matching)          │
│                                                                      │
│  HALLUCINATION DETECTION                                            │
│  □ Verify factual claims against ground truth                       │
│  □ Check for made-up entities/data                                  │
│  □ Validate generated code/SQL actually runs                        │
│                                                                      │
│  PROMPT INJECTION TESTING                                           │
│  □ Test with adversarial inputs                                     │
│  □ Try to bypass instructions                                       │
│  □ Test with special characters/formatting                          │
│                                                                      │
│  REGRESSION TESTING                                                 │
│  □ Re-run evaluation set after prompt changes                       │
│  □ Track metrics over time                                          │
│  □ Alert on significant degradation                                 │
│                                                                      │
│  COST MONITORING                                                    │
│  □ Track tokens used per test                                       │
│  □ Set budget limits for test runs                                  │
│  □ Optimize prompts for token efficiency                            │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 3.4 Phase 3 Deliverables Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│              PHASE 3 COMPLETION CHECKLIST                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  □ Foundation layer working (LLM connection, data layer)            │
│  □ Core agent flow working end-to-end                               │
│  □ All prompts documented with specifications                       │
│  □ Error handling implemented                                       │
│  □ Component tests passing                                          │
│  □ Integration tests passing                                        │
│  □ Evaluation set created (50+ cases)                               │
│  □ Accuracy meets minimum threshold (defined in Phase 1)            │
│  □ User interface functional                                        │
│  □ Basic monitoring in place                                        │
│                                                                      │
│  GATE REVIEW QUESTIONS:                                             │
│  □ Does the agent solve the original problem?                       │
│  □ Is accuracy acceptable for users?                                │
│  □ Is cost within budget?                                           │
│  □ Is latency acceptable?                                           │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 4: DEPLOY & ITERATE

## 4.1 Deployment Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                   DEPLOYMENT CHECKLIST                               │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PRE-DEPLOYMENT                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SECURITY                                                     │   │
│  │ □ API keys secured (not in code)                             │   │
│  │ □ PII handling verified                                      │   │
│  │ □ Authentication implemented                                 │   │
│  │ □ Rate limiting configured                                   │   │
│  │ □ Input sanitization in place                                │   │
│  │                                                              │   │
│  │ RELIABILITY                                                  │   │
│  │ □ Error handling tested                                      │   │
│  │ □ Fallback mechanisms working                                │   │
│  │ □ Timeouts configured                                        │   │
│  │ □ Retry logic implemented                                    │   │
│  │                                                              │   │
│  │ OBSERVABILITY                                                │   │
│  │ □ Logging configured                                         │   │
│  │ □ Metrics collection set up                                  │   │
│  │ □ Alerting configured                                        │   │
│  │ □ Dashboard created                                          │   │
│  │                                                              │   │
│  │ DOCUMENTATION                                                │   │
│  │ □ User guide created                                         │   │
│  │ □ API documentation                                          │   │
│  │ □ Runbook for common issues                                  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ROLLOUT STRATEGY                                                   │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Phase 1: Internal team (1 week)                            │   │
│  │   • Scope: ___ users                                         │   │
│  │   • Success criteria: ___                                    │   │
│  │                                                              │   │
│  │ □ Phase 2: Beta users (2 weeks)                              │   │
│  │   • Scope: ___ users                                         │   │
│  │   • Success criteria: ___                                    │   │
│  │                                                              │   │
│  │ □ Phase 3: General availability                              │   │
│  │   • Scope: All target users                                  │   │
│  │   • Success criteria: Match Phase 1 metrics                  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 4.2 Monitoring Framework

### Template: Monitoring Dashboard Spec

```
┌─────────────────────────────────────────────────────────────────────┐
│                 MONITORING DASHBOARD SPEC                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  REAL-TIME METRICS (Update every minute)                            │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ • Requests per minute: ___ (Alert if > ___ or < ___)        │   │
│  │ • Average latency: ___ ms (Alert if > ___ ms)               │   │
│  │ • Error rate: ___% (Alert if > ___%)                        │   │
│  │ • Active users: ___                                         │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  DAILY METRICS                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ • Total queries: ___                                         │   │
│  │ • Unique users: ___                                          │   │
│  │ • Success rate: ___%                                         │   │
│  │ • Total cost: $___                                           │   │
│  │ • Cost per query: $___                                       │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  QUALITY METRICS (Weekly review)                                    │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ • User satisfaction (from feedback): ___/5                   │   │
│  │ • Accuracy (from sampling): ___%                             │   │
│  │ • Feature adoption: ___%                                     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ALERTS                                                             │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Level    │ Condition              │ Action                  │   │
│  │──────────│────────────────────────│─────────────────────────│   │
│  │ Critical │ Error rate > 10%       │ Page on-call            │   │
│  │ Critical │ Latency > 30s          │ Page on-call            │   │
│  │ Warning  │ Cost > 150% budget     │ Slack alert             │   │
│  │ Info     │ New user milestone     │ Slack notification      │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 4.3 Feedback & Iteration Loop

### Template: Feedback Collection

```
┌─────────────────────────────────────────────────────────────────────┐
│                  FEEDBACK COLLECTION PLAN                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  IN-APP FEEDBACK                                                    │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Thumbs up/down on each response                            │   │
│  │ □ Optional comment field                                     │   │
│  │ □ "Report issue" button                                      │   │
│  │ □ Rating prompt after X interactions                         │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  PERIODIC SURVEYS                                                   │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Frequency: □ Weekly  □ Bi-weekly  □ Monthly                 │   │
│  │                                                              │   │
│  │ Questions:                                                   │   │
│  │ 1. How often do you use [Agent]? ___                        │   │
│  │ 2. How accurate are the results? (1-5) ___                  │   │
│  │ 3. How much time does it save you? ___                      │   │
│  │ 4. What's the biggest issue? ___                            │   │
│  │ 5. What feature would you like? ___                         │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  USER INTERVIEWS                                                    │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Frequency: □ Weekly  □ Bi-weekly  □ Monthly                 │   │
│  │ Number of users: ___ per cycle                              │   │
│  │ Format: □ 1-on-1  □ Group  □ Observation                    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  AUTOMATED QUALITY SAMPLING                                         │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Random sample ___% of queries daily                        │   │
│  │ □ Manual review by team member                               │   │
│  │ □ LLM-as-judge for automated scoring                         │   │
│  │ □ Track accuracy trend over time                             │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Iteration Prioritization Framework

```
┌─────────────────────────────────────────────────────────────────────┐
│              ITERATION PRIORITIZATION MATRIX                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│                        IMPACT                                        │
│                 Low            High                                  │
│              ┌─────────────┬─────────────┐                          │
│              │             │             │                          │
│         Low  │   IGNORE    │  SCHEDULE   │                          │
│              │             │   (Batch)   │                          │
│   EFFORT     ├─────────────┼─────────────┤                          │
│              │             │             │                          │
│         High │   IGNORE    │  PRIORITIZE │                          │
│              │             │   (Sprint)  │                          │
│              └─────────────┴─────────────┘                          │
│                                                                      │
│  ITERATION BACKLOG TEMPLATE:                                        │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Item          │ Source   │ Impact │ Effort │ Priority      │   │
│  │───────────────│──────────│────────│────────│───────────────│   │
│  │               │ Feedback │ H/M/L  │ H/M/L  │ P0/P1/P2      │   │
│  │               │ Metrics  │        │        │               │   │
│  │               │ Bug      │        │        │               │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ITERATION CADENCE:                                                 │
│  □ Weekly: Bug fixes, prompt tweaks                                 │
│  □ Bi-weekly: Small features, optimizations                         │
│  □ Monthly: Major features, architecture changes                    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 4.4 Scaling Considerations

```
┌─────────────────────────────────────────────────────────────────────┐
│                  SCALING CHECKLIST                                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  WHEN TO SCALE (Triggers)                                           │
│  □ Consistent >80% capacity utilization                             │
│  □ Latency degradation >20%                                         │
│  □ User complaints about speed                                      │
│  □ Planned user growth >2x                                          │
│                                                                      │
│  SCALING STRATEGIES                                                 │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ COST OPTIMIZATION (First priority)                           │   │
│  │ □ Implement caching for common queries                       │   │
│  │ □ Use smaller/cheaper models where possible                  │   │
│  │ □ Optimize prompts for fewer tokens                          │   │
│  │ □ Batch similar requests                                     │   │
│  │                                                              │   │
│  │ PERFORMANCE OPTIMIZATION                                     │   │
│  │ □ Add response caching                                       │   │
│  │ □ Implement async processing                                 │   │
│  │ □ Parallelize independent components                         │   │
│  │ □ Optimize RAG retrieval                                     │   │
│  │                                                              │   │
│  │ INFRASTRUCTURE SCALING                                       │   │
│  │ □ Horizontal scaling (more instances)                        │   │
│  │ □ Load balancing                                             │   │
│  │ □ Multi-region deployment                                    │   │
│  │ □ Consider self-hosted models for high volume                │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  REUSABILITY (Uber's approach)                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ □ Extract common components as shared libraries              │   │
│  │ □ Create templates for new agents                            │   │
│  │ □ Document patterns and best practices                       │   │
│  │ □ Build internal framework (like Uber's LangEffect)          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# APPENDIX

## A. Quick Reference Cards

### Card 1: Agent Pattern Quick Reference

```
┌─────────────────────────────────────────────────────────────────────┐
│              AGENT PATTERN QUICK REFERENCE                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Sequential Pipeline │ Supervisor + Agents │ Parallel + Merge       │
│  ────────────────────│─────────────────────│──────────────────────  │
│  Step-by-step flow   │ Multi-domain/skill  │ Batch generation       │
│  Clear dependencies  │ Need routing        │ No human-in-loop       │
│  Each step refines   │ Specialized agents  │ Scale important        │
│                      │                     │                        │
│  Example:            │ Example:            │ Example:               │
│  Text-to-SQL         │ Multi-skill bot     │ Test generation        │
│  Document processing │ Customer support    │ Content generation     │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Card 2: Hybrid Architecture Quick Reference

```
┌─────────────────────────────────────────────────────────────────────┐
│              HYBRID ARCHITECTURE QUICK REFERENCE                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  USE LLM FOR:                    USE DETERMINISTIC FOR:             │
│  ─────────────                   ─────────────────────              │
│  • Understanding intent          • Validation (format, syntax)      │
│  • Classification                • Calculation                      │
│  • Generation                    • Data transformation              │
│  • Summarization                 • API calls                        │
│  • Reasoning                     • Rule-based checks                │
│                                                                      │
│  PATTERN: LLM generates → Deterministic validates → LLM refines    │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## B. Common Pitfalls & Solutions

```
┌─────────────────────────────────────────────────────────────────────┐
│                  COMMON PITFALLS & SOLUTIONS                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PITFALL                          │ SOLUTION                        │
│  ─────────────────────────────────│─────────────────────────────────│
│  Building too broad initially     │ Start with narrow, specific     │
│                                   │ problem; expand later           │
│  ─────────────────────────────────│─────────────────────────────────│
│  100% LLM (no deterministic)      │ Use hybrid: LLM + validation    │
│                                   │ Deterministic where possible    │
│  ─────────────────────────────────│─────────────────────────────────│
│  No evaluation set                │ Create 50+ golden test cases    │
│                                   │ before building                 │
│  ─────────────────────────────────│─────────────────────────────────│
│  Ignoring cost until too late     │ Track cost from day 1           │
│                                   │ Set budgets and alerts          │
│  ─────────────────────────────────│─────────────────────────────────│
│  Complex prompts from start       │ Start simple, iterate           │
│                                   │ Add complexity as needed        │
│  ─────────────────────────────────│─────────────────────────────────│
│  No user feedback loop            │ Build feedback into UI          │
│                                   │ Review samples weekly           │
│  ─────────────────────────────────│─────────────────────────────────│
│  Hallucination not handled        │ Add validation step             │
│                                   │ Use RAG for facts               │
│                                   │ Human-in-loop for critical      │
│  ─────────────────────────────────│─────────────────────────────────│
│  No fallback when LLM fails       │ Always have graceful fallback   │
│                                   │ Don't fail silently             │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## C. Uber Case Study Summary

```
┌─────────────────────────────────────────────────────────────────────┐
│                  UBER AI AGENT CASE STUDY                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  AGENTS BUILT:                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ Agent      │ Pattern            │ Impact                    │   │
│  │────────────│────────────────────│───────────────────────────│   │
│  │ QueryGPT   │ Sequential Pipeline│ 140K hours/month saved    │   │
│  │ AutoCover  │ Parallel + Merge   │ 21K dev hours saved       │   │
│  │ Validator  │ Hybrid (LLM+Lint)  │ Real-time IDE security    │   │
│  │ Finch      │ Supervisor+Agents  │ Slack-based finance Q&A   │   │
│  │ Genie      │ RAG + Agentic      │ 13K hours/month saved     │   │
│  │ uReview    │ Prompt Chaining    │ 65K diffs/week reviewed   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  KEY SUCCESS FACTORS:                                               │
│  1. GenAI Gateway as unified infrastructure                         │
│  2. Hybrid architecture (LLM + Deterministic)                       │
│  3. Domain-specific agents > Generic                                │
│  4. Reusable components (LangEffect framework)                      │
│  5. Clear metrics and measurement                                   │
│                                                                      │
│  TECHNOLOGY STACK:                                                  │
│  • Orchestration: LangGraph + LangEffect (internal)                 │
│  • LLM: Multi-provider (OpenAI, Google, Self-hosted)               │
│  • Vector DB: SIA (internal), OpenSearch                           │
│  • Infrastructure: Kubernetes, NVIDIA A100                          │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## D. Glossary

```
┌─────────────────────────────────────────────────────────────────────┐
│                        GLOSSARY                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Agent: Hệ thống AI có thể tự động thực hiện tasks bằng cách        │
│         reasoning và sử dụng tools                                  │
│                                                                      │
│  RAG (Retrieval-Augmented Generation): Kỹ thuật bổ sung context     │
│         từ knowledge base vào LLM prompt                            │
│                                                                      │
│  LangGraph: Framework để build stateful, multi-agent applications   │
│                                                                      │
│  Hybrid Architecture: Kết hợp LLM và deterministic components       │
│                                                                      │
│  Few-shot Learning: Cung cấp examples trong prompt để guide LLM     │
│                                                                      │
│  Prompt Chaining: Kết nối nhiều LLM calls theo sequence             │
│                                                                      │
│  Human-in-the-loop: Có người review/approve trong workflow          │
│                                                                      │
│  Hallucination: LLM tạo ra thông tin không chính xác/bịa đặt       │
│                                                                      │
│  Gateway: Service trung gian để access LLM providers                │
│                                                                      │
│  Evaluation Set: Tập test cases với ground truth để đo accuracy     │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# CHECKLIST TỔNG HỢP

```
┌─────────────────────────────────────────────────────────────────────┐
│               MASTER CHECKLIST - AI AGENT PROJECT                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PHASE 1: DISCOVERY (Week 1-2)                                      │
│  □ Problem Definition Canvas                                        │
│  □ User Analysis Matrix                                             │
│  □ Success Metrics Framework                                        │
│  □ Constraints Checklist                                            │
│  □ Go/No-Go Decision                                                │
│                                                                      │
│  PHASE 2: ARCHITECTURE (Week 2-3)                                   │
│  □ Pattern Selection (with rationale)                               │
│  □ Component Specifications                                         │
│  □ LLM vs Deterministic decisions                                   │
│  □ Data Flow Diagram                                                │
│  □ Technology Stack Decision Record                                 │
│  □ Architecture Review                                              │
│                                                                      │
│  PHASE 3: BUILD & TEST (Week 3-6)                                   │
│  □ Foundation Layer (Gateway, Data)                                 │
│  □ Core Agent Components                                            │
│  □ Prompt Specifications                                            │
│  □ Error Handling & Fallbacks                                       │
│  □ Test Plan Execution                                              │
│  □ Evaluation Set & Accuracy Check                                  │
│  □ User Interface                                                   │
│                                                                      │
│  PHASE 4: DEPLOY & ITERATE (Week 6+)                                │
│  □ Deployment Checklist                                             │
│  □ Monitoring Dashboard                                             │
│  □ Feedback Collection Setup                                        │
│  □ Rollout Execution                                                │
│  □ First Iteration Cycle                                            │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

**Document Version:** 1.0
**Based on:** Uber AI Agent Ecosystem Research (2024-2025)
**Intended Use:** Reference guide for AI-assisted product development