# Technical Specs

Folder chứa tài liệu kỹ thuật: kiến trúc hệ thống, database schema, và technical specs per feature.

---

## Structure

```
02_technical_specs/
├── architecture.md             # System architecture overview
├── database-schema.md          # Database schema tổng thể
└── [module-name]/              # Per-module technical specs
    └── TP-[PREFIX]-[N].md      # Technical Spec per feature/epic
```

---

## Document Types

| Type | Prefix | Template |
|------|--------|----------|
| System Architecture | `architecture` | `_template_architecture.md` |
| Database Schema | `database-schema` | `_template_database_schema.md` |
| Technical Spec | `TP-[PREFIX]-[N]` | `_template_tech_spec.md` |

Templates in: `.agent/resources/templates/02_technical_specs/`

---

## When to Write a Technical Spec

Write a TP when an Epic/Feature involves:
- Complex business logic or algorithms
- New database tables or significant schema changes
- New or modified API endpoints
- Integration with external services
- Performance or security considerations

---

## Rules

- Architecture and DB Schema docs are singleton files at the root
- Per-feature TPs link to their parent Epic
- Always include API spec, DB design, and logic flow
- Keep in sync with code — update when implementation changes
