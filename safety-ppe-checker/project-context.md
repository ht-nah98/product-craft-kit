# Project Context: Safety PPE Checker

> File này chứa bối cảnh quan trọng nhất của dự án. AI sẽ đọc file này ĐẦU TIÊN khi làm việc với project.

---

## 1. Overview

### Tên dự án
Safety PPE Checker — AI-Powered Personal Protective Equipment Compliance Assessment

### Mô tả ngắn gọn
Hệ thống web demo cho phép upload ảnh toàn thân nhân viên kỹ thuật điện và tự động đánh giá xem nhân viên có đang mặc đầy đủ thiết bị bảo hộ cá nhân (PPE) theo quy định an toàn hay không, sử dụng AI/Computer Vision.

### Problem Statement
Khi nhân viên kỹ thuật điện thực hiện sửa chữa điện, họ phải tuân thủ quy định an toàn bằng cách mặc đầy đủ thiết bị bảo hộ. Hiện tại, việc kiểm tra tuân thủ được thực hiện thủ công bởi giám sát viên — tốn thời gian, dễ bỏ sót, không có bằng chứng hình ảnh, và không thể scale. Dự án này chứng minh rằng AI có thể tự động hoá quá trình kiểm tra này từ một ảnh chụp.

### Phase hiện tại
**Phase 1 — Demo / Proof of Concept**
Mục tiêu: Xây dựng web demo đủ thuyết phục để thu thập dữ liệu thực từ công ty và phê duyệt triển khai thực tế.

---

## 2. Business Context

### Business Goals
1. Chứng minh tính khả thi của AI trong kiểm tra PPE tự động từ ảnh chụp toàn thân
2. Tạo bằng chứng thuyết phục (demo) để xin phê duyệt thu thập dữ liệu thực từ camera công ty
3. Xây dựng nền tảng kỹ thuật để scale lên hệ thống production trong Phase 2

### Success Metrics — Demo Phase

| Metric | Target | Cách đo |
|--------|--------|---------|
| Detection accuracy on demo images | ≥ 85% mAP@0.5 | Evaluate trên test set tự xây dựng |
| Inference time per image | ≤ 3 giây | Đo từ lúc upload đến khi có kết quả |
| Demo usability | Stakeholder có thể tự dùng không cần hướng dẫn | Quan sát khi demo |
| PPE items covered | 5 loại PPE chính | Helmet, Vest, Gloves, Goggles, Boots |

### Stakeholders

| Role | Mô tả |
|------|-------|
| Product Builder | Người xây dựng demo |
| Internal Reviewer | Quản lý/kỹ thuật công ty điện — người xem demo |
| Phase 2 Sponsor | Người phê duyệt ngân sách thu thập dữ liệu thực |

---

## 3. Users

### Demo Users (Phase 1)

| User Type | Mô tả | Key Needs |
|-----------|-------|-----------|
| Demo Viewer | Manager/kỹ sư xem demo để đánh giá tính khả thi | Kết quả trực quan, dễ hiểu |
| Developer | Người build và test hệ thống | API rõ ràng, dễ debug, dễ extend |

### End Users (Phase 2 — Production)

| User Type | Mô tả | Key Needs |
|-----------|-------|-----------|
| Electrical Worker | Nhân viên kỹ thuật điện | Kiểm tra nhanh trước khi vào vùng làm việc |
| Safety Supervisor | Giám sát an toàn | Xem kết quả, nhận cảnh báo vi phạm |
| EHS Manager | Quản lý an toàn lao động | Dashboard, báo cáo tuân thủ, audit trail |

---

## 4. Product Scope

### Phase 1 — In Scope (Demo)
- Web UI cho upload ảnh toàn thân nhân viên
- AI phát hiện 5 loại PPE: Helmet, Safety Vest, Protective Gloves, Safety Goggles, Safety Boots
- Trả về kết quả: ảnh annotated + checklist từng PPE item + tổng kết PASS/FAIL
- Demo mode: bộ ảnh mẫu sẵn có để demo không cần upload thật
- Chạy được trên laptop (Docker Compose)

