# PRD: Safety PPE Checker

> **Version**: v1.0 — Phase 1 (Demo/POC)
> **Status**: 📝 Draft
> **Author**: Product Team
> **Created**: 2026-03-13

---

## 1. Overview

### Problem Statement

Nhân viên kỹ thuật điện làm việc trong môi trường nguy hiểm cao — hồ quang điện, điện giật, vật rơi. Quy định an toàn bắt buộc họ phải mặc đầy đủ PPE trước khi bắt đầu công việc.

**Vấn đề hiện tại:**
- Kiểm tra PPE được thực hiện thủ công bởi giám sát viên → tốn thời gian, phụ thuộc vào sự hiện diện của giám sát
- Không có bằng chứng hình ảnh về việc kiểm tra → không thể audit
- Human error: giám sát viên có thể bỏ sót PPE item trong lúc bận
- Không scale được khi số lượng nhân viên và địa điểm làm việc lớn

### Proposed Solution

Một web application cho phép nhân viên chụp ảnh toàn thân và gửi lên để AI tự động phát hiện PPE, đánh giá tuân thủ, và trả kết quả PASS/FAIL kèm bằng chứng hình ảnh trong vòng 3 giây.

**Phase 1**: Web demo chứng minh tính khả thi (không cần dữ liệu thực)
**Phase 2**: Production system với dữ liệu thực, tích hợp vào quy trình an toàn

---

## 2. Goals & Non-Goals

### Goals

| # | Goal | Success Metric |
|---|------|----------------|
| G1 | Chứng minh AI có thể phát hiện 5 PPE items từ ảnh toàn thân | ≥ 85% accuracy trên demo images |
| G2 | Trải nghiệm demo trực quan, dễ hiểu cho stakeholder | Stakeholder tự dùng được không cần hướng dẫn |
| G3 | Inference nhanh, không làm gián đoạn workflow | ≤ 3 giây từ upload đến kết quả |
| G4 | Hệ thống portable, chạy offline trên laptop | Demo chạy được qua Docker Compose |

### Non-Goals (Phase 1)

- Xác định danh tính nhân viên (face recognition)
- Lưu trữ lịch sử kiểm tra (database/logging)
- Real-time video monitoring
- Phân biệt loại/cấp độ PPE (arc rating, glove voltage class)
- Tích hợp access control hoặc permit-to-work
- Multi-person detection trong cùng 1 frame
- Mobile native app
- Authentication / user accounts

---

## 3. User Stories (Overview)

### Primary Flow

```
Người dùng mở web app
    → Upload ảnh toàn thân nhân viên (hoặc chọn ảnh demo)
    → Chờ AI xử lý (~1-3 giây)
    → Xem kết quả: ảnh annotated + checklist PPE + PASS/FAIL
    → (Optional) Download kết quả hoặc upload ảnh mới
```

### Key User Stories

| ID | Story | Priority |
|----|-------|----------|
| US-WEB-001 | Upload ảnh để kiểm tra PPE | Must Have |
| US-WEB-002 | Xem ảnh đã annotated với bounding boxes | Must Have |
| US-WEB-003 | Xem checklist PPE items với PASS/FAIL | Must Have |
| US-WEB-004 | Dùng ảnh demo mẫu (không cần upload) | Must Have |
| US-WEB-005 | Xem confidence score cho từng PPE item | Should Have |
| US-CV-001 | AI phát hiện 5 PPE items từ ảnh | Must Have |
| US-CV-002 | Tạo compliance report dựa trên required PPE set | Must Have |
| US-CV-003 | Trả về ảnh đã annotated | Must Have |

---

## 4. Functional Requirements

### 4.1 Image Upload

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | Hỗ trợ upload ảnh định dạng: JPG, JPEG, PNG, WEBP | Must Have |
| FR-02 | Giới hạn file size: tối đa 10MB | Must Have |
| FR-03 | Hiển thị preview ảnh trước khi submit | Should Have |
| FR-04 | Drag-and-drop upload | Should Have |
| FR-05 | Validate định dạng file trước khi upload | Must Have |

### 4.2 PPE Detection

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-06 | Phát hiện: Helmet, Safety Vest, Gloves, Goggles, Boots | Must Have |
| FR-07 | Phát hiện cả "có PPE" và "không có PPE" (negative class) | Must Have |
| FR-08 | Confidence threshold: loại bỏ detections dưới 0.5 | Must Have |
| FR-09 | Inference time ≤ 3 giây trên CPU | Must Have |
| FR-10 | Xử lý ảnh có 1 người (single person) | Must Have |

### 4.3 Compliance Assessment

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-11 | PASS = tất cả 5 PPE required items đều detected | Must Have |
| FR-12 | FAIL = thiếu ít nhất 1 required PPE item | Must Have |
| FR-13 | Hiển thị danh sách PPE items bị thiếu | Must Have |
| FR-14 | Mỗi item hiển thị: tên, detected/not detected, confidence % | Should Have |

