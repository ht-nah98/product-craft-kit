# TP-CV-001: CV Detection Pipeline

> **Linked Epic**: [EPIC-CV-001](../../01_product_requirements/cv-engine/EPIC-CV-001.md)
> **Status**: Draft | **Version**: v1.0

---

## 1. Overview

Tech Spec cho toàn bộ CV inference pipeline: từ bytes ảnh đầu vào → JSON compliance report + annotated image đầu ra.

Phần core của hệ thống. Mọi thành phần khác (frontend, API routes) đều phụ thuộc vào pipeline này.

---

## 2. API Specification

### POST `/api/analyze`

**Request Headers:**
```
Content-Type: multipart/form-data
```

**Request Body:**
```
file: binary (image/jpeg | image/png | image/webp)
      max size: 10MB
```

**Response 200 — Success:**
```json
{
  "status": "FAIL",
  "overall_pass": false,
  "missing_items": ["Gloves", "Safety Goggles"],
  "detections": [
    {
      "label": "Hardhat",
      "confidence": 0.924,
      "detected": true,
      "bbox": [145, 23, 312, 198]
    },
    {
      "label": "Safety Vest",
      "confidence": 0.881,
      "detected": true,
      "bbox": [98, 210, 445, 680]
    },
    {
      "label": "Gloves",
      "confidence": 0.0,
      "detected": false,
      "bbox": null
    },
    {
      "label": "Safety Goggles",
      "confidence": 0.0,
      "detected": false,
      "bbox": null
    },
    {
      "label": "Boots",
      "confidence": 0.763,
      "detected": true,
      "bbox": [120, 1450, 380, 1680]
    }
  ],
  "annotated_image": "data:image/jpeg;base64,/9j/4AAQ...",
  "inference_time_ms": 1847
}
```

**Response 400 — Invalid file:**
```json
{ "detail": "Invalid file type. Accepted: jpg, jpeg, png, webp" }
```

**Response 413 — File too large:**
```json
{ "detail": "File size exceeds 10MB limit" }
```

**Response 500 — Inference error:**
```json
{ "detail": "Inference failed: <error message>" }
```

### GET `/api/health`
```json
{
  "status": "ok",
  "model_loaded": true,
  "model_name": "yolov8m-ppe",
  "ppe_classes": ["Hardhat", "Safety Vest", "Gloves", "Safety Goggles", "Boots"],
  "version": "1.0.0"
}
```

---

## 3. Pydantic Models

```python
# models.py

from pydantic import BaseModel
from typing import Optional

class Detection(BaseModel):
    label: str                    # e.g. "Hardhat"
    confidence: float             # 0.0 if not detected
    detected: bool
    bbox: Optional[list[int]]     # [x1, y1, x2, y2] or None

class ComplianceResult(BaseModel):
    overall_pass: bool
    missing_items: list[str]

class AnalyzeResponse(BaseModel):
    status: str                   # "PASS" or "FAIL"
    overall_pass: bool
    missing_items: list[str]
    detections: list[Detection]
    annotated_image: str          # "data:image/jpeg;base64,..."
    inference_time_ms: int
```

---

## 4. Implementation: `detector.py`

