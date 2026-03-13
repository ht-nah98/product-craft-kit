# Test Cases — Backend API

> **File**: `tests/integration/test_api.py` + `tests/unit/test_compliance.py`
> **Tools**: pytest, httpx

---

## TC-API-001: Health Check endpoint

| Field | Value |
|-------|-------|
| **ID** | TC-API-001 |
| **Endpoint** | GET `/api/health` |
| **Priority** | High |

**Steps:**
1. Send GET request to `/api/health`

**Expected:**
- Status: 200 OK
- Body: `{ "status": "ok", "model_loaded": true, "model_name": "yolov8m-ppe" }`

**Pass Criteria:** Response 200, `model_loaded` = true

---

## TC-API-002: Upload valid image — PASS case

| Field | Value |
|-------|-------|
| **ID** | TC-API-002 |
| **Endpoint** | POST `/api/analyze` |
| **Test Image** | `test_all_ppe.jpg` (all 5 PPE detected) |
| **Priority** | Critical |

**Steps:**
1. POST multipart/form-data with `test_all_ppe.jpg`

**Expected:**
- Status: 200 OK
- `overall_pass`: `true`
- `status`: `"PASS"`
- `missing_items`: `[]`
- `detections`: array with 5 items, all `detected: true`
- `annotated_image`: starts with `"data:image/jpeg;base64,"`
- `inference_time_ms`: integer > 0

**Pass Criteria:** All fields match, no missing items

---

## TC-API-003: Upload image — FAIL, 1 item missing

| Field | Value |
|-------|-------|
| **ID** | TC-API-003 |
| **Test Image** | `test_no_helmet.jpg` |
| **Priority** | Critical |

**Steps:**
1. POST `test_no_helmet.jpg`

**Expected:**
- `overall_pass`: `false`
- `status`: `"FAIL"`
- `missing_items`: `["Helmet"]` (exactly 1 item)
- Detection for Helmet: `detected: false`, `confidence: 0.0`, `bbox: null`
- Other 4 items: `detected: true`

**Pass Criteria:** Exactly "Helmet" in missing_items, others detected

---

## TC-API-004: Upload image — FAIL, multiple items missing

| Field | Value |
|-------|-------|
| **ID** | TC-API-004 |
| **Test Image** | `test_multiple_missing.jpg` (no Helmet, no Safety Goggles) |
| **Priority** | Critical |

**Expected:**
- `overall_pass`: `false`
- `missing_items`: contains "Helmet" AND "Safety Goggles" (order may vary)
- Length of `missing_items`: 2

---

## TC-API-005: Upload image — all PPE missing

| Field | Value |
|-------|-------|
| **ID** | TC-API-005 |
| **Test Image** | `test_no_ppe.jpg` |
| **Priority** | High |

**Expected:**
- `overall_pass`: `false`
- `missing_items`: contains all 5: `["Helmet","Safety Vest","Gloves","Safety Goggles","Boots"]`
- All detections: `detected: false`

---

## TC-API-006: Upload invalid file type

| Field | Value |
|-------|-------|
| **ID** | TC-API-006 |
| **Test File** | `document.pdf` |
| **Priority** | High |

**Expected:**
- Status: **400 Bad Request**
- Body: `{ "detail": "Invalid file type..." }`

**Pass Criteria:** 400 returned, server does NOT crash

---

## TC-API-007: Upload file exceeding size limit

| Field | Value |
|-------|-------|
| **ID** | TC-API-007 |
| **Test File** | Image > 10MB |
| **Priority** | High |

**Expected:**
- Status: **413 Request Entity Too Large**
- Body: `{ "detail": "File size exceeds 10MB limit" }`

---

## TC-API-008: Upload corrupt image file

| Field | Value |
|-------|-------|
| **ID** | TC-API-008 |
| **Test File** | `test_corrupt.bin` (binary garbage renamed to .jpg) |
| **Priority** | High |

**Expected:**
- Status: **400 Bad Request**
- Body: `{ "detail": "Cannot decode image" }` or similar
- Server does NOT crash, does NOT return 500

---

