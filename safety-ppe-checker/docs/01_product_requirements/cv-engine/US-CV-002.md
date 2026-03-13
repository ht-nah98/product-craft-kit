# US-CV-002: Tạo compliance report (PASS/FAIL)

> **Epic**: [EPIC-CV-001](./EPIC-CV-001.md)
> **Priority**: 🔴 Must Have | **Points**: 3

---

## User Story

**As a** safety supervisor or demo viewer,
**I want to** see a clear PASS or FAIL result with details of which PPE items are missing,
**So that** I can immediately understand whether a worker is compliant without needing to interpret bounding boxes.

---

## Acceptance Criteria

### AC1: PASS khi đủ tất cả PPE
**Given** model detect đủ cả 5 PPE required items (confidence ≥ 0.5)
**When** compliance engine đánh giá kết quả
**Then** response trả về `"overall_pass": true` và `"status": "PASS"`
**And** `"missing_items": []`

### AC2: FAIL khi thiếu bất kỳ 1 PPE item
**Given** model không detect được Helmet (confidence < 0.5 hoặc không có)
**When** compliance engine đánh giá
**Then** response trả về `"overall_pass": false` và `"status": "FAIL"`
**And** `"missing_items": ["Helmet"]`

### AC3: Missing items list đúng và đầy đủ
**Given** ảnh thiếu Helmet và Gloves
**When** compliance engine xử lý
**Then** `"missing_items": ["Helmet", "Gloves"]` (đúng thứ tự, đúng tên)

### AC4: Mỗi detection item có đầy đủ thông tin
**Given** model trả kết quả inference
**When** compliance engine format response
**Then** mỗi item trong `detections` có: `label`, `confidence`, `detected` (bool), `bbox` (hoặc null nếu không detect)

### AC5: Inference time được ghi nhận
**Given** request analyze hoàn thành
**Then** response bao gồm `"inference_time_ms"` = thời gian thực tế chạy inference (không bao gồm upload time)

---

## Definition of Done
- [ ] PASS/FAIL logic đúng cho tất cả combinations
- [ ] `missing_items` list chính xác
- [ ] Response JSON đúng schema (validated bởi Pydantic model)
- [ ] `inference_time_ms` có trong response
- [ ] Unit tests cho compliance engine (5+ test cases)
