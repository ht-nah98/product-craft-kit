# Testing Docs

Folder chứa tài liệu kiểm thử: test strategy, test guides, và test cases.

---

## Structure

```
04_testing/
├── test-strategy.md            # Overall test strategy for the project
└── [module-name]/              # Per-module test guides
    └── test-guide-[feature].md # Test guide per feature/epic
```

---

## Document Types

| Type | Template |
|------|----------|
| Test Strategy | `_template_test_strategy.md` |
| Test Guide | `_template_test_guide.md` |

Templates in: `.agent/resources/templates/05_testing_docs/`

---

## Rules

- One test strategy per project (singleton)
- Test guides are per Epic or major feature
- Test guides link to Acceptance Criteria in User Stories
- Cover: unit, integration, E2E, and manual testing scope
