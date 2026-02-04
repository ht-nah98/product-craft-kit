# 🚀 PRODUCT BUILDING METHODOLOGY
## Quy Trình Chuẩn Hóa Xây Dựng Sản Phẩm
### Tổng hợp từ: Double Diamond, Lean Startup, Shape Up, Agile & Industry Best Practices

---

## 📋 MỤC ĐÍCH TÀI LIỆU

Đây là **methodology chuẩn hóa** để xây dựng bất kỳ sản phẩm nào:
- **Software products** (Web, Mobile, Desktop)
- **AI-powered products** (AI Agents, ML systems, Chatbots)
- **Platform products** (Marketplaces, SaaS)
- **Internal tools** (Dashboards, Automation)
- **Hardware + Software** (IoT, Embedded)

Tài liệu được thiết kế để:
- AI models có thể đọc hiểu và hướng dẫn người dùng
- Có templates cụ thể cho từng phase
- Linh hoạt customize theo context dự án
- Tích hợp được nhiều methodologies (Agile, Lean, Shape Up...)

---

## 🎯 TRIẾT LÝ CỐT LÕI

### The 5 Product Truths

```
┌─────────────────────────────────────────────────────────────────────┐
│                     5 PRODUCT TRUTHS                                 │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  1. PROBLEM FIRST, SOLUTION SECOND                                  │
│     "Fall in love with the problem, not the solution"               │
│     → Hiểu sâu vấn đề trước khi nghĩ đến giải pháp                 │
│                                                                      │
│  2. BUILD → MEASURE → LEARN                                         │
│     "The goal is validated learning, not shipping features"         │
│     → Mục tiêu là học hỏi được điều gì đó, không phải ship feature │
│                                                                      │
│  3. USERS OVER FEATURES                                             │
│     "No one cares about your product, they care about themselves"   │
│     → Users quan tâm đến vấn đề của họ, không phải sản phẩm của bạn│
│                                                                      │
│  4. SMALL BETS, FAST LEARNING                                       │
│     "Reduce risk through rapid iteration, not extensive planning"   │
│     → Giảm rủi ro bằng iterate nhanh, không phải plan chi tiết     │
│                                                                      │
│  5. SHIP TO LEARN, NOT TO FINISH                                    │
│     "Real learning starts after users interact with your product"   │
│     → Ship để học, không phải để hoàn thành                        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📊 TỔNG QUAN QUY TRÌNH

### The Product Building Lifecycle

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      PRODUCT BUILDING LIFECYCLE                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│                         PROBLEM SPACE          SOLUTION SPACE               │
│                    ┌──────────────────────┐ ┌──────────────────────┐        │
│                    │     DIAMOND 1        │ │     DIAMOND 2        │        │
│                    │                      │ │                      │        │
│           DIVERGE  │    ╱╲                │ │        ╱╲            │ DIVERGE│
│                    │   ╱  ╲               │ │       ╱  ╲           │        │
│                    │  ╱    ╲              │ │      ╱    ╲          │        │
│                    │ ╱      ╲             │ │     ╱      ╲         │        │
│          CONVERGE  │╱        ╲            │ │    ╱        ╲        │CONVERGE│
│                    │          ╲           │ │   ╱          ╲       │        │
│                    │           ╲          │ │  ╱            ╲      │        │
│                    │            ╲         │ │ ╱              ╲     │        │
│                    │             ╲        │ │╱                ╲    │        │
│                    └──────────────────────┘ └──────────────────────┘        │
│                                                                              │
│   PHASE 1         PHASE 2         PHASE 3         PHASE 4         PHASE 5  │
│  ┌────────┐      ┌────────┐      ┌────────┐      ┌────────┐      ┌────────┐│
│  │DISCOVER│  →   │ DEFINE │  →   │DEVELOP │  →   │DELIVER │  →   │ SCALE  ││
│  └────────┘      └────────┘      └────────┘      └────────┘      └────────┘│
│                                                                              │
│  "Understand"    "Focus"         "Explore"       "Ship"          "Grow"    │
│  the problem     the problem     solutions       & Learn         & Iterate │
│                                                                              │
│  Week 1-2        Week 2-3        Week 3-6        Week 6-8        Ongoing   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Phase Summary

| Phase | Mindset | Key Question | Output |
|-------|---------|--------------|--------|
| **1. Discover** | Divergent | "What's really going on?" | Research insights |
| **2. Define** | Convergent | "What problem to solve?" | Problem statement |
| **3. Develop** | Divergent | "How might we solve it?" | Solution options |
| **4. Deliver** | Convergent | "Does it actually work?" | MVP + Learnings |
| **5. Scale** | Iterative | "How do we grow?" | Product-Market Fit |

---

# PHASE 1: DISCOVER
## "Understand the problem space"

### 1.1 Mục tiêu Phase này

```
┌─────────────────────────────────────────────────────────────────────┐
│                    DISCOVER PHASE GOALS                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ✓ Hiểu sâu về users và context của họ                             │
│  ✓ Khám phá pain points thực sự (không phải giả định)              │
│  ✓ Thu thập insights từ nhiều nguồn                                 │
│  ✓ Tránh "solution bias" - đừng nghĩ về giải pháp                  │
│                                                                      │
│  OUTPUT: Research insights & opportunity areas                      │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 1.2 Template: Discovery Research Plan