```python
# detector.py

import time
import cv2
import numpy as np
from ultralytics import YOLO
from models import Detection

REQUIRED_CLASSES = ["Hardhat", "Safety Vest", "Gloves", "Safety Goggles", "Boots"]
CONFIDENCE_THRESHOLD = 0.50
IOU_THRESHOLD = 0.45

class PPEDetector:
    def __init__(self, model_path: str):
        self.model = YOLO(model_path)
        self.class_names = self.model.names  # {0: "Hardhat", 1: "NO-Hardhat", ...}

    def predict(self, image_bytes: bytes) -> tuple[list[Detection], int]:
        """
        Run inference on image bytes.
        Returns: (detections, inference_time_ms)
        """
        # Decode image
        nparr = np.frombuffer(image_bytes, np.uint8)
        image = cv2.imdecode(nparr, cv2.IMREAD_COLOR)
        if image is None:
            raise ValueError("Cannot decode image")

        # Run inference
        start = time.monotonic()
        results = self.model.predict(
            source=image,
            conf=CONFIDENCE_THRESHOLD,
            iou=IOU_THRESHOLD,
            verbose=False
        )[0]
        inference_ms = int((time.monotonic() - start) * 1000)

        # Parse results
        detections = self._parse_results(results)
        return detections, inference_ms

    def _parse_results(self, results) -> list[Detection]:
        detected_labels = {}

        for box in results.boxes:
            label = self.class_names[int(box.cls[0])]
            conf = float(box.conf[0])
            bbox = [int(x) for x in box.xyxy[0].tolist()]

            # Skip negative classes (NO-Hardhat etc.) — handled by absence
            if label.startswith("NO-"):
                continue

            # Keep highest-confidence detection per label
            if label not in detected_labels or conf > detected_labels[label].confidence:
                detected_labels[label] = Detection(
                    label=label,
                    confidence=round(conf, 3),
                    detected=True,
                    bbox=bbox
                )

        # Add undetected required items
        all_detections = []
        for required in REQUIRED_CLASSES:
            if required in detected_labels:
                all_detections.append(detected_labels[required])
            else:
                all_detections.append(Detection(
                    label=required,
                    confidence=0.0,
                    detected=False,
                    bbox=None
                ))

        return all_detections
```

---

## 5. Implementation: `compliance.py`

```python
# compliance.py

from models import Detection, ComplianceResult

REQUIRED_PPE = ["Hardhat", "Safety Vest", "Gloves", "Safety Goggles", "Boots"]

def assess_compliance(detections: list[Detection]) -> ComplianceResult:
    detected_labels = {d.label for d in detections if d.detected}
    missing = [ppe for ppe in REQUIRED_PPE if ppe not in detected_labels]
    return ComplianceResult(
        overall_pass=len(missing) == 0,
        missing_items=missing
    )
```

---

## 6. Implementation: `annotator.py`

```python
# annotator.py

import cv2
import base64
import numpy as np
from models import Detection

# Colors (BGR): green for detected, red for missing
COLOR_DETECTED = (0, 200, 0)
COLOR_MISSING  = (0, 0, 220)
FONT = cv2.FONT_HERSHEY_SIMPLEX

def annotate_image(image_bytes: bytes, detections: list[Detection]) -> str:
    """Draw bounding boxes and return base64 JPEG."""
    nparr = np.frombuffer(image_bytes, np.uint8)
    image = cv2.imdecode(nparr, cv2.IMREAD_COLOR)

    for det in detections:
        if det.detected and det.bbox:
            x1, y1, x2, y2 = det.bbox
            color = COLOR_DETECTED
            label_text = f"{det.label} {det.confidence:.0%}"
            cv2.rectangle(image, (x1, y1), (x2, y2), color, 2)
            cv2.putText(image, label_text, (x1, y1 - 8),
                        FONT, 0.55, color, 2)

    # Encode to base64
    _, buffer = cv2.imencode(".jpg", image, [cv2.IMWRITE_JPEG_QUALITY, 85])
    b64 = base64.b64encode(buffer).decode("utf-8")
    return f"data:image/jpeg;base64,{b64}"
```

---

## 7. Implementation: `main.py`

