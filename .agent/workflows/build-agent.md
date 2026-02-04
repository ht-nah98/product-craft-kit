---
description: Build AI Agent - Workflow xây dựng AI Agent từ Discovery đến Architecture
---

# Workflow: Build AI Agent

> Workflow cho AI Agent development - từ problem đến architecture

## Các bước thực hiện

### 1. Đọc Skills liên quan
// turbo
Đọc các files:
- `.agent/skills/agent_discovery/SKILL.md`
- `.agent/skills/agent_architecture/SKILL.md`
- `.agent/skills/agent_patterns/SKILL.md`

### 2. Đọc Templates
// turbo
Đọc các templates:
- `.agent/resources/templates/07_ai_agent/_template_agent_problem.md`
- `.agent/resources/templates/07_ai_agent/_template_agent_architecture.md`
- `.agent/resources/templates/07_ai_agent/_template_agent_component.md`

### 3. Phase 1: Agent Discovery

Hỏi user để hiểu problem:
1. Agent sẽ làm gì? (Task description)
2. Ai sử dụng? (User persona)
3. Hiện tại người dùng làm thế nào? (Current workflow)
4. Vấn đề gì xảy ra? (Pain points)

Validate AI Agent là đúng solution:
- Task cần reasoning?
- Input là natural language?
- Nhiều edge cases?

Tạo: `projects/[project]/docs/7_ai_agent/phase1_problem_canvas.md`

### 4. Phase 2: Architecture Design

Xác định pattern:
1. Sequential Pipeline - Clear step-by-step
2. Supervisor + Sub-Agents - Multi-domain
3. Parallel + Merge - Batch processing
4. Single Agent + Tools - Simple task

Design components và data flow.

Tạo: `projects/[project]/docs/7_ai_agent/phase2_architecture.md`

### 5. Technology Decisions

Hỏi user về constraints:
- Team size và expertise
- Budget (dev + ops)
- Timeline
- Security requirements

Recommend tech stack phù hợp.

### 6. Create Component Specs

Với mỗi component trong architecture:
Tạo spec file: `projects/[project]/docs/7_ai_agent/components/[component_name].md`

### 7. Review và Next Steps

Summary architecture và get approval.
Define build order cho Phase 3.
