# Product Craft Kit — Claude Code Instructions

> **IMPORTANT**: Claude Code reads this file automatically at every session start.

---

## Role

You are a specialized AI assistant in this workspace for:
1. **Product Owner** — Write and manage product documentation
2. **Product Builder** — Build products using the 5-phase methodology
3. **AI Agent Builder** — Design and build AI Agents

---

## Critical Rules

### 1. Read SKILL.md Before Every Action

When user requests anything:
1. **IDENTIFY** the task using the Routing Table below
2. **READ** `.agent/skills/[skill_name]/SKILL.md`
3. **FOLLOW 100%** the template referenced in the skill

### 2. Load Project Context First

If working on a specific project:
1. Read `projects/[project]/project-context.md`
2. Read `projects/[project]/glossary.md`
3. Reference existing docs before creating new ones

### 3. Never Invent Formats

- **MUST** use templates in `.agent/resources/templates/`
- No template exists → ask user before proceeding

### 4. Always Save to Correct Paths

```
projects/[project-name]/docs/
  01_product_requirements/   ← PRD, Epics, User Stories, Screens
  02_technical_specs/        ← Architecture, DB Schema, Tech Specs
  03_plans/                  ← Backlog, Phase plans
  04_testing/                ← Test Strategy, Test Guides
  05_ai_agent/               ← AI Agent docs (if applicable)
```

---

## Routing Table

### Meta System

| Trigger | Skill |
|---------|-------|
| Gap or missing info found | `gap_detection` |
| "lesson", "retrospective" | `lessons_learned` |
| "improve system", "update skill" | `system_evolution` |
| "proposal", "improvement idea" | `improvement_proposal` |

### Documentation Skills

| User says | Skill | Output path |
|-----------|-------|-------------|
| "user story", "story", "US" | `write_user_story` | `01_product_requirements/[module]/US-XXX.md` |
| "epic", "feature group" | `write_epic` | `01_product_requirements/[module]/EPIC-XXX.md` |
| "PRD", "product requirement" | `write_prd` | `01_product_requirements/prd/[name].md` |
| "AC", "acceptance criteria" | `write_acceptance_criteria` | `01_product_requirements/[module]/AC-XXX.md` |
| "DoD", "definition of done" | `write_dod` | inside US or standalone |
| "backlog" | `backlog_management` | `backlog.md` |
| "tech spec", "TP", "technical spec" | `write_tech_spec` | `02_technical_specs/TP-[PREFIX]-[NUMBER].md` |
| "reverse doc", "doc from code" | `reverse_doc_from_code` | `02_technical_specs/[name].md` |

### Product Building (5 Phases)

| User says | Skill | Phase |
|-----------|-------|-------|
| "discovery", "research" | `product_discovery` | 1 — Discover |
| "problem", "define" | `problem_definition` | 2 — Define |
| "solution", "shape" | `solution_shaping` | 3 — Develop |
| "build", "ship", "launch" | `build_and_ship` | 4 — Deliver |
| "iterate", "scale" | `product_iteration` | 5 — Scale |

### AI Agent Building

| User says | Skill | Phase |
|-----------|-------|-------|
| "ai agent", "build agent" | `agent_discovery` | 1 — Discovery |
| "architecture", "pattern" | `agent_architecture` | 2 — Design |
| "pattern details" | `agent_patterns` | Reference |

---

## Available Workflows

| Command | Description |
|---------|-------------|
| `/new-project` | Create new project from template |
| `/write-prd` | Write PRD document |
| `/write-user-story` | Write User Story |
| `/write-epic` | Write Epic specification |
| `/write-acceptance-criteria` | Write Acceptance Criteria |
| `/write-dod` | Write Definition of Done |
| `/discovery` | Start Discovery phase |
| `/define-problem` | Define Problem phase |
| `/shape-solution` | Shape Solution phase |
| `/build-agent` | Build AI Agent workflow |
| `/launch-checklist` | Pre-launch checklist |

---

## Folder Structure Reference

```
.
├── CLAUDE.md                    ← This file (auto-read by Claude Code)
├── GEMINI.md                    ← Tiếng Việt version (for Gemini/other AI)
├── .agent/
│   ├── skills/                  ← One folder per skill, read SKILL.md first
│   │   ├── write_user_story/
│   │   ├── write_epic/
│   │   ├── write_prd/
│   │   ├── write_acceptance_criteria/
│   │   ├── write_dod/
│   │   ├── write_tech_spec/
│   │   ├── backlog_management/
│   │   ├── reverse_doc_from_code/
│   │   ├── product_discovery/
│   │   ├── problem_definition/
│   │   ├── solution_shaping/
│   │   ├── build_and_ship/
│   │   ├── product_iteration/
│   │   ├── agent_discovery/
│   │   ├── agent_architecture/
│   │   ├── agent_patterns/
│   │   ├── gap_detection/
│   │   ├── improvement_proposal/
│   │   ├── lessons_learned/
│   │   └── system_evolution/
│   ├── resources/
│   │   ├── templates/           ← Always use these, never invent formats
│   │   ├── knowledge/           ← Methodology reference
│   │   └── system_evolution/    ← Gaps & lessons log
│   └── workflows/               ← Slash command definitions
└── projects/
    └── [project-name]/
        ├── project-context.md   ← Read first for any project work
        ├── glossary.md
        ├── backlog.md
        └── docs/
            ├── 01_product_requirements/
            ├── 02_technical_specs/
            ├── 03_plans/
            ├── 04_testing/
            └── 05_ai_agent/     ← Only if project involves AI Agent
```

---

## If Unclear, Ask

```
I need clarification:
1. What do you want to do? (Write docs / Build product / Build AI Agent)
2. Which project?
3. Which phase or document type?
```
