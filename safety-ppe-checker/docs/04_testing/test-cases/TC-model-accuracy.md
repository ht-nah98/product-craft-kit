# Test Cases — CV Model Accuracy

> **File**: `tests/model/test_accuracy.py`
> **Tools**: Ultralytics val(), custom evaluation script

---

## Mục đích

Đánh giá độ chính xác của YOLOv8m pre-trained model trên các loại ảnh khác nhau. Giúp xác định:
- Model đủ tốt để demo không?
- Loại ảnh nào model yếu (cần cải thiện)?
- Baseline để so sánh khi fine-tune sau này

---

## TC-MODEL-001: Baseline accuracy trên test set tổng hợp

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-001 |
| **Dataset** | 50+ ảnh test đa dạng (tự thu thập từ internet) |
| **Metric** | mAP@0.5 per class + overall |
| **Target** | ≥ 85% mAP@0.5 overall |
| **Priority** | Critical |

**Evaluation command:**
```python
from ultralytics import YOLO
model = YOLO("models/ppe-detector.pt")
results = model.val(data="tests/model/test_dataset.yaml", split="test")
print(results.box.map50)  # mAP@0.5
```

**Expected per-class targets:**

| Class | Target mAP@0.5 | Notes |
|-------|----------------|-------|
| Helmet | ≥ 90% | Highest-contrast item, easiest to detect |
| Safety Vest | ≥ 88% | High-vis color, distinctive |
| Gloves | ≥ 75% | Small, color varies — hardest |
| Safety Goggles | ≥ 78% | Small, often occluded by helmet |
| Boots | ≥ 80% | Bottom of frame, often cut off |

**Pass Criteria:** Overall mAP@0.5 ≥ 85%

---

## TC-MODEL-002: Detection trên ảnh toàn thân đứng thẳng

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-002 |
| **Input** | 10 ảnh nhân viên đứng thẳng, ánh sáng tốt, nền đơn giản |
| **Expected** | Tất cả 5 PPE detected với confidence ≥ 0.75 |
| **Priority** | Critical |

**Test cases:**
- TC-MODEL-002a: Nhân viên đứng thẳng, ánh sáng tốt, nền trắng → tất cả PPE detect ≥ 90%
- TC-MODEL-002b: Nhân viên đứng thẳng, nền phức tạp (kho điện) → tất cả PPE detect ≥ 80%
- TC-MODEL-002c: Nhân viên đứng thẳng, ánh sáng ngược → tất cả PPE detect ≥ 75%

---

## TC-MODEL-003: Robustness — Góc chụp khác nhau

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-003 |
| **Purpose** | Kiểm tra model có hoạt động khi ảnh không hoàn hảo |
| **Priority** | High |

**Sub-cases:**

| Case | Input | Expected |
|------|-------|----------|
| TC-MODEL-003a | Ảnh chụp hơi nghiêng (±15 độ) | Helmet + Vest vẫn detect |
| TC-MODEL-003b | Ảnh chụp từ xa (người nhỏ trong frame) | Ít nhất Helmet + Vest detect |
| TC-MODEL-003c | Ảnh chụp từ gần (chỉ thấy từ đầu gối lên) | Helmet + Vest + Gloves detect |
| TC-MODEL-003d | Ảnh chụp hơi mờ/nhòe | Helmet + Vest detect (items lớn) |

**Pass Criteria:** Với ảnh góc bất thường, ít nhất Helmet và Vest phải detect được

---

## TC-MODEL-004: Robustness — Điều kiện ánh sáng

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-004 |
| **Priority** | High |

| Case | Điều kiện | Expected |
|------|-----------|----------|
| TC-MODEL-004a | Ánh sáng tốt, đủ sáng | Tất cả 5 items detect ≥ 80% |
| TC-MODEL-004b | Ảnh tối (indoor, ít đèn) | Ít nhất 3/5 items detect |
| TC-MODEL-004c | Ánh sáng mạnh (outdoor, nắng gắt) | Ít nhất 4/5 items detect |
| TC-MODEL-004d | Ảnh chụp bằng điện thoại thường | ≥ 80% items detect |

---

## TC-MODEL-005: False positive rate

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-005 |
| **Purpose** | Model không được "thấy" PPE khi không có |
| **Priority** | Critical |
| **Input** | 10 ảnh người KHÔNG mặc PPE (thường phục, áo thường) |

**Expected:**
- Helmet: không được detect khi không đội mũ
- Safety Vest: không được detect khi không mặc vest
- False positive rate < 10% per class

**Pass Criteria:** Model FAIL đúng khi nhân viên thật sự thiếu PPE

---

## TC-MODEL-006: Edge case — Không có người trong ảnh

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-006 |
| **Input** | Ảnh chỉ có thiết bị điện, không có người |
| **Expected** | Không detect PPE items nào, hoặc detections trống |
| **Priority** | Medium |

---

## TC-MODEL-007: Edge case — Nhiều người trong ảnh

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-007 |
| **Input** | Ảnh có 2 người, 1 người đủ PPE, 1 người thiếu |
| **Expected** | Hệ thống chỉ phân tích 1 người (primary subject) — không bị confused |
| **Priority** | Medium |

**Note**: Phase 1 chỉ support single person. Kết quả có thể không chính xác với multi-person. Cần ghi rõ limitation này trong UI.

---

## TC-MODEL-008: Performance benchmark

| Field | Value |
|-------|-------|
| **ID** | TC-MODEL-008 |
| **Priority** | High |

**Benchmark script:**
```python
import time
from ultralytics import YOLO
import cv2

model = YOLO("models/ppe-detector.pt")
image = cv2.imread("tests/fixtures/images/test_all_ppe.jpg")

times = []
for _ in range(10):
    start = time.monotonic()
    model.predict(image, conf=0.5, verbose=False)
    times.append((time.monotonic() - start) * 1000)

avg_ms = sum(times) / len(times)
print(f"Average inference: {avg_ms:.0f}ms")
assert avg_ms <= 3000, f"Too slow: {avg_ms}ms"
```

**Target:**
- Demo laptop (Intel i5/i7 CPU, no GPU): ≤ 3000ms average
- Server with GPU (RTX series): ≤ 200ms average

---

## Kết quả đánh giá (điền sau khi chạy)

| Test ID | Kết quả | Ghi chú | Ngày test |
|---------|---------|---------|-----------|
| TC-MODEL-001 | ⬜ | | |
| TC-MODEL-002 | ⬜ | | |
| TC-MODEL-003 | ⬜ | | |
| TC-MODEL-004 | ⬜ | | |
| TC-MODEL-005 | ⬜ | | |
| TC-MODEL-006 | ⬜ | | |
| TC-MODEL-007 | ⬜ | | |
| TC-MODEL-008 | ⬜ | | |

---

## Limitations cần ghi nhận trong demo

- Model được train trên ảnh công trường xây dựng → có thể kém hơn trên ảnh trạm điện
- Gloves và Goggles là 2 class khó nhất → accuracy thấp hơn Helmet/Vest
- Điều kiện ánh sáng xấu ảnh hưởng đáng kể
- Không phân biệt được chất lượng PPE (chỉ detect có/không)
- Chỉ hoạt động tốt với 1 người trong ảnh