## TC-API-009: Annotated image is valid base64 JPEG

| Field | Value |
|-------|-------|
| **ID** | TC-API-009 |
| **Priority** | High |

**Steps:**
1. POST any valid image
2. Take `annotated_image` from response
3. Strip `"data:image/jpeg;base64,"` prefix
4. Decode base64 → bytes
5. cv2.imdecode or Pillow open

**Expected:**
- Decode succeeds without error
- Image dimensions match original image dimensions

---

## TC-API-010: Inference time within limit

| Field | Value |
|-------|-------|
| **ID** | TC-API-010 |
| **Priority** | High |

**Steps:**
1. POST `test_all_ppe.jpg` on demo laptop CPU
2. Check `inference_time_ms` in response

**Expected:**
- `inference_time_ms` ≤ 3000
- Total response time (measured by client) ≤ 5000ms

---

## TC-UNIT-001: Compliance engine — PASS case

```python
def test_compliance_pass():
    detections = [
        Detection(label="Helmet", confidence=0.92, detected=True, bbox=[...]),
        Detection(label="Safety Vest", confidence=0.88, detected=True, bbox=[...]),
        Detection(label="Gloves", confidence=0.79, detected=True, bbox=[...]),
        Detection(label="Safety Goggles", confidence=0.83, detected=True, bbox=[...]),
        Detection(label="Boots", confidence=0.91, detected=True, bbox=[...]),
    ]
    result = assess_compliance(detections)
    assert result.overall_pass == True
    assert result.missing_items == []
```

---

## TC-UNIT-002: Compliance engine — single item missing

```python
def test_compliance_missing_helmet():
    detections = [
        Detection(label="Helmet", confidence=0.0, detected=False, bbox=None),
        Detection(label="Safety Vest", confidence=0.88, detected=True, bbox=[...]),
        Detection(label="Gloves", confidence=0.79, detected=True, bbox=[...]),
        Detection(label="Safety Goggles", confidence=0.83, detected=True, bbox=[...]),
        Detection(label="Boots", confidence=0.91, detected=True, bbox=[...]),
    ]
    result = assess_compliance(detections)
    assert result.overall_pass == False
    assert "Helmet" in result.missing_items
    assert len(result.missing_items) == 1
```

---

## TC-UNIT-003: Compliance engine — all items missing

```python
def test_compliance_all_missing():
    detections = [
        Detection(label=label, confidence=0.0, detected=False, bbox=None)
        for label in ["Helmet", "Safety Vest", "Gloves", "Safety Goggles", "Boots"]
    ]
    result = assess_compliance(detections)
    assert result.overall_pass == False
    assert len(result.missing_items) == 5
```

---

## TC-UNIT-004: Compliance engine — below confidence threshold

```python
def test_compliance_low_confidence_treated_as_missing():
    # Confidence 0.3 is below threshold → should be treated as not detected
    detections = [
        Detection(label="Helmet", confidence=0.3, detected=False, bbox=None),
        # ... others detected
    ]
    result = assess_compliance(detections)
    assert result.overall_pass == False
    assert "Helmet" in result.missing_items
```

---

## TC-UNIT-005: Annotator — returns valid base64

```python
def test_annotator_returns_valid_base64():
    with open("tests/fixtures/images/test_all_ppe.jpg", "rb") as f:
        image_bytes = f.read()
    detections = [...]
    result = annotate_image(image_bytes, detections)
    assert result.startswith("data:image/jpeg;base64,")
    b64_data = result.replace("data:image/jpeg;base64,", "")
    decoded = base64.b64decode(b64_data)
    img = cv2.imdecode(np.frombuffer(decoded, np.uint8), cv2.IMREAD_COLOR)
    assert img is not None
```

---

## TC-UNIT-006: Annotator — empty detections returns original image

```python
def test_annotator_empty_detections():
    with open("tests/fixtures/images/test_all_ppe.jpg", "rb") as f:
        image_bytes = f.read()
    result = annotate_image(image_bytes, [])
    assert result.startswith("data:image/jpeg;base64,")
    # Image should be decodable and not crash
```
