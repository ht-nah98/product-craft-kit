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

Designed to work seamlessly with AI assistants (like Gemini/Claude) to help Product Owners and builders work efficiently.

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

1. Browse `_master/skills/` to understand methodologies
2. Use templates in `_master/templates/`
3. Create projects in `projects/` folder

---

## Structure

```
.
├── GEMINI.md                   # AI instructions (read first)
├── _master/
│   ├── skills/
│   │   ├── SKILL.md            # Router (main entry)
│   │   ├── 1_documentation/    # PO documentation skills
│   │   ├── 2_product_building/ # Product lifecycle skills
│   │   └── 3_ai_agent/         # AI agent building skills
│   ├── templates/              # Document templates
│   └── knowledge/              # Methodology references
├── projects/                   # Your projects go here
│   └── _project-template/      # Template for new projects
└── .agent/workflows/           # Slash command definitions
```

---

## Skills Overview

### 📝 Documentation Skills
| Skill | Purpose |
|-------|---------|
| Write Epic | Large feature specification |
| Write User Story | Individual feature requirements |
| Write PRD | Product Requirements Document |
| Write AC | Acceptance Criteria |
| Backlog Management | Priority and planning |

### 🚀 Product Building Skills (5 Phases)
| Phase | Skill | Output |
|-------|-------|--------|
| 1. Discover | Research & Insights | Research findings |
| 2. Define | Problem Definition | Problem canvas |
| 3. Develop | Solution Shaping | Shaped solution |
| 4. Deliver | Build & Ship | Launch checklist |
| 5. Scale | Iteration | Iteration plan |

### 🤖 AI Agent Skills
| Skill | Purpose |
|-------|---------|
| Agent Discovery | Problem validation, user analysis |
| Agent Architecture | Pattern selection, component design |
| Agent Patterns | Implementation reference |

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

Contributions welcome! Please read the methodology docs in `_master/knowledge/` first.
