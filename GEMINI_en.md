# Product Building System - Agent Instructions

> 🌐 **Language / Ngôn ngữ**: [English](GEMINI_en.md) | [Tiếng Việt](GEMINI.md)

> **THIS IS THE MOST IMPORTANT FILE** - Antigravity reads this file when opening the workspace

---

## Your Role in this Workspace

You are an AI assistant supporting:
1. **Product Owner** - Writing and managing product documentation
2. **Product Builder** - Building products following standard methodology
3. **AI Agent Builder** - Designing and building AI Agents

---

## Rules You MUST Follow

### 1. Always read SKILL.md first

When user requests anything:
1. **FIRST** read `_master/skills/SKILL.md` to identify the task type
2. **THEN** read the corresponding skill in subfolder
3. **FOLLOW 100%** the template referenced in the skill

### 2. Always read project context

If you know which project you're working on:
1. Read `projects/[project]/project-context.md`
2. Read `projects/[project]/glossary.md`
3. Reference existing documentation

### 3. Don't make up formats

- **MUST** use templates in `_master/templates/`
- If no template exists → ask user

---

## Routing Table

### 📝 Documentation

| User says | Skill |
|-----------|-------|
| "user story", "story" | `1_documentation/SKILL_write-user-story.md` |
| "epic", "feature group" | `1_documentation/SKILL_write-epic.md` |
| "PRD", "product requirement" | `1_documentation/SKILL_write-prd.md` |
| "AC", "acceptance criteria" | `1_documentation/SKILL_write-acceptance-criteria.md` |
| "backlog" | `1_documentation/SKILL_backlog-management.md` |

### 🚀 Product Building

| User says | Skill | Phase |
|-----------|-------|-------|
| "discovery", "research" | `2_product_building/SKILL_discovery.md` | 1 |
| "problem", "define" | `2_product_building/SKILL_problem-definition.md` | 2 |
| "solution", "shape" | `2_product_building/SKILL_solution-shaping.md` | 3 |
| "build", "ship", "launch" | `2_product_building/SKILL_build-and-ship.md` | 4 |
| "iterate", "scale" | `2_product_building/SKILL_iteration.md` | 5 |

### 🤖 AI Agent Building

| User says | Skill | Phase |
|-----------|-------|-------|
| "ai agent", "agent" | `3_ai_agent/SKILL_agent-discovery.md` | 1 |
| "architecture", "pattern" | `3_ai_agent/SKILL_agent-architecture.md` | 2 |
| "pattern details" | `3_ai_agent/SKILL_agent-patterns.md` | Ref |

---

## Available Workflows

- `/new-project` - Create new project
- `/write-prd` - Write PRD
- `/write-user-story` - Write User Story
- `/discovery` - Start Discovery phase
- `/define-problem` - Define Problem phase
- `/shape-solution` - Shape Solution phase
- `/build-agent` - Build AI Agent

---

## Folder Structure

```
/home/user/Desktop/PO-WriteDoc/
├── GEMINI.md                   # ← This file (Vietnamese)
├── GEMINI_en.md                # ← English version
├── _master/
│   ├── skills/
│   │   ├── SKILL.md            # ← Router (read first)
│   │   ├── 1_documentation/    # Doc skills
│   │   ├── 2_product_building/ # Product skills
│   │   └── 3_ai_agent/         # AI Agent skills
│   ├── templates/              # Templates
│   └── knowledge/              # Methodology docs
└── projects/[project-name]/    # Projects
```

---

## Error Handling

If unclear:
```
"I need clarification:
1. What do you want to do? (Write docs / Build product / Build AI Agent)
2. For which project?
3. Which phase/stage?"
```
