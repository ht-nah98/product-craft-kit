# Product Craft Kit

> 🌐 **Language / Ngôn ngữ**: [English](README.md) | [Tiếng Việt](README_vi.md)

> 🚀 A comprehensive methodology & documentation framework for building products - from Discovery to Scale

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Language](https://img.shields.io/badge/Language-EN%20%7C%20VI-blue.svg)](README_vi.md)

---

## What is this?

A complete system for:
- **📝 Product Documentation** - Structured templates for PRD, Epic, User Story, etc.
- **🚀 Product Building** - 5-phase methodology (Discover → Define → Develop → Deliver → Scale)
- **🤖 AI Agent Development** - Patterns and architecture for building AI agents

Designed to work seamlessly with AI assistants (like Gemini/Claude) following **Google Antigravity** standards.

---

## Quick Start

### For AI Assistant (Gemini/Claude)

1. Open this workspace
2. AI will automatically read `GEMINI.md` for instructions
3. Use slash commands:
   - `/new-project` - Create new project
   - `/discovery` - Start research phase
   - `/define-problem` - Define problem
   - `/shape-solution` - Design solution
   - `/build-agent` - Build AI Agent

### For Humans

1. Browse `.agent/skills/` to understand methodologies (Note: hidden folder)
2. Use templates in `.agent/resources/templates/`
3. Create projects in `projects/` folder

---

## New Structure (Antigravity Standard)

```
.
├── GEMINI.md                   # AI instructions (read first)
├── .agent/                     # (Hidden) Core system
│   ├── skills/                 # Atomic Skills (One folder per skill)
│   │   ├── write_user_story/   # User story skill
│   │   ├── product_discovery/  # Discovery skill
│   │   └── ...
│   ├── resources/              # Shared resources
│   │   ├── templates/          # Document templates
│   │   ├── knowledge/          # Methodology references
│   │   └── system_evolution/   # Gaps & Lessons data
│   └── workflows/              # Slash command definitions
└── projects/                   # Your projects go here
    └── _project-template/      # Template for new projects
```

---

## Skills Overview

### 📝 Documentation Skills
| Skill | Purpose |
|-------|---------|
| `write_epic` | Large feature specification |
| `write_user_story` | Individual feature requirements |
| `write_prd` | Product Requirements Document |
| `write_acceptance_criteria` | Acceptance Criteria |
| `backlog_management` | Priority and planning |

### 🚀 Product Building Skills (5 Phases)
| Phase | Skill | Output |
|-------|-------|--------|
| 1. Discover | `product_discovery` | Research findings |
| 2. Define | `problem_definition` | Problem canvas |
| 3. Develop | `solution_shaping` | Shaped solution |
| 4. Deliver | `build_and_ship` | Launch checklist |
| 5. Scale | `product_iteration` | Iteration plan |

### 🤖 AI Agent Skills
| Skill | Purpose |
|-------|---------|
| `agent_discovery` | Problem validation, user analysis |
| `agent_architecture` | Pattern selection, component design |
| `agent_patterns` | Implementation reference |

---

## Workflows (Slash Commands)

| Command | Description |
|---------|-------------|
| `/new-project` | Create new project from template |
| `/write-prd` | Write PRD document |
| `/write-user-story` | Write User Story |
| `/discovery` | Start Discovery phase |
| `/define-problem` | Define Problem phase |
| `/shape-solution` | Shape Solution phase |
| `/launch-checklist` | Pre-launch checklist |
| `/build-agent` | Build AI Agent workflow |

---

## Creating a New Project

```bash
# Copy template
cp -r projects/_project-template projects/your-project-name

# Edit project context
vim projects/your-project-name/project-context.md
```

Or use `/new-project` command with AI assistant.

---

## Methodologies Included

### Product Building Methodology
Based on:
- **Shape Up** (Basecamp) - Appetite-driven development
- **Lean Startup** - Build-Measure-Learn
- **Jobs to be Done** - Problem-focused thinking
- **Design Thinking** - Human-centered approach

### AI Agent Building Methodology
Core principles:
- Start Narrow, Scale Later
- Hybrid Architecture (LLM + Deterministic)
- Infrastructure First
- Domain Expert > Generic
- Reusable Components
- Measure Everything

---

## License

MIT License - See [LICENSE](LICENSE) file

---

## Contributing

Contributions welcome! Please read the methodology docs in `.agent/resources/knowledge/` first.