### Phase 1 — Out of Scope
- Xác định danh tính nhân viên
- Lưu lịch sử kiểm tra (database)
- Real-time camera feed
- Tích hợp access control / permit-to-work
- Phân biệt cấp độ PPE (arc rating, glove class)
- Multi-person detection trong cùng 1 ảnh

### Phase 2 — Roadmap
- Fine-tune model trên dữ liệu thực của công ty
- Arc flash suit detection
- Real-time video stream
- Worker identity linking
- Tích hợp permit-to-work
- Mobile app

---

## 5. Technical Context

### Tech Stack

| Layer | Technology | Lý do chọn |
|-------|-----------|------------|
| AI Model | YOLOv8m (Ultralytics) | SOTA detector, pre-trained Construction-PPE weights có sẵn |
| Pre-trained Dataset | Ultralytics Construction-PPE | Covers 5 PPE classes cần thiết, không cần training từ đầu |
| Backend | FastAPI (Python 3.11) | Cùng ecosystem với Ultralytics, async, tự generate API docs |
| Frontend | Next.js 14 + Tailwind CSS + shadcn/ui | Clean UI nhanh, TypeScript |
| Image Processing | OpenCV + Pillow | Standard, native với YOLO pipeline |
| Deployment | Docker Compose | Portable, chạy offline trên laptop |

### Architecture Overview

```
Browser (Next.js)
    │  multipart/form-data (image upload)
    ▼
FastAPI Backend
    │
    ├── YOLOv8m Inference → bounding boxes + labels + confidence
    │
    └── Compliance Engine (rule-based)
            │  check required PPE set
            ▼
    Response: annotated_image (base64) + compliance_report (JSON)
            │
            ▼
    Next.js — display annotated image + checklist + PASS/FAIL
```

### PPE Detection Classes (Phase 1)

| Class | Label | Required for PASS |
|-------|-------|------------------|
| Hard Hat | `Hardhat` / `NO-Hardhat` | YES |
| Safety Vest | `Safety Vest` / `NO-Safety Vest` | YES |
| Protective Gloves | `Gloves` / `NO-Gloves` | YES |
| Safety Goggles | `Safety Goggles` / `NO-Safety Goggles` | YES |
| Safety Boots | `Boots` / `NO-Boots` | YES |

---

## 6. Timeline

| Milestone | Target | Status |
|-----------|--------|--------|
| Documentation complete | Week 1 | 🔄 In Progress |
| Backend API + model integration | Week 1–2 | ⬜ Planned |
| Frontend UI | Week 2 | ⬜ Planned |
| Integration + testing | Week 2–3 | ⬜ Planned |
| Demo ready | Week 3 | ⬜ Planned |
| Real data collection (Phase 2) | After approval | ⬜ Planned |

---

## 7. Key Technical Decisions

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-03-13 | YOLOv8m pre-trained weights | Fastest path to working demo without custom training data |
| 2026-03-13 | Photo-based only (no real-time) | Sufficient for demo; real-time adds unnecessary complexity |
| 2026-03-13 | Docker Compose deployment | Must run offline on laptop during presentation |
| 2026-03-13 | Stateless API (no DB) | Demo scope; DB adds complexity not needed for Phase 1 |
| 2026-03-13 | 5 PPE classes | Best coverage with available pre-trained weights |

---

## 8. Related Documents

| Document | Path |
|----------|------|
| PRD | [PRD-safety-ppe-checker.md](./docs/01_product_requirements/prd/PRD-safety-ppe-checker.md) |
| Backlog | [backlog.md](./backlog.md) |
| System Architecture | [architecture.md](./docs/02_technical_specs/architecture.md) |
| CV Pipeline Tech Spec | [TP-CV-001.md](./docs/02_technical_specs/cv-engine/TP-CV-001.md) |
| Web Interface Epic | [EPIC-WEB-001.md](./docs/01_product_requirements/web-interface/EPIC-WEB-001.md) |
| CV Engine Epic | [EPIC-CV-001.md](./docs/01_product_requirements/cv-engine/EPIC-CV-001.md) |
