# Plans

Folder chứa tài liệu kế hoạch triển khai: backlog, phase plans, và roadmap.

---

## Structure

```
03_plans/
├── phases/                     # Phase breakdown
│   ├── phase-1.md              # Phase 1 plan
│   └── phase-1-sprint-1.md     # Sprint-level detail
└── roadmap.md                  # High-level roadmap (optional)
```

> Backlog chính được lưu tại `projects/[project]/backlog.md` (root level)

---

## Document Types

| Type | Template |
|------|----------|
| Phase Plan | `_template_phase.md` |
| Sprint/Sub-phase Plan | `_template_sub_phase.md` |
| Backlog | `_template_backlog.md` |

Templates in: `.agent/resources/templates/04_plans_docs/`

---

## Rules

- Phase = 1-3 months of work, contains multiple sprints
- Each phase has clear goals and deliverables
- Use checklist format to track progress
- Link phases back to Epics in `01_product_requirements/`