```python
# main.py

import os
from contextlib import asynccontextmanager
from fastapi import FastAPI, File, UploadFile, HTTPException
from fastapi.middleware.cors import CORSMiddleware
from detector import PPEDetector
from compliance import assess_compliance
from annotator import annotate_image
from models import AnalyzeResponse

ALLOWED_TYPES = {"image/jpeg", "image/png", "image/webp"}
MAX_FILE_SIZE = 10 * 1024 * 1024  # 10MB

detector: PPEDetector = None

@asynccontextmanager
async def lifespan(app: FastAPI):
    global detector
    model_path = os.getenv("MODEL_PATH", "models/ppe-detector.pt")
    detector = PPEDetector(model_path)
    print(f"Model loaded: {model_path}")
    yield

app = FastAPI(title="Safety PPE Checker API", lifespan=lifespan)

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000"],
    allow_methods=["POST", "GET"],
    allow_headers=["*"],
)

@app.get("/api/health")
def health():
    return {
        "status": "ok",
        "model_loaded": detector is not None,
        "model_name": "yolov8m-ppe",
        "ppe_classes": ["Hardhat", "Safety Vest", "Gloves", "Safety Goggles", "Boots"],
        "version": "1.0.0"
    }

@app.post("/api/analyze", response_model=AnalyzeResponse)
async def analyze(file: UploadFile = File(...)):
    # Validate type
    if file.content_type not in ALLOWED_TYPES:
        raise HTTPException(400, "Invalid file type. Accepted: jpg, jpeg, png, webp")

    image_bytes = await file.read()

    # Validate size
    if len(image_bytes) > MAX_FILE_SIZE:
        raise HTTPException(413, "File size exceeds 10MB limit")

    try:
        detections, inference_ms = detector.predict(image_bytes)
    except ValueError as e:
        raise HTTPException(400, str(e))
    except Exception as e:
        raise HTTPException(500, f"Inference failed: {str(e)}")

    compliance = assess_compliance(detections)
    annotated = annotate_image(image_bytes, detections)

    return AnalyzeResponse(
        status="PASS" if compliance.overall_pass else "FAIL",
        overall_pass=compliance.overall_pass,
        missing_items=compliance.missing_items,
        detections=detections,
        annotated_image=annotated,
        inference_time_ms=inference_ms
    )
```

---

## 8. Model Strategy

### Phase 1 — Pre-trained (Demo)
- **Source**: Ultralytics Construction-PPE dataset weights
- **Download**: `from ultralytics import YOLO; YOLO("yolov8m.pt")` then fine-tune or use Construction-PPE checkpoint
- **No custom training needed**: pre-trained weights already cover 5 required classes
- **Expected accuracy**: ~85–90% mAP@0.5 on general construction/industrial images

### Phase 2 — Fine-tuned (Production)
```
Company cameras → collect 500–2000 labeled images
                → CVAT or Label Studio for annotation
                → Fine-tune YOLOv8l on company data
                → Expected: 90–95%+ mAP on domain-specific data
```

**Training command (Phase 2):**
```bash
yolo train \
  model=yolov8l.pt \
  data=company_ppe.yaml \
  epochs=100 \
  imgsz=640 \
  batch=16 \
  name=ppe_company_v1
```

---

## 9. Performance Targets

| Environment | Expected Inference Time | Notes |
|-------------|------------------------|-------|
| Demo laptop (CPU, no GPU) | 1.5–3.0 seconds | YOLOv8m on Intel i7/i5 |
| Server with GPU (RTX 3060+) | 50–150ms | Production target |
| Edge device (Jetson Orin) | 200–400ms | Future deployment |

---

## 10. Security Considerations

| Risk | Mitigation |
|------|------------|
| Malicious file upload | Validate content-type + attempt cv2.imdecode before inference |
| Large file attack (DoS) | 10MB hard limit before reading full bytes |
| Path traversal | Files processed in-memory only, never written to disk |
| CORS abuse | Whitelist only `localhost:3000` in demo; restrict to domain in production |

---

## 11. Testing Strategy

```
tests/
  test_detector.py      → Unit test: PPEDetector.predict() on sample images
  test_compliance.py    → Unit test: assess_compliance() for all combinations
  test_annotator.py     → Unit test: annotate_image() output is valid base64 JPEG
  test_api.py           → Integration test: POST /api/analyze with real images
```

**Minimum test cases for compliance engine:**
1. All 5 detected → PASS, missing=[]
2. 0 detected → FAIL, missing=[all 5]
3. Only Helmet missing → FAIL, missing=["Helmet"]
4. Only Boots missing → FAIL, missing=["Boots"]
5. 3 items missing → FAIL, missing=[3 items]

---

## 12. Mapping to User Stories

| Feature/Endpoint | User Story |
|-----------------|------------|
| `PPEDetector.predict()` | US-CV-001: Detect PPE items |
| `assess_compliance()` | US-CV-002: Generate compliance report |
| `annotate_image()` | US-CV-003: Return annotated image |
| `POST /api/analyze` | US-CV-001, US-CV-002, US-CV-003 |
| `GET /api/health` | System reliability |
