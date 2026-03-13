# System Architecture — Safety PPE Checker

> **Version**: v1.0 | **Phase**: Demo/POC
> **Status**: Approved

---

## 1. Overview

Hệ thống gồm 2 services chạy trong Docker Compose:
- **Frontend** (Next.js): giao diện người dùng, chạy tại `localhost:3000`
- **Backend** (FastAPI): AI inference engine, chạy tại `localhost:8000`

Không có database. Stateless. Chạy hoàn toàn offline sau khi pull images.

---

## 2. Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                     Docker Compose Network                   │
│                                                             │
│  ┌───────────────────┐          ┌────────────────────────┐  │
│  │   frontend         │          │       backend           │  │
│  │   (Next.js 14)     │          │       (FastAPI)         │  │
│  │   Port: 3000       │◄────────►│       Port: 8000        │  │
│  │                   │  HTTP    │                        │  │
│  │  app/             │  REST    │  main.py               │  │
│  │  components/      │          │  detector.py           │  │
│  │  public/          │          │  compliance.py         │  │
│  │  (demo images)    │          │  models.py             │  │
│  └───────────────────┘          │                        │  │
│                                 │  ┌──────────────────┐  │  │
│                                 │  │   YOLOv8m.pt     │  │  │
│                                 │  │   (loaded once   │  │  │
│                                 │  │    at startup)   │  │  │
│                                 │  └──────────────────┘  │  │
│                                 └────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘

External Access:
  Browser → http://localhost:3000  (Frontend)
  API Docs → http://localhost:8000/docs  (FastAPI Swagger)
```

---

## 3. Request Flow

```
1. User selects/uploads image in browser
       │
       ▼
2. Next.js frontend: POST /api/analyze
   Content-Type: multipart/form-data
   Body: { file: <image_bytes> }
       │
       ▼ (proxied via Next.js API route or direct call)
3. FastAPI backend receives request
   │
   ├─ 3a. Validate: file type, file size
   │
   ├─ 3b. Read image bytes → cv2/numpy array
   │
   ├─ 3c. YOLOv8m.predict(image, conf=0.5, iou=0.45)
   │        → Results: boxes, labels, confidences
   │
   ├─ 3d. compliance.assess(detections)
   │        → overall_pass: bool
   │        → missing_items: list[str]
   │
   └─ 3e. annotate_image(original, detections)
            → draw bounding boxes (green=detected, red=missing zone)
            → encode as base64 JPEG
       │
       ▼
4. Response JSON returned to frontend
       │
       ▼
5. Next.js renders:
   - Annotated image (from base64)
   - PASS/FAIL banner
   - PPE checklist
```

---

## 4. Component Breakdown

### 4.1 Frontend (Next.js 14)

| Component | Responsibility |
|-----------|----------------|
| `app/page.tsx` | Main page layout: left panel (upload) + right panel (results) |
| `components/UploadZone.tsx` | Drag-and-drop + file browser, validation, preview |
| `components/DemoImages.tsx` | Grid of pre-loaded sample images |
| `components/AnnotatedImage.tsx` | Display base64 annotated image, loading state |
| `components/ComplianceReport.tsx` | PASS/FAIL banner + PPE checklist |
| `lib/api.ts` | API call wrapper: `analyzeImage(file)` → response |

**Key dependencies:**
- `next` 14 (App Router)
- `tailwindcss` + `shadcn/ui` (UI components)
- `react-dropzone` (drag-and-drop)

---

### 4.2 Backend (FastAPI)

| File | Responsibility |
|------|----------------|
| `main.py` | FastAPI app init, CORS config, route registration, model loading at startup |
| `detector.py` | `class PPEDetector`: wraps Ultralytics YOLO, `predict(image_bytes)` → `list[Detection]` |
| `compliance.py` | `assess_compliance(detections)` → `ComplianceResult` (PASS/FAIL + missing items) |
| `models.py` | Pydantic schemas: `Detection`, `ComplianceResult`, `AnalyzeResponse` |
| `annotator.py` | `annotate_image(image, detections)` → base64 JPEG string |

**Key dependencies:**
- `fastapi` + `uvicorn[standard]`
- `ultralytics` (YOLOv8)
- `opencv-python-headless`
- `pillow`
- `python-multipart`

---

### 4.3 YOLOv8m Model

| Property | Value |
|----------|-------|
| Architecture | YOLOv8m (medium) |
| Pre-trained weights | Ultralytics Construction-PPE dataset |
| Input size | 640×640 (auto-resized) |
| Confidence threshold | 0.50 |
| IoU threshold | 0.45 |
| Inference mode | CPU (demo); GPU if available |
| Load strategy | Once at server startup via `@app.on_event("startup")` |
| File | `models/ppe-detector.pt` (mounted into container) |

---

## 5. Docker Compose Setup

```yaml
# docker-compose.yml (simplified)
services:
  backend:
    build: ./src/backend
    ports: ["8000:8000"]
    volumes:
      - ./models:/app/models    # mount .pt file here
    environment:
      - MODEL_PATH=/app/models/ppe-detector.pt
      - CONFIDENCE_THRESHOLD=0.5

  frontend:
    build: ./src/frontend
    ports: ["3000:3000"]
    environment:
      - NEXT_PUBLIC_API_URL=http://backend:8000
    depends_on: [backend]
```

**Startup:**
```bash
# Download model weights (one time)
python scripts/download_model.py

# Start everything
docker compose up
```

---

## 6. Data Flow: Image → Response

```
Input: JPEG/PNG/WEBP (max 10MB)
    │
    ▼ FastAPI reads bytes
Raw bytes (io.BytesIO)
    │
    ▼ cv2.imdecode
NumPy array (H×W×3, BGR)
    │
    ▼ YOLOv8m.predict()
YOLO Results object
  └─ boxes.xyxy   → [[x1,y1,x2,y2], ...]
  └─ boxes.cls    → [class_id, ...]
  └─ boxes.conf   → [confidence, ...]
    │
    ▼ detector.parse_results()
List[Detection]
  └─ Detection(label="Hardhat", confidence=0.92, bbox=[...], detected=True)
  └─ Detection(label="Gloves", confidence=0.0, bbox=None, detected=False)
    │
    ├─▶ compliance.assess() → ComplianceResult(pass=False, missing=["Gloves"])
    │
    └─▶ annotator.draw() → base64 JPEG string
    │
    ▼
AnalyzeResponse (Pydantic)
  └─ status: "FAIL"
  └─ overall_pass: false
  └─ missing_items: ["Gloves"]
  └─ detections: [...]
  └─ annotated_image: "data:image/jpeg;base64,/9j/..."
  └─ inference_time_ms: 1240
```

---

## 7. Phase 2 Upgrade Path

| Component | Phase 1 (Demo) | Phase 2 (Production) |
|-----------|----------------|---------------------|
| Model | YOLOv8m pre-trained | YOLOv8l fine-tuned on company data |
| PPE classes | 5 basic classes | +Arc suit, +Harness |
| Input | Single photo upload | Real-time RTSP camera stream |
| Storage | Stateless | PostgreSQL (event log) + S3 (images) |
| Auth | None | JWT + role-based access |
| Deployment | Docker Compose (local) | Cloud VM or on-premise server |
| Integration | Standalone | Permit-to-work API integration |