### 4.4 Results Display

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-15 | Hiển thị ảnh gốc và ảnh annotated cạnh nhau | Must Have |
| FR-16 | Bounding boxes màu xanh = detected, đỏ = missing zone | Must Have |
| FR-17 | PASS banner màu xanh, FAIL banner màu đỏ | Must Have |
| FR-18 | Checklist hiển thị ✓/✗ cho từng PPE item | Must Have |

### 4.5 Demo Mode

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-19 | Có ít nhất 4 ảnh mẫu sẵn có cho demo | Must Have |
| FR-20 | Ảnh mẫu bao gồm: fully compliant, 1 item missing, multiple items missing | Must Have |
| FR-21 | Click ảnh mẫu → tự động chạy analysis | Must Have |

---

## 5. Non-Functional Requirements

| ID | Requirement | Target |
|----|-------------|--------|
| NFR-01 | Inference time | ≤ 3 giây trên CPU (demo laptop) |
| NFR-02 | Max image size accepted | 10 MB |
| NFR-03 | UI responsiveness | Chạy tốt trên 1080p màn hình laptop |
| NFR-04 | Offline capability | Chạy hoàn toàn offline sau khi `docker compose up` |
| NFR-05 | Model accuracy | ≥ 85% mAP@0.5 trên test images |
| NFR-06 | API availability | Stateless — không cần database, không cần cloud |

---

## 6. Technical Architecture (Summary)

```
┌─────────────────────────────────────────────────────┐
│                   Browser (Next.js)                  │
│  ┌──────────────┐         ┌──────────────────────┐  │
│  │  Upload Zone │         │   Results Panel       │  │
│  │  (drag/drop) │         │  - Annotated image    │  │
│  │              │         │  - PPE checklist      │  │
│  │  Demo images │         │  - PASS/FAIL banner   │  │
│  └──────┬───────┘         └──────────────────────┘  │
└─────────┼───────────────────────────────────────────┘
          │ POST /api/analyze (multipart/form-data)
          ▼
┌─────────────────────────────────────────────────────┐
│                  FastAPI Backend                      │
│                                                      │
│  ┌──────────────────────────────────────────────┐   │
│  │            detector.py                        │   │
│  │   YOLOv8m.predict(image)                     │   │
│  │   → boxes, labels, confidence scores         │   │
│  └──────────────────┬───────────────────────────┘   │
│                     │                                │
│  ┌──────────────────▼───────────────────────────┐   │
│  │           compliance.py                       │   │
│  │   check_required_ppe(detections)             │   │
│  │   → compliance_report (PASS/FAIL + details)  │   │
│  └──────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────┘
          │
          ▼ Response JSON:
          {
            "status": "FAIL",
            "missing": ["Helmet", "Gloves"],
            "detections": [...],
            "annotated_image": "<base64>"
          }
```

**Tech Stack:**
- Frontend: Next.js 14 (App Router), Tailwind CSS, shadcn/ui
- Backend: FastAPI (Python 3.11), Uvicorn
- AI: Ultralytics YOLOv8m, pre-trained on Construction-PPE dataset
- Image: OpenCV, Pillow
- Deployment: Docker Compose (2 services: frontend + backend)

---

## 7. Phases & Timeline

### Phase 1 — Demo (Current)

| Week | Deliverable |
|------|-------------|
| Week 1 | Documentation, project setup, Docker skeleton |
| Week 1–2 | Backend: FastAPI + YOLOv8 integration, `/api/analyze` endpoint |
| Week 2 | Frontend: upload UI + results display |
| Week 2–3 | Integration, demo images, testing |
| Week 3 | Demo ready — present to stakeholders |

### Phase 2 — Production (After approval)

1. Collect real electrical worker images from company cameras
2. Annotate and build domain-specific dataset
3. Fine-tune YOLOv8l/x on company data
4. Add arc flash suit detection
5. Real-time video stream processing
6. Permit-to-work integration
7. Worker identity linking

---

## 8. Open Questions

| # | Question | Owner | Status |
|---|----------|-------|--------|
| Q1 | Công ty sử dụng tiêu chuẩn PPE nào? (NFPA 70E, IEC, hay QCVN?) | Stakeholder | ⬜ Open |
| Q2 | Bao nhiêu loại PPE cần detect trong production? (arc suit, harness?) | Stakeholder | ⬜ Open |
| Q3 | Quy trình hiện tại khi phát hiện vi phạm PPE là gì? | Stakeholder | ⬜ Open |
| Q4 | Có cần tích hợp với hệ thống nào hiện có (HR, access control)? | Stakeholder | ⬜ Open |
| Q5 | Dữ liệu ảnh từ camera hiện tại của công ty như thế nào? | Stakeholder | ⬜ Open |
