# Product Backlog — Safety PPE Checker

**Phase**: 1 — Demo/POC
**Last Updated**: 2026-03-13

---

## Sprint 1 — Backend Foundation (Week 1–2)

| # | Story | Points | Status |
|---|-------|--------|--------|
| 1 | Project setup: Docker Compose skeleton (frontend + backend services) | 2 | ⬜ Todo |
| 2 | Backend: FastAPI app init + CORS + health endpoint | 1 | ⬜ Todo |
| 3 | Backend: Download + integrate YOLOv8m pre-trained PPE weights | 2 | ⬜ Todo |
| 4 | [US-CV-001](./docs/01_product_requirements/cv-engine/US-CV-001.md) Detect PPE items from image | 5 | ⬜ Todo |
| 5 | [US-CV-002](./docs/01_product_requirements/cv-engine/US-CV-002.md) Compliance report (PASS/FAIL) | 3 | ⬜ Todo |
| 6 | Backend: Annotate image + return base64 (US-CV-003) | 3 | ⬜ Todo |
| 7 | Backend: Unit tests (detector + compliance engine) | 2 | ⬜ Todo |

**Sprint 1 Total**: 18 points

---

## Sprint 2 — Frontend + Integration (Week 2–3)

| # | Story | Points | Status |
|---|-------|--------|--------|
| 8 | Frontend: Next.js project setup + Tailwind + shadcn/ui | 1 | ⬜ Todo |
| 9 | [US-WEB-001](./docs/01_product_requirements/web-interface/US-WEB-001.md) Upload zone (drag-drop + validation) | 3 | ⬜ Todo |
| 10 | Frontend: Display annotated image + loading state (US-WEB-002) | 3 | ⬜ Todo |
| 11 | Frontend: PPE compliance checklist + PASS/FAIL banner (US-WEB-003) | 2 | ⬜ Todo |
| 12 | [US-WEB-004](./docs/01_product_requirements/web-interface/US-WEB-004.md) Demo mode with sample images | 2 | ⬜ Todo |
| 13 | Integration: Frontend ↔ Backend API wiring | 2 | ⬜ Todo |
| 14 | Collect + prepare 4 demo sample images (diverse scenarios) | 1 | ⬜ Todo |
| 15 | End-to-end testing: upload → analyze → display results | 2 | ⬜ Todo |
| 16 | Docker Compose: verify full offline run on clean machine | 1 | ⬜ Todo |

**Sprint 2 Total**: 17 points

---

## Phase 2 Backlog (After demo approval — not started)

| # | Story | Notes |
|---|-------|-------|
| P2-1 | Collect 500+ real electrical worker images from company cameras | Need stakeholder approval |
| P2-2 | Annotate dataset with CVAT (5 PPE classes + arc suit + harness) | Labeling effort |
| P2-3 | Fine-tune YOLOv8l on company dataset | 100 epochs |
| P2-4 | Add arc flash suit detection class | Requires domain-specific data |
| P2-5 | Add harness detection class | Requires pose estimation pipeline |
| P2-6 | Real-time RTSP camera stream processing | Architecture upgrade |
| P2-7 | Worker identity linking (badge ID or face recognition) | Privacy considerations |
| P2-8 | PostgreSQL: event log for compliance history | Database layer |
| P2-9 | S3/storage: save analyzed images as evidence | Storage layer |
| P2-10 | Permit-to-work API integration | External system dependency |
| P2-11 | Authentication + role-based access (worker, supervisor, EHS manager) | Security layer |
| P2-12 | Mobile-responsive UI | UX improvement |
| P2-13 | Dashboard: compliance rate over time, violation trends | Analytics layer |

---

## Definition of Done — Demo MVP

- [ ] Backend: `POST /api/analyze` works correctly end-to-end
- [ ] All 5 PPE classes detected correctly on test images
- [ ] Frontend: upload + annotated result + checklist display all work
- [ ] Demo mode: 4 sample images available and auto-analyze on click
- [ ] Docker Compose: `docker compose up` → full app running at localhost:3000
- [ ] Offline capable: works with no internet after `docker compose up`
- [ ] Inference time ≤ 3 seconds on demo laptop CPU
