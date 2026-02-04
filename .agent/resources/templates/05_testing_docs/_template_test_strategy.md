# Template: Tổng quan Chiến lược Test

> Tài liệu mô tả chiến lược testing tổng quan cho dự án.

---

## 1. Mục tiêu

| Mục tiêu | Mô tả |
|----------|-------|
| **Độ tin cậy cao** | [Mô tả yêu cầu về độ tin cậy] |
| **Phát hiện Edge cases** | [Mô tả các tình huống biên cần kiểm tra] |
| **Regression testing** | Đảm bảo code mới không phá vỡ chức năng cũ |
| **Documentation** | Test như living documentation cho behaviors |
| **Confidence** | Tự tin khi deploy và refactor code |

---

## 2. Nguyên tắc cốt lõi

| Nguyên tắc | Mô tả |
|------------|-------|
| **Test Pyramid** | Unit Tests > Integration Tests > E2E Tests |
| **FIRST** | Fast, Isolated, Repeatable, Self-validating, Timely |
| **AAA** | Arrange-Act-Assert pattern |
| **Given-When-Then** | BDD-style tests cho readability |

---

## 3. Test Pyramid

```
┌─────────────────────────────────────────────────────────────────┐
│                        E2E Tests (5%)                            │
│              Full workflow, critical user journeys               │
├─────────────────────────────────────────────────────────────────┤
│                  Integration Tests (25%)                         │
│     API endpoints, database, external services                   │
├─────────────────────────────────────────────────────────────────┤
│                    Unit Tests (70%)                              │
│    Domain logic, Handlers, Validators, Services                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 4. Test Layers

| Layer | Loại Test | Mục đích |
|-------|-----------|----------|
| **Domain** | Unit Tests | Business rules, Entities, Value Objects |
| **Application** | Unit Tests | Handlers, Validators, DTOs mapping |
| **Infrastructure** | Integration Tests | Repositories, External Services, Database |
| **Presentation** | Integration Tests | Controllers, API endpoints, Authorization |

---

## 5. Chiến lược cho từng Module

### [Module 1]

```
├── Domain Tests        → Test [entities, rules]
├── Application Tests   → Test [handlers, validators]
├── Integration Tests   → Test [API endpoints]
└── Authorization Tests → Test [permissions]
```

### [Module 2] (nếu chưa phát triển)

```
└── Áp dụng TDD từ đầu - viết test trước khi code
```

---

## 6. Coverage Targets

| Layer | Target | Mô tả |
|-------|--------|-------|
| **Domain** | 90%+ | Critical business logic |
| **Application** | 85%+ | Use cases và handlers |
| **Infrastructure** | 70%+ | Repositories, external services |
| **Presentation** | 80%+ | Controllers, authorization |
| **Overall** | 80%+ | Toàn bộ codebase |

### Critical Paths (100% coverage required)

| Path | Lý do |
|------|-------|
| [Critical path 1] | [Lý do cần 100% coverage] |
| [Critical path 2] | [Lý do] |
| Authorization | Bảo mật |
| Data validation | Data integrity |

### Coverage Exclusions

- Auto-generated code
- Configuration/startup code
- Constants và Enums
- [Các loại khác]

---

## 7. CI/CD Integration

### Test Pipeline

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│ Unit Tests  │ -> │ Integration │ -> │ [Optional]  │ -> │  Coverage   │
│   (fast)    │    │   Tests     │    │Arch Tests   │    │   Report    │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
                                │
                                ▼
                         ┌─────────────┐
                         │   Deploy    │
                         │  (if pass)  │
                         └─────────────┘
```

### Quality Gates

| Gate | Threshold | Action |
|------|-----------|--------|
| Unit Tests Pass | 100% | Block merge |
| Integration Tests Pass | 100% | Block merge |
| Code Coverage | 80%+ | Warning (block if < 70%) |

---

## Tài liệu liên quan

- [Kiến trúc Test](./architecture.md)
- [Công nghệ sử dụng](./technologies.md)
- [Unit Tests](./unit_tests.md)
- [Integration Tests](./integration_tests.md)
- [Edge Cases](./edge_cases.md)
- [Conventions](./conventions.md)

