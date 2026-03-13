# CLAUDE.md — Safety PPE Checker

Instructions for Claude Code when working inside this project.

---

## Project Overview

**Safety PPE Checker** — AI-powered web demo that automatically assesses PPE compliance from a single full-body photo of an electrical worker.

**Phase 1 Goal**: Working demo to prove the concept and secure approval for real data collection.

Tech stack: Next.js 14 + FastAPI (Python 3.11) + YOLOv8m (Ultralytics)

---

## Folder Structure

```
safety-ppe-checker/
├── project-context.md              # READ FIRST
├── glossary.md                     # Domain terms
├── backlog.md                      # Backlog
└── docs/
    ├── 01_product_requirements/
    │   ├── prd/
    │   │   └── PRD-safety-ppe-checker.md
    │   ├── web-interface/
    │   │   ├── EPIC-WEB-001.md
    │   │   └── US-WEB-*.md
    │   └── cv-engine/
    │       ├── EPIC-CV-001.md
    │       └── US-CV-*.md
    ├── 02_technical_specs/
    │   ├── architecture.md
    │   └── cv-engine/
    │       └── TP-CV-001.md
    ├── 03_plans/
    └── 04_testing/
```

---

## Rules

### General
- Read `project-context.md` before any task
- This is a demo/POC — keep it simple, avoid over-engineering
- English for code and technical docs; Vietnamese acceptable for comments

### Code Rules
- Python: PEP8, type hints, Pydantic models for API schemas
- TypeScript: functional components, no `any` type
- Never commit `.pt` model weight files or `.env` files to git

### Source Code Layout (when building)
```
src/
  backend/
    main.py           ← FastAPI app entrypoint
    detector.py       ← YOLOv8 inference wrapper
    compliance.py     ← PPE compliance rule engine
    models.py         ← Pydantic request/response schemas
  frontend/
    app/page.tsx      ← Main upload + results page
    components/
      UploadZone.tsx
      ComplianceReport.tsx
      AnnotatedImage.tsx
  docker-compose.yml
  .env.example
```

---

## Navigation

- [Project context](./project-context.md)
- [Glossary](./glossary.md)
- [Backlog](./backlog.md)
- [PRD](./docs/01_product_requirements/prd/PRD-safety-ppe-checker.md)
- [Architecture](./docs/02_technical_specs/architecture.md)
- [CV Tech Spec](./docs/02_technical_specs/cv-engine/TP-CV-001.md)
