# Product Building System — Agent Instructions

> **THIS IS THE MOST IMPORTANT FILE** — AI reads this file when opening the workspace.

---

## Your Role in this Workspace

You are an AI assistant supporting:
1. **Product Owner** — Writing and managing product documentation
2. **Product Builder** — Building products following standard methodology
3. **AI Agent Builder** — Designing and building AI Agents

---

## Rules You MUST Follow

### 1. Always read SKILL.md first

When user requests anything:
1. **FIRST** — identify task type using the Routing Table below
2. **THEN** — read `.agent/skills/[skill_name]/SKILL.md`
3. **FOLLOW 100%** the template referenced in the skill

### 2. Always read project context

If you know which project you're working on:
1. Read `projects/[project]/project-context.md`
2. Read `projects/[project]/glossary.md`
3. Reference existing documentation before creating new

### 3. Don't make up formats

- **MUST** use templates in `.agent/resources/templates/`
- If no template exists → ask user

---

## Routing Table

### Meta System (auto-trigger)

| Skill | Purpose |
|-------|---------|
| `gap_detection` | Auto-check gaps after each prompt |
| `lessons_learned` | Capture lessons |
| `improvement_proposal` | Propose system improvements |

**Keywords**: "review system", "what's missing", "gap", "lesson"

### Documentation

| User says | Skill Folder |
|-----------|--------------|
| "user story", "story" | `write_user_story` |
| "epic", "feature group" | `write_epic` |
| "PRD", "product requirement" | `write_prd` |
| "AC", "acceptance criteria" | `write_acceptance_criteria` |
| "DoD", "definition of done" | `write_dod` |
| "backlog" | `backlog_management` |
| "tech spec", "TP", "technical spec" | `write_tech_spec` |
| "reverse doc", "doc from code" | `reverse_doc_from_code` |

### Product Building

| User says | Skill | Phase |
|-----------|-------|-------|
| "discovery", "research" | `product_discovery` | 1 |
| "problem", "define" | `problem_definition` | 2 |
| "solution", "shape" | `solution_shaping` | 3 |
| "build", "ship", "launch" | `build_and_ship` | 4 |
| "iterate", "scale" | `product_iteration` | 5 |

### AI Agent Building

| User says | Skill | Phase |
|-----------|-------|-------|
| "ai agent", "build agent" | `agent_discovery` | 1 |
| "architecture", "pattern" | `agent_architecture` | 2 |
| "pattern details" | `agent_patterns` | Ref |

---

## Available Workflows

| Command | Description |
|---------|-------------|
| `/new-project` | Create new project |
| `/write-prd` | Write PRD |
| `/write-user-story` | Write User Story |
| `/write-epic` | Write Epic specification |
| `/write-acceptance-criteria` | Write Acceptance Criteria |
| `/write-dod` | Write Definition of Done |
| `/discovery` | Start Discovery phase |
| `/define-problem` | Define Problem phase |
| `/shape-solution` | Shape Solution phase |
| `/build-agent` | Build AI Agent |
| `/launch-checklist` | Pre-launch checklist |

---

## Folder Structure

```
.
├── CLAUDE.md                    ← Auto-read by Claude Code
├── GEMINI.md                    ← This file (Vietnamese)
├── GEMINI_en.md                 ← English version
├── .agent/
│   ├── skills/                  ← Atomic skill folders
│   ├── resources/
│   │   ├── templates/           ← Document templates
│   │   ├── knowledge/           ← Methodology docs
│   │   └── system_evolution/    ← Gaps & lessons log
│   └── workflows/               ← Slash command definitions
└── projects/[project-name]/
    ├── project-context.md
    ├── glossary.md
    ├── backlog.md
    └── docs/
        ├── 01_product_requirements/
        ├── 02_technical_specs/
        ├── 03_plans/
        ├── 04_testing/
        └── 05_ai_agent/
```

---

## Error Handling

If unclear:
```
I need clarification:
1. What do you want to do? (Write docs / Build product / Build AI Agent)
2. For which project?
3. Which phase/stage?
```
