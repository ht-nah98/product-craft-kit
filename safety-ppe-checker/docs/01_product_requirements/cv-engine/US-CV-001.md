# US-CV-001: Detect PPE items từ ảnh upload

> **Epic**: [EPIC-CV-001](./EPIC-CV-001.md)
> **Priority**: 🔴 Must Have | **Points**: 5

---

## User Story

**As a** system (backend),
**I want to** run YOLOv8 inference on an uploaded image and detect all PPE items,
**So that** the compliance engine has accurate detection data to assess safety.

---

## Acceptance Criteria

### AC1: Detect các PPE items có mặt
**Given** ảnh upload của 1 nhân viên mặc đủ Helmet, Vest, Gloves, Goggles, Boots
**When** model chạy inference
**Then** cả 5 items đều được detect với confidence ≥ 0.50
**And** bounding box của mỗi item nằm đúng vị trí trên cơ thể

### AC2: Detect trường hợp thiếu PPE
**Given** ảnh nhân viên không đeo Helmet và không mặc Vest
**When** model chạy inference
**Then** `NO-Hardhat` và `NO-Safety Vest` được detect (hoặc `Hardhat`/`Safety Vest` không có trong detections)
**And** compliance engine đánh dấu 2 items đó là MISSING

### AC3: Confidence threshold
**Given** model detect một item với confidence < 0.50
**When** compliance engine xử lý kết quả
**Then** detection đó bị loại bỏ (treated as not detected)

### AC4: Single person assumption
**Given** ảnh chứa nhiều hơn 1 người
**When** model chạy inference
**Then** chỉ xử lý người có bounding box lớn nhất / trung tâm nhất (primary subject)
**And** kết quả trả về cho 1 người duy nhất

### AC5: Inference time
**Given** ảnh JPG kích thước 1080×1920px
**When** inference chạy trên CPU (không có GPU)
**Then** kết quả trả về trong vòng ≤ 3000ms

### AC6: Invalid image handling
**Given** file được upload bị corrupt hoặc không parse được
**When** model cố load ảnh
**Then** raise exception và API trả về HTTP 400 với message rõ ràng

---

## Technical Notes
- Model: `yolov8m.pt` fine-tuned trên Ultralytics Construction-PPE dataset
- Input image được resize về `640×640` trước inference (standard YOLO input)
- Confidence threshold: `conf=0.5`, IoU threshold: `iou=0.45`
- Model load 1 lần khi server startup, không load lại per request

---

## Definition of Done
- [ ] Model load thành công từ `.pt` file khi server start
- [ ] `/api/analyze` endpoint nhận ảnh và chạy inference
- [ ] 5 PPE classes detect đúng trên test images
- [ ] Negative classes (NO-Hardhat, etc.) xử lý đúng
- [ ] Confidence threshold 0.5 được áp dụng
- [ ] Inference time ≤ 3 giây trên demo laptop CPU
