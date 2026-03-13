# CLAUDE.md — [Project Name]

Instructions for Claude Code when working inside this project.

---

## Project Overview

**[Project Name]** — [Short description, 1-2 sentences].

Tech stack: [Frontend] / [Backend] / [Database] / [Deployment]

---

## Folder Structure

```
[project-name]/
├── project-context.md          # Project context — READ FIRST
├── glossary.md                 # Domain terms and definitions
├── backlog.md                  # Product backlog
└── docs/
    ├── 01_product_requirements/ # PRD, Epics, User Stories, Screens
    ├── 02_technical_specs/      # Architecture, DB Schema, Tech Specs
    ├── 03_plans/                # Phase plans, roadmap
    ├── 04_testing/              # Test strategy, test guides
    └── 05_ai_agent/             # AI Agent docs (only if applicable)
```

---

## Rules

### General
- Use Vietnamese for all communication with user (unless user writes in English)
- Read `project-context.md` and `glossary.md` before any task

### Documentation Rules
- Use Markdown format for all docs
- Always place docs in the correct subfolder
- Use Mermaid or ASCII for diagrams
- DRY: if content is shared, extract to a separate file and link
- Keep docs concise — cover key points, not every detail

### File Naming
| Document type | Convention |
|--------------|------------|
| PRD | `PRD-[name].md` |
| Epic | `EPIC-[PREFIX]-[N].md` |
| User Story | `US-[PREFIX]-[N].md` |
| Screen Spec | `SCR-[PREFIX]-[N].md` |
| Technical Spec | `TP-[PREFIX]-[N].md` |

---

## Start of Session

1. Read `project-context.md`
2. Read `glossary.md`
3. Read the relevant folder README(s) to understand existing docs
4. Reference existing docs before creating new ones

---

## Navigation

- [Business context & goals](./project-context.md)
- [Domain glossary](./glossary.md)
- [Product backlog](./backlog.md)
- [Product Requirements](./docs/01_product_requirements/README.md)
- [Technical Specs](./docs/02_technical_specs/README.md)
- [Plans](./docs/03_plans/README.md)
- [Testing](./docs/04_testing/README.md)
