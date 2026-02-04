# Template: Hướng dẫn viết [Loại Test]

> Hướng dẫn chi tiết cách viết [Unit Tests / Integration Tests / ...] cho dự án.

---

## 1. Tổng quan

### 1.1. Mục đích
[Mô tả mục đích của loại test này]

### 1.2. Phạm vi
[Mô tả phạm vi: test cái gì, không test cái gì]

---

## 2. Cấu trúc thư mục

```
tests/
├── [TestProject]/
│   ├── [Layer1]/
│   │   ├── [Subject1]Tests.cs
│   │   └── [Subject2]Tests.cs
│   └── [Layer2]/
│       └── ...
```

---

## 3. Quy tắc đặt tên

### 3.1. Test Class

```
[Subject]Tests

Ví dụ:
- UserServiceTests
- OrderValidatorTests
- PaymentControllerTests
```

### 3.2. Test Method

```
[Method]_[Scenario]_[ExpectedResult]

Ví dụ:
- Create_WithValidInput_ReturnsSuccess
- Validate_WithEmptyName_ThrowsValidationException
- GetById_WhenNotFound_ReturnsNotFound
```

---

## 4. Pattern cơ bản

### 4.1. Arrange-Act-Assert (AAA)

```
// Arrange
[Setup test data và dependencies]

// Act
[Thực hiện action cần test]

// Assert
[Verify kết quả]
```

### 4.2. Given-When-Then (BDD Style)

```
// Given [initial context]
[Setup]

// When [action occurs]
[Execute]

// Then [expected outcome]
[Assert]
```

---

## 5. Test Cases theo Category

### 5.1. Happy Path

| Scenario | Input | Expected Output |
|----------|-------|-----------------|
| [Mô tả scenario] | [Valid input] | [Expected result] |

### 5.2. Validation Errors

| Scenario | Input | Expected Error |
|----------|-------|----------------|
| [Mô tả scenario] | [Invalid input] | [Expected error message] |

### 5.3. Edge Cases

| Scenario | Input | Expected Behavior |
|----------|-------|-------------------|
| [Mô tả edge case] | [Edge input] | [Expected behavior] |

### 5.4. Authorization

| Scenario | User Role | Expected |
|----------|-----------|----------|
| [Action] | [Role với quyền] | Success |
| [Action] | [Role không có quyền] | Forbidden |

---

## 6. Mocking Guidelines

### 6.1. Khi nào Mock

| Component | Mock? | Lý do |
|-----------|-------|-------|
| Database | [Yes/No] | [Lý do] |
| External API | [Yes/No] | [Lý do] |
| [Component khác] | [Yes/No] | [Lý do] |

### 6.2. Cách Mock

```
[Code example cho mocking]
```

---

## 7. Test Data

### 7.1. Test Data Strategy

| Strategy | Khi sử dụng |
|----------|-------------|
| [Strategy 1] | [Use case] |
| [Strategy 2] | [Use case] |

### 7.2. Builders / Factories

```
[Code example cho test data builders]
```

---

## 8. Checklist trước khi commit

- [ ] Tất cả tests pass
- [ ] Test coverage đạt target
- [ ] Test names rõ ràng và descriptive
- [ ] Không có hard-coded values không cần thiết
- [ ] Tests độc lập với nhau (Isolated)
- [ ] Tests có thể chạy lại nhiều lần (Repeatable)

---

## Tài liệu liên quan

- [Tổng quan chiến lược test](./overview.md)
- [Conventions](./conventions.md)
- [Edge Cases](./edge_cases.md)

