# AI Agent Docs

Folder chứa tài liệu thiết kế AI Agent (chỉ dùng nếu project xây dựng AI Agent).

---

## Structure

```
05_ai_agent/
├── phase1_problem_canvas.md    # Agent problem definition
├── phase2_architecture.md      # Agent architecture design
└── components/                 # Per-component specs
    └── [component-name].md
```

---

## Document Types

| Type | Template |
|------|----------|
| Agent Problem Canvas | `_template_agent_problem.md` |
| Agent Architecture | `_template_agent_architecture.md` |
| Component Spec | `_template_agent_component.md` |

Templates in: `.agent/resources/templates/07_ai_agent/`

---

## AI Agent Building Phases

| Phase | Document | Skill |
|-------|----------|-------|
| 1. Discovery | `phase1_problem_canvas.md` | `agent_discovery` |
| 2. Architecture | `phase2_architecture.md` | `agent_architecture` |
| 3. Implementation | `components/[name].md` | `agent_patterns` |

---

## Rules

- Only create this folder if your project involves building an AI Agent
- Follow the 3-phase methodology: Discovery → Architecture → Build
- Each component gets its own spec file
- Use `/build-agent` workflow to start
