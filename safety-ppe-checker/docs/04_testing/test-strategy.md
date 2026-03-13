# Test Strategy — Safety PPE Checker

> **Phase**: 1 — Demo/POC
> **Scope**: Backend API, CV detection engine, Frontend UI

---

## 1. Testing Goals

| Goal | Mô tả |
|------|-------|
| **Correctness** | AI detect đúng PPE items, compliance logic đúng |
| **Reliability** | API hoạt động ổn định, xử lý đúng edge cases |
| **Performance** | Inference ≤ 3 giây trên CPU demo laptop |
| **Usability** | UI hoạt động đúng trên Chrome/Firefox |

---

## 2. Test Levels

### Level 1 — Unit Tests (Developer)
- **Scope**: Từng function độc lập
- **Tools**: `pytest` (Python), `jest` (TypeScript)
- **Coverage target**: ≥ 80% cho compliance engine và detector
- **Runs**: Mỗi lần commit (local) và CI

### Level 2 — Integration Tests (Developer)
- **Scope**: API endpoint end-to-end (upload → response)
- **Tools**: `pytest` + `httpx` (async API client)
- **Runs**: Trước mỗi demo, sau mỗi thay đổi major

### Level 3 — Model Accuracy Tests (Developer / Data)
- **Scope**: Đánh giá độ chính xác của YOLOv8m trên test image set
- **Tools**: Ultralytics `val()`, custom evaluation script
- **Runs**: Khi thay đổi model weights hoặc thêm PPE class

### Level 4 — Manual / Exploratory Testing (Demo Prep)
- **Scope**: UI/UX trên browser thực, demo flow end-to-end
- **Tools**: Browser manual testing
- **Runs**: Trước mỗi demo presentation

---

## 3. Test Environments

| Environment | Mục đích | Setup |
|-------------|----------|-------|
| Local (developer laptop) | Unit + integration tests | `docker compose up` |
| Demo laptop | Pre-demo validation | `docker compose up`, Chrome/Firefox |

---

## 4. Test Data

### Backend test images (cần chuẩn bị)

| File | Scenario | Expected Result |
|------|----------|-----------------|
| `test_all_ppe.jpg` | Nhân viên mặc đủ 5 PPE | PASS, 0 missing items |
| `test_no_helmet.jpg` | Thiếu Helmet | FAIL, missing=["Helmet"] |
| `test_no_gloves.jpg` | Thiếu Gloves | FAIL, missing=["Gloves"] |
| `test_multiple_missing.jpg` | Thiếu Helmet + Goggles | FAIL, missing=["Helmet","Safety Goggles"] |
| `test_no_ppe.jpg` | Không mặc gì | FAIL, missing=[all 5] |
| `test_low_confidence.jpg` | Vest barely visible (confidence ~55%) | PASS nhưng cảnh báo low confidence |
| `test_non_person.jpg` | Ảnh không có người | FAIL hoặc error handled gracefully |
| `test_corrupt.bin` | File corrupt (không phải ảnh) | HTTP 400 |
| `test_large.jpg` | File > 10MB | HTTP 413 |

Lưu tại: `tests/fixtures/images/`

---

## 5. Definition of Test Pass

| Level | Pass criteria |
|-------|---------------|
| Unit tests | 100% pass, coverage ≥ 80% |
| Integration tests | 100% pass trên test image set |
| Model accuracy | mAP@0.5 ≥ 85% trên test set |
| Manual | Tất cả happy path và critical error paths hoạt động đúng |

---

## 6. Test Files Location

```
tests/
  fixtures/
    images/             ← test images (xem danh sách ở trên)
  unit/
    test_compliance.py  ← Unit tests cho compliance engine
    test_detector.py    ← Unit tests cho detector wrapper
    test_annotator.py   ← Unit tests cho image annotator
  integration/
    test_api.py         ← Integration tests cho /api/analyze
  model/
    test_accuracy.py    ← Model accuracy evaluation
```

---

## 7. Risk Areas (cần test kỹ)

| Risk | Lý do | Test focus |
|------|-------|------------|
| Compliance logic sai | PASS khi thiếu PPE = nguy hiểm thực sự | Test mọi combination |
| Model không detect được trên ảnh thực | Domain shift từ construction → electrical | Test với ảnh đa dạng góc, ánh sáng |
| Base64 encoding lỗi | Frontend không render được ảnh | Unit test decode/encode round-trip |
| File upload lớn crash server | DoS / memory overflow | Test giới hạn 10MB |
| CORS block API calls | Demo fail tại chỗ | Test cross-origin request |
