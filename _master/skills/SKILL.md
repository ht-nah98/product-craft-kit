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
├── 0_meta_system/              # 🔄 System Evolution (tự cải tiến)
├── 1_documentation/            # Viết tài liệu PO truyền thống
├── 2_product_building/         # Product Building lifecycle
└── 3_ai_agent/                 # AI Agent development
```

---

## Routing Table

### 🔄 0. Meta System Evolution (AUTO)

> **Tự động trigger** sau mỗi prompt/project - không cần keywords

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `0_meta_system/SKILL_system-evolution.md` | Overview cơ chế tự cải tiến | Manual review |
| `0_meta_system/SKILL_gap-detection.md` | Phát hiện gaps | Auto mỗi prompt |
| `0_meta_system/SKILL_improvement-proposal.md` | Đề xuất cải tiến | Khi có gap |
| `0_meta_system/SKILL_lessons-learned.md` | Ghi nhận bài học | End of project |

**Keywords**: "review system", "what's missing", "improve", "lesson", "gap"

### 📝 1. Documentation Skills

| Từ khóa | Skill | Template |
|---------|-------|----------|
| "epic", "nhóm tính năng" | `1_documentation/SKILL_write-epic.md` | `_template_epic.md` |
| "user story", "story", "US" | `1_documentation/SKILL_write-user-story.md` | `_template_user_story.md` |
| "screen", "màn hình", "UI" | - | `02_features_docs/_template_screen.md` |
| "module", "nghiệp vụ" | - | `01_business_docs/_template_module.md` |
| "architecture", "kiến trúc" | - | `03_technical_docs/_template_architecture.md` |
| "test strategy", "kiểm thử" | - | `05_testing_docs/_template_test_strategy.md` |
| "phase", "triển khai" | - | `04_plans_docs/_template_phase.md` |
| "AC", "acceptance criteria" | `1_documentation/SKILL_write-acceptance-criteria.md` | - |
| "DoD", "definition of done" | `1_documentation/SKILL_write-dod.md` | - |
| "PRD", "product requirement" | `1_documentation/SKILL_write-prd.md` | `_template_prd.md` |
| "backlog", "prioritize" | `1_documentation/SKILL_backlog-management.md` | `_template_backlog.md` |
| "reverse", "từ code", "HDSD" | `1_documentation/SKILL_reverse-doc-from-code.md` | `_template_hdsd.md` |


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

## Cấu trúc Tài liệu (Documentation Hierarchy)

```
Module (Phân hệ nghiệp vụ)
└── Feature Folder (Thư mục theo Module trong Feature/Tech Pillar)
    └── Screen (Mô tả giao diện & logic tập trung)
        └── User Story (Các scenario chi tiết - nếu cần tách nhỏ)
```

> [!TIP]
> Luôn tổ chức tài liệu theo **Module-First**. Tránh để hàng chục file trong một folder duy nhất.

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
_master/
├── skills/
│   ├── SKILL.md                     # Router
│   ├── 1_documentation/             # Doc skills
│   ├── 2_product_building/          # Product skills
│   └── 3_ai_agent/                  # AI Agent skills
├── templates/
│   ├── 00_ai_instructions.md        # AI hướng dẫn viết docs
│   ├── 01_business_docs/            # Module, Overview, Glossary
│   ├── 02_features_docs/            # Screen, Epic, User Story
│   ├── 03_technical_docs/           # Architecture, Database
│   ├── 04_plans_docs/               # Phase, Sub-phase
│   ├── 05_testing_docs/             # Test Strategy, Guide
│   ├── 06_product_building/         # Discovery, Problem, Solution
│   └── 07_ai_agent/                 # Agent Architecture
│   └── README.md                    # Hướng dẫn sử dụng templates
│
└── knowledge/                        # Methodology docs

projects/[project-name]/
├── project-context.md
├── glossary.md
└── docs/
    ├── 1_business_docs/            # Overview & Modules
    ├── 2_features_docs/            # shared/ & [module_name]/ folders
    │   └── [module_name]/          # Screens (SCR-) and Stories (US-)
    ├── 3_technical_docs/           # architecture.md & [module_name]/
    ├── 4_plans_docs/               # Roadmap & Phases
    └── 5_testing_docs/             # Strategy & Guides
```

---

> [!CAUTION]
> **KHÔNG** tự bịa format. **PHẢI** đọc template và tuân theo 100%.