```
┌─────────────────────────────────────────────────────────────────────┐
│                   DISCOVERY RESEARCH PLAN                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PROJECT: ________________________________________________         │
│  DATE: _______________                                              │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 1. RESEARCH OBJECTIVES                                       │   │
│  │                                                              │   │
│  │ What do we want to learn?                                    │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │                                                              │   │
│  │ What assumptions do we need to validate?                     │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 2. TARGET USERS                                              │   │
│  │                                                              │   │
│  │ Primary user segment: _________________________________      │   │
│  │ Number of users to research: ___                            │   │
│  │ How to recruit: ________________________________________    │   │
│  │                                                              │   │
│  │ User characteristics:                                        │   │
│  │ • Role/Job: ___________________________________________     │   │
│  │ • Experience level: ___________________________________     │   │
│  │ • Current tools: ______________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 3. RESEARCH METHODS                                          │   │
│  │                                                              │   │
│  │ □ User Interviews (_____ sessions)                          │   │
│  │   Focus: _______________________________________________    │   │
│  │                                                              │   │
│  │ □ Observation / Job Shadowing (_____ sessions)              │   │
│  │   Focus: _______________________________________________    │   │
│  │                                                              │   │
│  │ □ Survey (target _____ responses)                           │   │
│  │   Distribution: ________________________________________    │   │
│  │                                                              │   │
│  │ □ Data Analysis                                              │   │
│  │   Data sources: ________________________________________    │   │
│  │                                                              │   │
│  │ □ Competitor Analysis                                        │   │
│  │   Competitors: _________________________________________    │   │
│  │                                                              │   │
│  │ □ Market Research                                            │   │
│  │   Sources: _____________________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 4. TIMELINE                                                  │   │
│  │                                                              │   │
│  │ Research period: ______ to ______                           │   │
│  │ Analysis period: ______ to ______                           │   │
│  │ Synthesis deadline: ______                                   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 1.3 Template: User Interview Guide

```
┌─────────────────────────────────────────────────────────────────────┐
│                    USER INTERVIEW GUIDE                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  OPENING (5 min)                                                    │
│  ─────────────────                                                  │
│  "Thanks for taking the time. I'm researching [topic] and would    │
│  love to learn about your experience. There are no right or wrong  │
│  answers - I'm just trying to understand how things work for you." │
│                                                                      │
│  CONTEXT QUESTIONS (10 min)                                         │
│  ──────────────────────────                                         │
│  1. Tell me about your role and what you do day-to-day?            │
│  2. Walk me through a typical [relevant activity]?                  │
│  3. What tools/processes do you currently use for [activity]?      │
│                                                                      │
│  PAIN POINT EXPLORATION (15 min)                                    │
│  ───────────────────────────────                                    │
│  4. What's the most frustrating part of [activity]?                │
│  5. Can you tell me about a recent time when [activity] was        │
│     particularly difficult?                                         │
│  6. What happens when [activity] goes wrong?                        │
│  7. How much time/money does [problem] cost you?                    │
│                                                                      │
│  CURRENT SOLUTIONS (10 min)                                         │
│  ──────────────────────────                                         │
│  8. How do you currently deal with [problem]?                       │
│  9. Have you tried any solutions? What worked/didn't work?         │
│  10. What would an ideal solution look like for you?                │
│                                                                      │
│  PRIORITIZATION (5 min)                                             │
│  ─────────────────────                                              │
│  11. If you could wave a magic wand and fix one thing about        │
│      [activity], what would it be?                                  │
│  12. How would your work/life change if [problem] was solved?      │
│                                                                      │
│  CLOSING (5 min)                                                    │
│  ──────────────                                                     │
│  "Is there anything else about [topic] that I should have asked?"  │
│  "Can you recommend anyone else I should talk to?"                  │
│                                                                      │
│  NOTES TO SELF:                                                     │
│  • Listen more than you talk (aim for 80/20)                       │
│  • Ask "why" and "tell me more" frequently                         │
│  • Watch for emotional reactions                                    │
│  • Don't pitch solutions - just understand                         │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 1.4 Template: Research Synthesis

```
┌─────────────────────────────────────────────────────────────────────┐
│                    RESEARCH SYNTHESIS                                │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  DATE: _______________   RESEARCHER: _____________________          │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ RESEARCH COMPLETED                                           │   │
│  │                                                              │   │
│  │ • User interviews: _____ completed                          │   │
│  │ • Survey responses: _____ collected                         │   │
│  │ • Observation sessions: _____ completed                     │   │
│  │ • Other: _______________________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ KEY INSIGHTS (Top 5)                                         │   │
│  │                                                              │   │
│  │ 1. ______________________________________________________   │   │
│  │    Evidence: ____________________________________________   │   │
│  │    Frequency: ___ out of ___ users mentioned this           │   │
│  │                                                              │   │
│  │ 2. ______________________________________________________   │   │
│  │    Evidence: ____________________________________________   │   │
│  │    Frequency: ___ out of ___ users mentioned this           │   │
│  │                                                              │   │
│  │ 3. ______________________________________________________   │   │
│  │    Evidence: ____________________________________________   │   │
│  │    Frequency: ___ out of ___ users mentioned this           │   │
│  │                                                              │   │
│  │ 4. ______________________________________________________   │   │
│  │    Evidence: ____________________________________________   │   │
│  │    Frequency: ___ out of ___ users mentioned this           │   │
│  │                                                              │   │
│  │ 5. ______________________________________________________   │   │
│  │    Evidence: ____________________________________________   │   │
│  │    Frequency: ___ out of ___ users mentioned this           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ USER QUOTES (Most impactful)                                 │   │
│  │                                                              │   │
│  │ "[__________________________________________________]"      │   │
│  │  - User role/context                                         │   │
│  │                                                              │   │
│  │ "[__________________________________________________]"      │   │
│  │  - User role/context                                         │   │
│  │                                                              │   │
│  │ "[__________________________________________________]"      │   │
│  │  - User role/context                                         │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ OPPORTUNITY AREAS                                            │   │
│  │                                                              │   │
│  │ Based on research, potential opportunity areas include:      │   │
│  │                                                              │   │
│  │ 1. ______________________________________________________   │   │
│  │ 2. ______________________________________________________   │   │
│  │ 3. ______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SURPRISES & UNEXPECTED FINDINGS                              │   │
│  │                                                              │   │
│  │ What did we learn that we didn't expect?                     │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 1.5 Phase 1 Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                PHASE 1 COMPLETION CHECKLIST                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  □ Research plan created                                            │
│  □ At least 5 user interviews conducted                             │
│  □ Competitor analysis completed                                    │
│  □ Data/analytics reviewed (if available)                           │
│  □ Research synthesis document completed                            │
│  □ Key insights identified and prioritized                          │
│  □ Opportunity areas documented                                     │
│  □ Team alignment on findings                                       │
│                                                                      │
│  GATE QUESTIONS:                                                    │
│  □ Do we have enough evidence to understand the problem?            │
│  □ Did we talk to real users (not just stakeholders)?               │
│  □ Are we confident we understand the root cause?                   │
│  □ Did we resist jumping to solutions?                              │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 2: DEFINE
## "Focus on the right problem"

### 2.1 Mục tiêu Phase này

```
┌─────────────────────────────────────────────────────────────────────┐
│                     DEFINE PHASE GOALS                               │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ✓ Chọn một problem cụ thể để solve                                │
│  ✓ Define problem statement rõ ràng                                 │
│  ✓ Xác định success metrics                                        │
│  ✓ Set "appetite" - bao nhiêu effort sẵn sàng bỏ ra               │
│                                                                      │
│  OUTPUT: Clear problem statement + success criteria                 │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.2 Template: Problem Prioritization Matrix

