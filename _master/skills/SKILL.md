---
name: PO Documentation & Product Building Router
description: Tự động nhận diện yêu cầu và route đến skill/template phù hợp
---

# PO Documentation & Product Building Router

> **ĐÂY LÀ FILE QUAN TRỌNG NHẤT - ĐỌC ĐẦU TIÊN KHI LÀM VIỆC TRONG WORKSPACE NÀY**

---

## Skill Categories

```
_master/skills/
├── SKILL.md                    # ← Router này
├── 1_documentation/            # Viết tài liệu PO truyền thống
├── 2_product_building/         # Product Building lifecycle
└── 3_ai_agent/                 # AI Agent development
```

---

## Routing Table

### 📝 1. Documentation Skills

| Từ khóa | Skill | Template |
|---------|-------|----------|
| "epic", "nhóm tính năng" | `1_documentation/SKILL_write-epic.md` | `_template_epic.md` |
| "user story", "story", "US" | `1_documentation/SKILL_write-user-story.md` | `_template_user_story.md` |
| "AC", "acceptance criteria" | `1_documentation/SKILL_write-acceptance-criteria.md` | - |
| "DoD", "definition of done" | `1_documentation/SKILL_write-dod.md` | - |
| "PRD", "product requirement" | `1_documentation/SKILL_write-prd.md` | `_template_prd.md` |
| "backlog", "prioritize" | `1_documentation/SKILL_backlog-management.md` | `_template_backlog.md` |

### 🚀 2. Product Building Skills

| Từ khóa | Skill | Template | Phase |
|---------|-------|----------|-------|
| "discovery", "research", "tìm hiểu user" | `2_product_building/SKILL_discovery.md` | `_template_discovery.md` | 1 |
| "problem", "vấn đề", "define" | `2_product_building/SKILL_problem-definition.md` | `_template_problem_canvas.md` | 2 |
| "solution", "giải pháp", "shape" | `2_product_building/SKILL_solution-shaping.md` | `_template_solution_shape.md` | 3 |
| "build", "ship", "launch" | `2_product_building/SKILL_build-and-ship.md` | `_template_launch_checklist.md` | 4 |
| "iterate", "scale", "improve" | `2_product_building/SKILL_iteration.md` | `_template_iteration_plan.md` | 5 |

### 🤖 3. AI Agent Skills

| Từ khóa | Skill | Template | Phase |
|---------|-------|----------|-------|
| "ai agent", "agent discovery", "llm" | `3_ai_agent/SKILL_agent-discovery.md` | `_template_agent_problem.md` | 1 |
| "architecture", "pattern", "supervisor" | `3_ai_agent/SKILL_agent-architecture.md` | `_template_agent_architecture.md` | 2 |
| "pattern", "sequential", "parallel" | `3_ai_agent/SKILL_agent-patterns.md` | `_template_agent_component.md` | Ref |

---

## Quy Trình Làm Việc

### Bước 1: Nhận diện LOẠI công việc

```
User muốn làm gì?
├── Viết tài liệu cụ thể (Epic, Story, PRD...) → 1_documentation/
├── Xây dựng sản phẩm mới từ đầu → 2_product_building/
└── Xây dựng AI Agent → 3_ai_agent/
```

### Bước 2: Xác định dự án

```
Nếu user đề cập tên dự án:
  → Đọc projects/[project-name]/project-context.md
  → Đọc projects/[project-name]/glossary.md

Nếu không rõ:
  → Hỏi: "Bạn muốn làm việc với dự án nào?"
```

### Bước 3: Đọc Skill và Template

```
1. Đọc skill tương ứng trong _master/skills/[category]/
2. Đọc template được reference trong Skill
3. Kết hợp với project context
4. Viết/tạo tài liệu theo template
```

---

## Cấu trúc Tài liệu (Documentation)

```
Module (Nhóm tính năng lớn)
└── Epic (Tính năng lớn, nhiều sprint)
    └── User Story (Chức năng đơn lẻ, 1 sprint)
        └── Acceptance Criteria (Tiêu chí)
```

## Product Building Lifecycle

```
Phase 1: DISCOVER → Phase 2: DEFINE → Phase 3: DEVELOP → Phase 4: DELIVER → Phase 5: SCALE
```

## AI Agent Lifecycle

```
Phase 1: DISCOVERY → Phase 2: ARCHITECTURE → Phase 3: BUILD → Phase 4: DEPLOY
```

---

## Xử lý khi KHÔNG RÕ

```
Tôi cần làm rõ yêu cầu:
1. Bạn muốn làm gì? (Viết tài liệu / Xây sản phẩm / Xây AI Agent)
2. Cho dự án nào?
3. Đang ở phase/giai đoạn nào?
```

---

## File Locations

```
/home/user/Desktop/PO-WriteDoc/
├── _master/
│   ├── skills/
│   │   ├── SKILL.md                     # Router
│   │   ├── 1_documentation/             # Doc skills
│   │   ├── 2_product_building/          # Product skills
│   │   └── 3_ai_agent/                  # AI Agent skills
│   ├── templates/
│   │   ├── 01_business_docs/
│   │   ├── 02_features_docs/
│   │   ├── 06_product_building/         # NEW
│   │   └── 07_ai_agent/                 # NEW
│   └── knowledge/                        # Methodology docs
│
└── projects/[project-name]/
    ├── project-context.md
    ├── glossary.md
    └── docs/
```

---

> [!CAUTION]
> **KHÔNG** tự bịa format. **PHẢI** đọc template và tuân theo 100%.
