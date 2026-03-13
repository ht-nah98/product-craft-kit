# Product Requirements

Folder chứa toàn bộ tài liệu yêu cầu sản phẩm: PRD, Epics, User Stories, và Screen Specs.

---

## Structure

```
01_product_requirements/
├── prd/                        # Product Requirements Documents
│   └── PRD-[name].md
└── [module-name]/              # One folder per module/domain
    ├── EPIC-[PREFIX]-[N].md    # Epic specification
    ├── US-[PREFIX]-[N].md      # User Stories
    └── SCR-[PREFIX]-[N].md     # Screen specs (complex UI features)
```

---

## Document Types

| Type | Prefix | Template |
|------|--------|----------|
| Product Requirements Doc | `PRD-` | `_template_prd.md` |
| Epic | `EPIC-[PREFIX]-[N]` | `_template_epic.md` |
| User Story | `US-[PREFIX]-[N]` | `_template_user_story.md` |
| Screen Spec | `SCR-[PREFIX]-[N]` | `_template_screen.md` |
| Shared Component | `COMP-[PREFIX]-[N]` | `_template_shared_component.md` |

Templates in: `.agent/resources/templates/01_product_requirements/`

---

## Naming Convention

```
Module prefix examples: ORG, EMP, ATT, PAY, AUTH, ...

EPIC-ORG-001: Quản lý Cơ cấu Tổ chức
US-ORG-001: Tạo đơn vị tổ chức
SCR-ORG-001: Màn hình quản lý cơ cấu tổ chức
```

---

## Rules

- Each module gets its own subfolder
- Epics and User Stories go in the module folder, NOT the root
- Always link User Story → Epic → PRD
- Use MoSCoW priority on all stories