```
┌─────────────────────────────────────────────────────────────────────┐
│               PROBLEM PRIORITIZATION MATRIX                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  List problems from Discovery phase and score each:                 │
│                                                                      │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │                                                               │  │
│  │  Problem   │ User    │ Business │ Feasibility │ Score │ Rank │  │
│  │            │ Impact  │ Impact   │             │       │      │  │
│  │            │ (1-5)   │ (1-5)    │ (1-5)       │       │      │  │
│  │────────────│─────────│──────────│─────────────│───────│──────│  │
│  │            │         │          │             │       │      │  │
│  │ Problem 1  │   ___   │   ___    │    ___      │ ___   │ ___  │  │
│  │            │         │          │             │       │      │  │
│  │ Problem 2  │   ___   │   ___    │    ___      │ ___   │ ___  │  │
│  │            │         │          │             │       │      │  │
│  │ Problem 3  │   ___   │   ___    │    ___      │ ___   │ ___  │  │
│  │            │         │          │             │       │      │  │
│  │ Problem 4  │   ___   │   ___    │    ___      │ ___   │ ___  │  │
│  │            │         │          │             │       │      │  │
│  │ Problem 5  │   ___   │   ___    │    ___      │ ___   │ ___  │  │
│  │            │         │          │             │       │      │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                                                                      │
│  SCORING GUIDE:                                                     │
│                                                                      │
│  User Impact:     1 = Nice to have    5 = Critical pain            │
│  Business Impact: 1 = Low value       5 = High strategic value     │
│  Feasibility:     1 = Very hard       5 = Relatively easy          │
│                                                                      │
│  Score = User Impact × Business Impact × Feasibility                │
│                                                                      │
│  SELECTED PROBLEM: ____________________________________________     │
│                                                                      │
│  WHY THIS PROBLEM?                                                  │
│  _________________________________________________________________  │
│  _________________________________________________________________  │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.3 Template: Problem Statement Canvas

```
┌─────────────────────────────────────────────────────────────────────┐
│                   PROBLEM STATEMENT CANVAS                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PROJECT NAME: ________________________________________________    │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ THE PROBLEM STATEMENT                                        │   │
│  │ (Use this format)                                            │   │
│  │                                                              │   │
│  │ ┌────────────────────────────────────────────────────────┐  │   │
│  │ │                                                        │  │   │
│  │ │  [WHO - target user]                                   │  │   │
│  │ │  needs a way to [DO WHAT - job to be done]            │  │   │
│  │ │  because [WHY - insight from research]                │  │   │
│  │ │                                                        │  │   │
│  │ │  Currently, they [CURRENT BEHAVIOR]                   │  │   │
│  │ │  which causes [PAIN/COST]                             │  │   │
│  │ │                                                        │  │   │
│  │ └────────────────────────────────────────────────────────┘  │   │
│  │                                                              │   │
│  │ EXAMPLE:                                                     │   │
│  │ "Operations analysts need a way to query business data      │   │
│  │ because they lack SQL skills but need quick answers.        │   │
│  │ Currently, they submit tickets to data team which takes     │   │
│  │ 2-3 days, causing delayed decisions and frustration."       │   │
│  │                                                              │   │
│  │ YOUR PROBLEM STATEMENT:                                      │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ "HOW MIGHT WE" QUESTIONS                                     │   │
│  │                                                              │   │
│  │ Reframe problem as opportunity:                              │   │
│  │                                                              │   │
│  │ HMW _____________________________________________________?  │   │
│  │ HMW _____________________________________________________?  │   │
│  │ HMW _____________________________________________________?  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ NOT IN SCOPE                                                 │   │
│  │                                                              │   │
│  │ What are we explicitly NOT solving?                          │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.4 Template: Success Metrics Definition

