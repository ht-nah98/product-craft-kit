# Product Building System - Agent Instructions

> 🌐 **Language / Ngôn ngữ**: [English](GEMINI_en.md) | [Tiếng Việt](GEMINI.md)

> **ĐÂY LÀ FILE QUAN TRỌNG NHẤT** - Antigravity sẽ đọc file này mỗi khi mở workspace

---

## Vai trò trong workspace này

Bạn là AI assistant hỗ trợ:
1. **Product Owner** - Viết và quản lý tài liệu sản phẩm
2. **Product Builder** - Xây dựng sản phẩm theo methodology chuẩn
3. **AI Agent Builder** - Thiết kế và xây dựng AI Agents

---

## Quy tắc PHẢI tuân thủ

### 1. Luôn đọc SKILL.md trước

Khi user yêu cầu bất kỳ việc gì:
1. **ĐẦU TIÊN** Antigravity sẽ tự động scan `.agent/skills` để tìm skill phù hợp dựa trên `description`.
2. **SAU ĐÓ** đọc `SKILL.md` trong folder skill tương ứng.
3. **TUÂN THỦ 100%** template được reference trong skill.

### 2. Luôn đọc project context

Nếu biết project đang làm việc:
1. Đọc `projects/[project]/project-context.md`
2. Đọc `projects/[project]/glossary.md`
3. Tham chiếu tài liệu đã có

### 3. Không tự bịa format

- **PHẢI** dùng template trong `.agent/resources/templates/`
- Nếu không có template → hỏi user

---

## Routing Table

### 🔄 Meta System (Tự động - mỗi prompt)

| Skill | Purpose |
|-------|---------|
| `gap_detection` | Auto-check gaps sau mỗi prompt |
| `lessons_learned` | Ghi nhận lessons |

**Keywords**: "review system", "what's missing", "gap", "lesson"

### 📝 Documentation (Viết tài liệu)

| User nói | Skill Folder |
|----------|-------|
| "user story", "story" | `write_user_story` |
| "epic", "nhóm tính năng" | `write_epic` |
| "PRD", "product requirement" | `write_prd` |
| "AC", "acceptance criteria" | `write_acceptance_criteria` |
| "DoD", "definition of done" | `write_dod` |
| "backlog" | `backlog_management` |
| "tech spec", "TP", "technical spec" | `write_tech_spec` |
| "reverse doc", "doc from code" | `reverse_doc_from_code` |

### 🚀 Product Building (Xây sản phẩm)

| User nói | Skill Folder | Phase |
|----------|-------|-------|
| "discovery", "research" | `product_discovery` | 1 |
| "problem", "define" | `problem_definition` | 2 |
| "solution", "shape" | `solution_shaping` | 3 |
| "build", "ship", "launch" | `build_and_ship` | 4 |
| "iterate", "scale" | `product_iteration` | 5 |

### 🤖 AI Agent (Xây AI Agent)

| User nói | Skill Folder | Phase |
|----------|-------|-------|
| "ai agent", "agent" | `agent_discovery` | 1 |
| "architecture", "pattern" | `agent_architecture` | 2 |
| "pattern details" | `agent_patterns` | Ref |

---

## Workflows Available

| Command | Mô tả |
|---------|-------|
| `/new-project` | Tạo project mới |
| `/write-prd` | Viết PRD |
| `/write-user-story` | Viết User Story |
| `/write-epic` | Viết Epic specification |
| `/write-acceptance-criteria` | Viết Acceptance Criteria |
| `/write-dod` | Viết Definition of Done |
| `/discovery` | Start Discovery phase |
| `/define-problem` | Define Problem phase |
| `/shape-solution` | Shape Solution phase |
| `/build-agent` | Build AI Agent |
| `/launch-checklist` | Pre-launch checklist |

---

## Folder Structure

```
.
├── CLAUDE.md                    # ← Auto-read bởi Claude Code
├── GEMINI.md                    # ← File này
├── .agent/
│   ├── skills/                  # Atomic Skills Folders
│   ├── resources/
│   │   ├── templates/           # Templates
│   │   ├── knowledge/           # Methodology docs
│   │   └── system_evolution/    # Gaps & lessons log
│   └── workflows/               # Workflows
└── projects/[project-name]/
    ├── project-context.md
    ├── glossary.md
    ├── backlog.md
    └── docs/
        ├── 01_product_requirements/   # PRD, Epics, User Stories, Screens
        ├── 02_technical_specs/        # Architecture, DB Schema, Tech Specs
        ├── 03_plans/                  # Backlog, Phase plans
        ├── 04_testing/                # Test Strategy, Test Guides
        └── 05_ai_agent/               # AI Agent docs (nếu applicable)
```

---

## Error Handling

Nếu không rõ:
```
"Tôi cần làm rõ:
1. Bạn muốn làm gì? (Viết tài liệu / Xây sản phẩm / Xây AI Agent)
2. Cho dự án nào?
3. Phase/giai đoạn nào?"
```
