# EPIC-CV-001: AI PPE Detection Engine

> AI backend phát hiện PPE từ ảnh toàn thân và tạo compliance report

---

## 1. Thông tin chung

| Mục | Nội dung |
|-----|----------|
| Epic ID | EPIC-CV-001 |
| Module | CV Engine + Backend API |
| Status | 📝 Draft |
| Priority | 🔴 Critical |
| Phase | Phase 1 — Demo |

---

## 2. Tổng quan

### Bối cảnh
Đây là core của toàn bộ hệ thống. Nhận ảnh toàn thân nhân viên, chạy YOLOv8 inference, áp dụng compliance rules, và trả kết quả về cho frontend.

### Mục tiêu
- Phát hiện chính xác 5 PPE items với ≥ 85% accuracy
- Inference ≤ 3 giây trên CPU
- API đơn giản, dễ gọi từ frontend
- Dễ extend để thêm PPE classes trong Phase 2

### Business Value
Đây là phần chứng minh tính khả thi của toàn bộ dự án. Nếu model detect đúng → demo thành công.

---

## 3. Phạm vi

### In-scope ✅
- FastAPI backend với endpoint `/api/analyze`
- YOLOv8m inference wrapper (detector.py)
- Compliance rule engine (5 required PPE items)
- Image annotation với OpenCV (vẽ bounding boxes)
- Response: annotated image (base64) + JSON compliance report
- Health check endpoint `/api/health`
- Docker containerization

### Out-of-scope ❌
- Database / persistence
- Worker identity recognition
- PPE quality/rating classification
- Real-time video stream
- Multi-person detection
- Batch processing

---

## 4. Detection Classes (Phase 1)

| # | Class Name | Label trong model | Required? |
|---|------------|-------------------|-----------|
| 1 | Helmet | `Hardhat` | YES |
| 2 | Safety Vest | `Safety Vest` | YES |
| 3 | Gloves | `Gloves` | YES |
| 4 | Safety Goggles | `Safety Goggles` | YES |
| 5 | Safety Boots | `Boots` | YES |

**Negative classes** (also detected but flip compliance): `NO-Hardhat`, `NO-Safety Vest`, `NO-Gloves`, `NO-Safety Goggles`, `NO-Boots`

---

## 5. User Stories

| Story ID | Tên | Priority | Points |
|----------|-----|----------|--------|
| [US-CV-001](./US-CV-001.md) | Detect PPE items từ ảnh upload | Must Have | 5 |
| [US-CV-002](./US-CV-002.md) | Tạo compliance report (PASS/FAIL) | Must Have | 3 |
| [US-CV-003](./US-CV-003.md) | Trả về ảnh annotated (base64) | Must Have | 3 |

**Total: 11 points**

---

## 6. API Contract

### POST `/api/analyze`

**Request:**
```
Content-Type: multipart/form-data
Body: file (image/jpeg | image/png | image/webp, max 10MB)
```

**Response 200:**
```json
{
  "status": "FAIL",
  "overall_pass": false,
  "missing_items": ["Gloves", "Safety Goggles"],
  "detections": [
    {
      "label": "Hardhat",
      "confidence": 0.92,
      "bbox": [x1, y1, x2, y2],
      "detected": true
    },
    {
      "label": "Gloves",
      "confidence": 0.0,
      "bbox": null,
      "detected": false
    }
  ],
  "annotated_image": "<base64_encoded_jpeg>",
  "inference_time_ms": 1240
}
```

**Response 400:** Invalid file format or size
**Response 500:** Inference error

### GET `/api/health`
```json
{ "status": "ok", "model": "yolov8m", "version": "1.0.0" }
```

---

## 7. Compliance Logic

```python
REQUIRED_PPE = ["Hardhat", "Safety Vest", "Gloves", "Safety Goggles", "Boots"]

def assess_compliance(detections):
    detected_labels = {d.label for d in detections if d.confidence >= THRESHOLD}
    missing = [ppe for ppe in REQUIRED_PPE if ppe not in detected_labels]
    return {
        "overall_pass": len(missing) == 0,
        "missing_items": missing
    }
```

---

## 8. Definition of Done

- [ ] `/api/analyze` nhận ảnh và trả JSON response đúng format
- [ ] `/api/health` hoạt động
- [ ] YOLOv8m model load thành công khi startup
- [ ] Detect đúng 5 PPE classes trên test images
- [ ] Inference time ≤ 3 giây trên CPU
- [ ] Annotated image trong response có bounding boxes rõ ràng
- [ ] Confidence threshold = 0.5 applied
- [ ] Error handling cho file không hợp lệ
- [ ] Docker container build và run thành công

---

## Related
- [PRD](../prd/PRD-safety-ppe-checker.md)
- [TP-CV-001 — CV Pipeline Tech Spec](../../02_technical_specs/cv-engine/TP-CV-001.md)
- [EPIC-WEB-001](../web-interface/EPIC-WEB-001.md)