```
┌─────────────────────────────────────────────────────────────────────┐
│                   SUCCESS METRICS DEFINITION                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PRIMARY SUCCESS METRIC (The ONE metric that matters most)   │   │
│  │                                                              │   │
│  │ Metric: _________________________________________________   │   │
│  │ Current baseline: _______________________________________   │   │
│  │ Target: _________________________________________________   │   │
│  │ Timeframe: ______________________________________________   │   │
│  │ How to measure: _________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SECONDARY METRICS (Supporting indicators)                    │   │
│  │                                                              │   │
│  │ User Metrics:                                                │   │
│  │ • _________________________ Baseline: ___ Target: ___       │   │
│  │ • _________________________ Baseline: ___ Target: ___       │   │
│  │                                                              │   │
│  │ Business Metrics:                                            │   │
│  │ • _________________________ Baseline: ___ Target: ___       │   │
│  │ • _________________________ Baseline: ___ Target: ___       │   │
│  │                                                              │   │
│  │ Quality Metrics:                                             │   │
│  │ • _________________________ Baseline: ___ Target: ___       │   │
│  │ • _________________________ Baseline: ___ Target: ___       │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ GUARDRAIL METRICS (Things we don't want to break)           │   │
│  │                                                              │   │
│  │ • _________________________ Must stay above: ___            │   │
│  │ • _________________________ Must stay below: ___            │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ MINIMUM SUCCESS CRITERIA                                     │   │
│  │                                                              │   │
│  │ What's the MINIMUM outcome that would make this worth it?   │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.5 Template: Appetite & Constraints (Shape Up style)

```
┌─────────────────────────────────────────────────────────────────────┐
│                   APPETITE & CONSTRAINTS                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ APPETITE (How much are we willing to invest?)               │   │
│  │                                                              │   │
│  │ Time budget:                                                 │   │
│  │ □ Small batch: 1-2 weeks                                    │   │
│  │ □ Medium batch: 3-4 weeks                                   │   │
│  │ □ Big batch: 5-6 weeks                                      │   │
│  │                                                              │   │
│  │ Team size: ___ people                                       │   │
│  │                                                              │   │
│  │ Budget (if applicable): $___                                │   │
│  │                                                              │   │
│  │ RATIONALE for this appetite:                                │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ CONSTRAINTS                                                  │   │
│  │                                                              │   │
│  │ Technical:                                                   │   │
│  │ □ Must integrate with: _________________________________    │   │
│  │ □ Must use technology: _________________________________    │   │
│  │ □ Performance requirement: _____________________________    │   │
│  │                                                              │   │
│  │ Business:                                                    │   │
│  │ □ Must launch by: ______________________________________    │   │
│  │ □ Must not exceed cost: ________________________________    │   │
│  │ □ Must comply with: ____________________________________    │   │
│  │                                                              │   │
│  │ Team:                                                        │   │
│  │ □ Available skills: ____________________________________    │   │
│  │ □ Skill gaps: __________________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ FIXED vs VARIABLE                                            │   │
│  │                                                              │   │
│  │ In Shape Up style, TIME is FIXED, SCOPE is VARIABLE        │   │
│  │                                                              │   │
│  │ This means: If we can't finish everything in the time       │   │
│  │ budget, we CUT SCOPE, not extend time.                      │   │
│  │                                                              │   │
│  │ Agreement: □ Yes, we commit to fixed time, variable scope   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 2.6 Phase 2 Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                PHASE 2 COMPLETION CHECKLIST                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  □ Problems prioritized with clear rationale                        │
│  □ Single problem selected to focus on                              │
│  □ Problem statement written (WHO/WHAT/WHY format)                  │
│  □ "How might we" questions generated                               │
│  □ Success metrics defined with baselines and targets               │
│  □ Appetite set (time/team/budget)                                  │
│  □ Constraints documented                                           │
│  □ Scope boundaries clear (what's NOT included)                     │
│  □ Stakeholder alignment achieved                                   │
│                                                                      │
│  GATE QUESTIONS:                                                    │
│  □ Is the problem specific enough to solve in the appetite?         │
│  □ Can we measure success?                                          │
│  □ Do stakeholders agree this is the right problem?                 │
│  □ Is the team excited about this problem?                          │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 3: DEVELOP
## "Explore solution options"

### 3.1 Mục tiêu Phase này

```
┌─────────────────────────────────────────────────────────────────────┐
│                     DEVELOP PHASE GOALS                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ✓ Generate nhiều solution options (divergent thinking)            │
│  ✓ Evaluate và chọn approach tốt nhất                              │
│  ✓ Design solution ở mức "shaped" (not too abstract, not too detailed)│
│  ✓ Identify risks và unknowns                                       │
│                                                                      │
│  OUTPUT: Shaped solution ready for building                         │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 3.2 Template: Solution Brainstorming

```
┌─────────────────────────────────────────────────────────────────────┐
│                   SOLUTION BRAINSTORMING                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PROBLEM: ____________________________________________________     │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ BRAINSTORM RULES                                             │   │
│  │ • Quantity over quality                                      │   │
│  │ • No judgment during brainstorm                              │   │
│  │ • Build on others' ideas                                     │   │
│  │ • Encourage wild ideas                                       │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SOLUTION OPTIONS                                             │   │
│  │                                                              │   │
│  │ Option 1: _______________________________________________   │   │
│  │ Brief description: ______________________________________   │   │
│  │                                                              │   │
│  │ Option 2: _______________________________________________   │   │
│  │ Brief description: ______________________________________   │   │
│  │                                                              │   │
│  │ Option 3: _______________________________________________   │   │
│  │ Brief description: ______________________________________   │   │
│  │                                                              │   │
│  │ Option 4: _______________________________________________   │   │
│  │ Brief description: ______________________________________   │   │
│  │                                                              │   │
│  │ Option 5: _______________________________________________   │   │
│  │ Brief description: ______________________________________   │   │
│  │                                                              │   │
│  │ "Crazy" option: _________________________________________   │   │
│  │ Brief description: ______________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ INSPIRATION SOURCES                                          │   │
│  │                                                              │   │
│  │ □ How do competitors solve this?                            │   │
│  │ □ How do other industries solve similar problems?           │   │
│  │ □ What would we do with unlimited resources?                │   │
│  │ □ What's the simplest possible solution?                    │   │
│  │ □ What would an AI/automation approach look like?           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 3.3 Template: Solution Evaluation Matrix

```
┌─────────────────────────────────────────────────────────────────────┐
│                 SOLUTION EVALUATION MATRIX                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Evaluate top 3 solution options:                                   │
│                                                                      │
│  ┌──────────────────────────────────────────────────────────────┐  │
│  │                                                               │  │
│  │  Criteria        │ Option 1 │ Option 2 │ Option 3 │ Weight   │  │
│  │                  │ (1-5)    │ (1-5)    │ (1-5)    │          │  │
│  │──────────────────│──────────│──────────│──────────│──────────│  │
│  │                  │          │          │          │          │  │
│  │ Solves problem   │   ___    │   ___    │   ___    │   30%    │  │
│  │ effectively      │          │          │          │          │  │
│  │──────────────────│──────────│──────────│──────────│──────────│  │
│  │ Fits appetite    │   ___    │   ___    │   ___    │   25%    │  │
│  │ (time/budget)    │          │          │          │          │  │
│  │──────────────────│──────────│──────────│──────────│──────────│  │
│  │ User will        │   ___    │   ___    │   ___    │   20%    │  │
│  │ understand/adopt │          │          │          │          │  │
│  │──────────────────│──────────│──────────│──────────│──────────│  │
│  │ Technical        │   ___    │   ___    │   ___    │   15%    │  │
│  │ feasibility      │          │          │          │          │  │
│  │──────────────────│──────────│──────────│──────────│──────────│  │
│  │ Scalable /       │   ___    │   ___    │   ___    │   10%    │  │
│  │ Future-proof     │          │          │          │          │  │
│  │──────────────────│──────────│──────────│──────────│──────────│  │
│  │                  │          │          │          │          │  │
│  │ WEIGHTED SCORE   │   ___    │   ___    │   ___    │          │  │
│  │                  │          │          │          │          │  │
│  └──────────────────────────────────────────────────────────────┘  │
│                                                                      │
│  SELECTED OPTION: __________                                        │
│                                                                      │
│  RATIONALE:                                                         │
│  _________________________________________________________________  │
│  _________________________________________________________________  │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 3.4 Template: Solution Shaping (Shape Up style)

```
┌─────────────────────────────────────────────────────────────────────┐
│                      SOLUTION SHAPING                                │
│              (Shaped = Not too abstract, not too detailed)          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  SOLUTION NAME: _______________________________________________     │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 1. PROBLEM RECAP (1 sentence)                                │   │
│  │                                                              │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 2. APPETITE                                                  │   │
│  │                                                              │   │
│  │ Time: ___ weeks   Team: ___ people                          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 3. SOLUTION SKETCH                                           │   │
│  │                                                              │   │
│  │ Describe the solution at a high level. Use "breadboards"    │   │
│  │ (boxes and arrows) or "fat marker sketches" (rough UI).     │   │
│  │                                                              │   │
│  │ Key elements:                                                │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  │                                                              │   │
│  │ User flow:                                                   │   │
│  │ [Entry point] → [Step 1] → [Step 2] → [Outcome]             │   │
│  │                                                              │   │
│  │ _________________________________________________________   │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 4. RABBIT HOLES (Risks to avoid)                             │   │
│  │                                                              │   │
│  │ Things that could derail the project:                        │   │
│  │ □ _______________________________________________________   │   │
│  │   Mitigation: ___________________________________________   │   │
│  │                                                              │   │
│  │ □ _______________________________________________________   │   │
│  │   Mitigation: ___________________________________________   │   │
│  │                                                              │   │
│  │ □ _______________________________________________________   │   │
│  │   Mitigation: ___________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 5. NO-GOs (Explicitly out of scope)                          │   │
│  │                                                              │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 6. NICE-TO-HAVES (If time permits)                           │   │
│  │                                                              │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 3.5 Technology & Architecture Decision

```
┌─────────────────────────────────────────────────────────────────────┐
│              TECHNOLOGY & ARCHITECTURE DECISION                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SOLUTION TYPE (Check all that apply)                         │   │
│  │                                                              │   │
│  │ □ Traditional software (CRUD, workflows)                    │   │
│  │ □ AI/ML powered (needs model, training data)                │   │
│  │ □ AI Agent (autonomous, tool-using)                         │   │
│  │ □ Integration/Automation (connects systems)                 │   │
│  │ □ Data product (analytics, dashboards)                      │   │
│  │ □ Other: ______________________________________________     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ IF AI/AGENT: Additional considerations                       │   │
│  │                                                              │   │
│  │ □ Does this need an AI Agent? (See AI Agent checklist)      │   │
│  │ □ What agent pattern? (Sequential/Supervisor/Parallel)      │   │
│  │ □ Hybrid approach? (LLM + Deterministic)                    │   │
│  │ □ Data requirements for training/RAG?                       │   │
│  │                                                              │   │
│  │ → Refer to AI-AGENT-BUILDING-METHODOLOGY.md for details     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ ARCHITECTURE APPROACH                                        │   │
│  │                                                              │   │
│  │ □ Build from scratch                                        │   │
│  │ □ Extend existing system: ______________________________    │   │
│  │ □ Use off-the-shelf + customize: _______________________    │   │
│  │ □ Integration only (no new system)                          │   │
│  │                                                              │   │
│  │ RATIONALE:                                                   │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ KEY TECHNOLOGY CHOICES                                       │   │
│  │                                                              │   │
│  │ Frontend: _______________________________________________   │   │
│  │ Backend: ________________________________________________   │   │
│  │ Database: _______________________________________________   │   │
│  │ AI/ML (if applicable): __________________________________   │   │
│  │ Infrastructure: _________________________________________   │   │
│  │ Key integrations: _______________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 3.6 Phase 3 Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                PHASE 3 COMPLETION CHECKLIST                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  □ Multiple solution options generated                              │
│  □ Options evaluated against criteria                               │
│  □ Solution selected with clear rationale                           │
│  □ Solution shaped (not too abstract, not too detailed)             │
│  □ Rabbit holes identified with mitigations                         │
│  □ Scope boundaries clear (no-gos defined)                          │
│  □ Technology approach decided                                      │
│  □ Team understands the solution well enough to build               │
│                                                                      │
│  GATE QUESTIONS (Shape Up "Betting Table"):                         │
│  □ Is this shaped well enough that a team can build it?             │
│  □ Is the appetite appropriate for the value?                       │
│  □ Are the risks manageable?                                        │
│  □ Is this the right time to build this?                            │
│  □ Do we have the right team available?                             │
│                                                                      │
│  DECISION: □ BET (proceed to build)  □ NO BET (return to shaping)  │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 4: DELIVER
## "Build, Ship & Learn"

### 4.1 Mục tiêu Phase này

```
┌─────────────────────────────────────────────────────────────────────┐
│                     DELIVER PHASE GOALS                              │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ✓ Build MVP theo shaped solution                                   │
│  ✓ Ship to real users                                               │
│  ✓ Measure impact                                                   │
│  ✓ Learn từ user feedback và data                                   │
│  ✓ Decide: Iterate, Pivot, hoặc Proceed                            │
│                                                                      │
│  OUTPUT: Shipped MVP + Validated learnings                          │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 4.2 Template: Build Kickoff

```
┌─────────────────────────────────────────────────────────────────────┐
│                      BUILD KICKOFF                                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PROJECT: _____________________________________________________    │
│  START DATE: ______________   END DATE: ______________              │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ TEAM                                                         │   │
│  │                                                              │   │
│  │ • Product Owner: _______________________________________    │   │
│  │ • Designer: ____________________________________________    │   │
│  │ • Engineers: ___________________________________________    │   │
│  │ • Other: _______________________________________________    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PROBLEM & SOLUTION RECAP                                     │   │
│  │                                                              │   │
│  │ Problem: ________________________________________________   │   │
│  │ Solution: _______________________________________________   │   │
│  │ Success metric: _________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SCOPE REMINDER                                               │   │
│  │                                                              │   │
│  │ IN SCOPE:                                                    │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │                                                              │   │
│  │ OUT OF SCOPE:                                                │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │                                                              │   │
│  │ NICE-TO-HAVE (only if time):                                │   │
│  │ □ _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ WORKING AGREEMENTS                                           │   │
│  │                                                              │   │
│  │ □ Time is fixed, scope is variable                          │   │
│  │ □ Team has autonomy to make scope decisions                 │   │
│  │ □ Update Hill Chart daily (or equivalent progress tracking) │   │
│  │ □ No scope creep without explicit trade-off discussion      │   │
│  │ □ Ship something by end of cycle, no matter what            │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 4.3 Build Progress Tracking (Hill Chart concept)

```
┌─────────────────────────────────────────────────────────────────────┐
│                   BUILD PROGRESS TRACKING                            │
│                     (Hill Chart Concept)                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  The "Hill" represents progress on any piece of work:               │
│                                                                      │
│                        ╱╲                                           │
│                       ╱  ╲                                          │
│                      ╱    ╲                                         │
│                     ╱      ╲                                        │
│                    ╱        ╲                                       │
│                   ╱          ╲                                      │
│                  ╱            ╲                                     │
│                 ╱              ╲                                    │
│                ╱                ╲                                   │
│               ╱                  ╲                                  │
│              ╱                    ╲                                 │
│  ───────────╱──────────────────────╲────────────                   │
│                                                                      │
│  UPHILL (Figuring out)    │    DOWNHILL (Executing)                │
│  • Unknowns               │    • Knowns                            │
│  • Discovering approach   │    • Executing tasks                   │
│  • Solving puzzles        │    • Finishing work                    │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ SCOPE ITEMS TRACKING                                         │   │
│  │                                                              │   │
│  │ Item                    │ Status           │ Position       │   │
│  │─────────────────────────│──────────────────│────────────────│   │
│  │ [Scope item 1]          │ Figuring out     │ ●○○○○○○○○○    │   │
│  │ [Scope item 2]          │ Approach clear   │ ○○○○●○○○○○    │   │
│  │ [Scope item 3]          │ Executing        │ ○○○○○○●○○○    │   │
│  │ [Scope item 4]          │ Almost done      │ ○○○○○○○○●○    │   │
│  │ [Scope item 5]          │ Done             │ ○○○○○○○○○●    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  Update daily/every-other-day. If items stuck uphill for too long, │
│  it's a sign of trouble - may need to cut scope or get help.       │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 4.4 Template: Launch Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                      LAUNCH CHECKLIST                                │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PRE-LAUNCH: QUALITY                                          │   │
│  │                                                              │   │
│  │ □ Core functionality tested                                  │   │
│  │ □ Edge cases handled (or documented as known issues)        │   │
│  │ □ Error handling in place                                    │   │
│  │ □ Performance acceptable                                     │   │
│  │ □ Security review completed (if needed)                      │   │
│  │ □ Accessibility checked (if user-facing)                     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PRE-LAUNCH: MEASUREMENT                                      │   │
│  │                                                              │   │
│  │ □ Analytics/tracking in place                                │   │
│  │ □ Success metrics can be measured                            │   │
│  │ □ Error/exception monitoring set up                          │   │
│  │ □ User feedback mechanism ready                              │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PRE-LAUNCH: COMMUNICATION                                    │   │
│  │                                                              │   │
│  │ □ User documentation ready (if needed)                       │   │
│  │ □ Support team briefed (if needed)                          │   │
│  │ □ Stakeholders informed of launch                            │   │
│  │ □ Rollback plan documented                                   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ LAUNCH STRATEGY                                              │   │
│  │                                                              │   │
│  │ □ Big bang (everyone at once)                               │   │
│  │ □ Phased rollout:                                           │   │
│  │   • Phase 1: __________ (___% of users)                     │   │
│  │   • Phase 2: __________ (___% of users)                     │   │
│  │   • Phase 3: General availability                           │   │
│  │                                                              │   │
│  │ □ Feature flag controlled                                    │   │
│  │ □ A/B test                                                   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  LAUNCH DATE: ______________                                        │
│  LAUNCH OWNER: ______________                                       │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 4.5 Template: Post-Launch Review (Learn)

```
┌─────────────────────────────────────────────────────────────────────┐
│                    POST-LAUNCH REVIEW                                │
│                  (Build-Measure-Learn: LEARN)                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PROJECT: _____________________________________________________    │
│  REVIEW DATE: ______________ (1-2 weeks after launch)               │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 1. METRICS REVIEW                                            │   │
│  │                                                              │   │
│  │ Primary metric:                                              │   │
│  │ • Target: __________  Actual: __________  □Met □Not met     │   │
│  │                                                              │   │
│  │ Secondary metrics:                                           │   │
│  │ • _____________ Target: ___ Actual: ___ □Met □Not met       │   │
│  │ • _____________ Target: ___ Actual: ___ □Met □Not met       │   │
│  │ • _____________ Target: ___ Actual: ___ □Met □Not met       │   │
│  │                                                              │   │
│  │ Guardrail metrics:                                           │   │
│  │ • _____________ Status: □OK □Concerning                     │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 2. USER FEEDBACK SUMMARY                                     │   │
│  │                                                              │   │
│  │ Feedback collected from:                                     │   │
│  │ □ In-app feedback: ___ responses                            │   │
│  │ □ User interviews: ___ sessions                             │   │
│  │ □ Support tickets: ___ related tickets                      │   │
│  │ □ Other: ____________                                       │   │
│  │                                                              │   │
│  │ Top positive feedback:                                       │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  │                                                              │   │
│  │ Top negative feedback / issues:                              │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  │                                                              │   │
│  │ Unexpected feedback:                                         │   │
│  │ • _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 3. KEY LEARNINGS                                             │   │
│  │                                                              │   │
│  │ What did we learn about the problem?                         │   │
│  │ _________________________________________________________   │   │
│  │                                                              │   │
│  │ What did we learn about the solution?                        │   │
│  │ _________________________________________________________   │   │
│  │                                                              │   │
│  │ What did we learn about our users?                           │   │
│  │ _________________________________________________________   │   │
│  │                                                              │   │
│  │ What would we do differently?                                │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ 4. DECISION                                                  │   │
│  │                                                              │   │
│  │ Based on learnings, we will:                                 │   │
│  │                                                              │   │
│  │ □ PERSEVERE - Continue with current approach                │   │
│  │   Next iteration focus: _________________________________   │   │
│  │                                                              │   │
│  │ □ PIVOT - Change approach based on learnings                │   │
│  │   New direction: ________________________________________   │   │
│  │                                                              │   │
│  │ □ KILL - This isn't working, move on                        │   │
│  │   Reason: _______________________________________________   │   │
│  │                                                              │   │
│  │ □ SCALE - Success! Invest more                              │   │
│  │   Scale plan: ___________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 4.6 Phase 4 Checklist

```
┌─────────────────────────────────────────────────────────────────────┐
│                PHASE 4 COMPLETION CHECKLIST                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  BUILD:                                                             │
│  □ MVP built within appetite (time/budget)                          │
│  □ Core functionality working                                       │
│  □ Scope cut appropriately (not over-built)                         │
│                                                                      │
│  SHIP:                                                              │
│  □ Shipped to real users                                            │
│  □ Measurement in place                                             │
│  □ Feedback collection enabled                                      │
│                                                                      │
│  LEARN:                                                             │
│  □ Metrics reviewed (1-2 weeks post-launch)                         │
│  □ User feedback collected and analyzed                             │
│  □ Key learnings documented                                         │
│  □ Decision made (Persevere/Pivot/Kill/Scale)                       │
│                                                                      │
│  GATE QUESTIONS:                                                    │
│  □ Did we ship something valuable within the appetite?              │
│  □ Do we have enough data to make an informed decision?             │
│  □ Is the team aligned on next steps?                               │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# PHASE 5: SCALE
## "Grow & Continuously Improve"

### 5.1 Mục tiêu Phase này

```
┌─────────────────────────────────────────────────────────────────────┐
│                     SCALE PHASE GOALS                                │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ✓ Iterate based on learnings                                       │
│  ✓ Expand to more users (if successful)                            │
│  ✓ Optimize performance and cost                                    │
│  ✓ Build sustainability (documentation, team knowledge)            │
│  ✓ Continuous improvement loop                                      │
│                                                                      │
│  This is an ONGOING phase - the product lifecycle continues        │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 5.2 Template: Iteration Planning

```
┌─────────────────────────────────────────────────────────────────────┐
│                    ITERATION PLANNING                                │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ITERATION #: ___   DATES: ______ to ______                         │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ INPUT: What did we learn last iteration?                     │   │
│  │                                                              │   │
│  │ Key learnings:                                               │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  │                                                              │   │
│  │ User requests:                                               │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  │                                                              │   │
│  │ Bugs/Issues:                                                 │   │
│  │ • _______________________________________________________   │   │
│  │ • _______________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ PRIORITIZATION (RICE or similar)                             │   │
│  │                                                              │   │
│  │ Item          │ Reach │ Impact │ Confidence │ Effort │ Score│   │
│  │───────────────│───────│────────│────────────│────────│──────│   │
│  │               │       │        │            │        │      │   │
│  │               │       │        │            │        │      │   │
│  │               │       │        │            │        │      │   │
│  │               │       │        │            │        │      │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ THIS ITERATION FOCUS                                         │   │
│  │                                                              │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │ □ _______________________________________________________   │   │
│  │                                                              │   │
│  │ Success criteria for this iteration:                         │   │
│  │ _________________________________________________________   │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 5.3 Template: Product Health Dashboard

```
┌─────────────────────────────────────────────────────────────────────┐
│                  PRODUCT HEALTH DASHBOARD                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PRODUCT: _____________________   PERIOD: _____________________     │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ USAGE METRICS                                                │   │
│  │                                                              │   │
│  │ Daily Active Users:    _______  (▲▼ ___% vs last period)    │   │
│  │ Weekly Active Users:   _______  (▲▼ ___% vs last period)    │   │
│  │ Monthly Active Users:  _______  (▲▼ ___% vs last period)    │   │
│  │                                                              │   │
│  │ Key actions per user:  _______  (▲▼ ___% vs last period)    │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ QUALITY METRICS                                              │   │
│  │                                                              │   │
│  │ User satisfaction (NPS/CSAT): _______                        │   │
│  │ Error rate:                   _______%                       │   │
│  │ Support tickets:              _______                        │   │
│  │ Uptime:                       _______%                       │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ BUSINESS METRICS                                             │   │
│  │                                                              │   │
│  │ Primary success metric:   _______  (vs target: _______)     │   │
│  │ Revenue/savings impact:   $_______                          │   │
│  │ Cost per user:            $_______                          │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ HEALTH STATUS                                                │   │
│  │                                                              │   │
│  │ Overall: □ Healthy  □ Needs attention  □ Critical           │   │
│  │                                                              │   │
│  │ Top concerns:                                                │   │
│  │ 1. _______________________________________________________  │   │
│  │ 2. _______________________________________________________  │   │
│  │ 3. _______________________________________________________  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### 5.4 Continuous Improvement Cycle

```
┌─────────────────────────────────────────────────────────────────────┐
│              CONTINUOUS IMPROVEMENT CYCLE                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  The product enters a continuous loop:                              │
│                                                                      │
│                    ┌───────────────┐                                │
│                    │    MEASURE    │                                │
│                    │  (Metrics &   │                                │
│                    │   Feedback)   │                                │
│                    └───────┬───────┘                                │
│                            │                                        │
│                            ▼                                        │
│  ┌───────────────┐        ┌───────────────┐                        │
│  │     BUILD     │◀───────│     LEARN     │                        │
│  │  (Implement   │        │  (Analyze &   │                        │
│  │   changes)    │        │   Decide)     │                        │
│  └───────┬───────┘        └───────────────┘                        │
│          │                        ▲                                 │
│          │                        │                                 │
│          └────────────────────────┘                                │
│                                                                      │
│  CADENCE RECOMMENDATIONS:                                           │
│                                                                      │
│  • Daily: Monitor key metrics                                       │
│  • Weekly: Review user feedback, address bugs                       │
│  • Bi-weekly/Monthly: Iteration planning                           │
│  • Quarterly: Strategic review, major feature planning              │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# APPENDIX

## A. When to Use AI/Agent (Decision Framework)

```
┌─────────────────────────────────────────────────────────────────────┐
│                  AI/AGENT DECISION FRAMEWORK                         │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Answer these questions to decide if AI Agent is appropriate:       │
│                                                                      │
│  1. Does the task require reasoning/judgment?                       │
│     □ Yes (AI candidate)  □ No (Traditional software)              │
│                                                                      │
│  2. Is the input unstructured (natural language, images)?           │
│     □ Yes (AI candidate)  □ No (Traditional software)              │
│                                                                      │
│  3. Are there too many edge cases to enumerate?                     │
│     □ Yes (AI candidate)  □ No (Rule-based system)                 │
│                                                                      │
│  4. Does it need to be creative/generative?                         │
│     □ Yes (AI candidate)  □ No (Traditional software)              │
│                                                                      │
│  5. Does it need to use tools autonomously?                         │
│     □ Yes (Agent needed)  □ No (Simple LLM call may suffice)       │
│                                                                      │
│  RESULT:                                                            │
│  • 4-5 Yes → Strong candidate for AI Agent                         │
│  • 2-3 Yes → Consider hybrid approach                              │
│  • 0-1 Yes → Traditional software likely better                    │
│                                                                      │
│  IF AI AGENT: → Refer to AI-AGENT-BUILDING-METHODOLOGY.md          │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

## B. Methodology Selection Guide

```
┌─────────────────────────────────────────────────────────────────────┐
│                 METHODOLOGY SELECTION GUIDE                          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  This framework combines multiple methodologies. Use what fits:     │
│                                                                      │
│  DOUBLE DIAMOND (This doc's structure)                              │
│  └─ Best for: Overall product discovery and design process         │
│  └─ Use: Problem/Solution space thinking, diverge/converge         │
│                                                                      │
│  SHAPE UP (Basecamp)                                                │
│  └─ Best for: Execution and delivery                               │
│  └─ Use: Shaping, appetite, betting, 6-week cycles, Hill Charts    │
│  └─ When: Team building software in cycles                         │
│                                                                      │
│  LEAN STARTUP (Eric Ries)                                           │
│  └─ Best for: Validating new ideas under uncertainty               │
│  └─ Use: MVP, Build-Measure-Learn, pivot/persevere                 │
│  └─ When: High uncertainty, need to validate assumptions           │
│                                                                      │
│  AGILE/SCRUM                                                        │
│  └─ Best for: Ongoing development with regular releases            │
│  └─ Use: Sprints, standups, retrospectives                         │
│  └─ When: Continuous feature development                           │
│                                                                      │
│  You can MIX approaches:                                            │
│  • Use Double Diamond for discovery                                 │
│  • Use Shape Up for delivery cycles                                 │
│  • Use Lean Startup for validation                                  │
│  • Use Agile ceremonies for team coordination                       │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

## C. Quick Reference: Template Index

```
┌─────────────────────────────────────────────────────────────────────┐
│                     TEMPLATE INDEX                                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PHASE 1: DISCOVER                                                  │
│  • Discovery Research Plan                                          │
│  • User Interview Guide                                             │
│  • Research Synthesis                                               │
│                                                                      │
│  PHASE 2: DEFINE                                                    │
│  • Problem Prioritization Matrix                                    │
│  • Problem Statement Canvas                                         │
│  • Success Metrics Definition                                       │
│  • Appetite & Constraints                                           │
│                                                                      │
│  PHASE 3: DEVELOP                                                   │
│  • Solution Brainstorming                                           │
│  • Solution Evaluation Matrix                                       │
│  • Solution Shaping                                                 │
│  • Technology & Architecture Decision                               │
│                                                                      │
│  PHASE 4: DELIVER                                                   │
│  • Build Kickoff                                                    │
│  • Build Progress Tracking (Hill Chart)                             │
│  • Launch Checklist                                                 │
│  • Post-Launch Review                                               │
│                                                                      │
│  PHASE 5: SCALE                                                     │
│  • Iteration Planning                                               │
│  • Product Health Dashboard                                         │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

## D. Glossary

```
┌─────────────────────────────────────────────────────────────────────┐
│                        GLOSSARY                                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Appetite: Lượng thời gian/effort sẵn sàng đầu tư cho một vấn đề   │
│            (Shape Up concept)                                       │
│                                                                      │
│  Divergent Thinking: Suy nghĩ mở rộng, khám phá nhiều khả năng     │
│                                                                      │
│  Convergent Thinking: Thu hẹp, chọn lựa, focus vào một hướng       │
│                                                                      │
│  MVP (Minimum Viable Product): Phiên bản tối thiểu để validate     │
│                                 hypothesis với real users           │
│                                                                      │
│  Hill Chart: Cách track progress - uphill (figuring out) và        │
│              downhill (executing)                                   │
│                                                                      │
│  Shaping: Định hình solution ở mức vừa đủ chi tiết để team có thể  │
│           tự quyết định implementation details                      │
│                                                                      │
│  Betting: Quyết định đầu tư vào một shaped project                 │
│                                                                      │
│  Pivot: Thay đổi hướng đi dựa trên learnings                       │
│                                                                      │
│  Persevere: Tiếp tục hướng hiện tại, iterate thêm                  │
│                                                                      │
│  Rabbit Hole: Rủi ro có thể kéo dài project ngoài dự kiến          │
│                                                                      │
│  Guardrail Metrics: Metrics không được vi phạm (safety thresholds) │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

# MASTER CHECKLIST

```
┌─────────────────────────────────────────────────────────────────────┐
│               MASTER CHECKLIST - PRODUCT BUILDING                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  PHASE 1: DISCOVER (Week 1-2)                                       │
│  □ Research plan created                                            │
│  □ User research conducted (interviews, observations)               │
│  □ Research synthesis completed                                     │
│  □ Key insights & opportunity areas identified                      │
│                                                                      │
│  PHASE 2: DEFINE (Week 2-3)                                         │
│  □ Problems prioritized                                             │
│  □ Problem statement written                                        │
│  □ Success metrics defined                                          │
│  □ Appetite set                                                     │
│  □ Stakeholder alignment                                            │
│                                                                      │
│  PHASE 3: DEVELOP (Week 3-4)                                        │
│  □ Solution options generated                                       │
│  □ Solution evaluated and selected                                  │
│  □ Solution shaped                                                  │
│  □ Risks identified                                                 │
│  □ Tech approach decided                                            │
│  □ Betting decision made                                            │
│                                                                      │
│  PHASE 4: DELIVER (Week 4-8)                                        │
│  □ Build kickoff completed                                          │
│  □ MVP built within appetite                                        │
│  □ Shipped to real users                                            │
│  □ Metrics measured                                                 │
│  □ Post-launch review completed                                     │
│  □ Decision made (Persevere/Pivot/Kill/Scale)                       │
│                                                                      │
│  PHASE 5: SCALE (Ongoing)                                           │
│  □ Iteration cycles established                                     │
│  □ Health monitoring in place                                       │
│  □ Continuous improvement loop active                               │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

**Document Version:** 1.0
**Sources:** Double Diamond (Design Council), Lean Startup (Eric Ries), Shape Up (Basecamp), Agile, Uber AI Agent Ecosystem
**Intended Use:** Reference guide for AI-assisted product development

---

## HOW TO USE THIS WITH AI

Khi bạn muốn AI hỗ trợ build product, copy prompt này:

```
Tôi đang build [mô tả sản phẩm]. 

Hãy đọc PRODUCT-BUILDING-METHODOLOGY.md và hướng dẫn tôi 
qua từng phase. Hiện tại tôi đang ở [Phase X].

[Mô tả thêm context nếu có]
```

AI sẽ guide bạn qua từng phase với templates phù hợp.