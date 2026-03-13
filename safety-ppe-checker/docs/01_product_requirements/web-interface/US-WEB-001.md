# US-WEB-001: Upload ảnh để kiểm tra PPE

> **Epic**: [EPIC-WEB-001](./EPIC-WEB-001.md)
> **Priority**: 🔴 Must Have | **Points**: 3

---

## User Story

**As a** demo presenter or safety supervisor,
**I want to** upload a full-body photo of an electrical worker,
**So that** the AI can analyze whether the worker is wearing all required PPE.

---

## Acceptance Criteria

### AC1: Upload ảnh thành công
**Given** tôi mở web app
**When** tôi kéo thả hoặc click chọn ảnh JPG/PNG/WEBP ≤ 10MB
**Then** ảnh được preview trên giao diện
**And** button "Analyze" được enable

### AC2: Validate file type
**Given** tôi cố upload file không phải ảnh (PDF, TXT, v.v.)
**When** file được chọn hoặc drop
**Then** hiển thị thông báo lỗi: "Please upload an image file (JPG, PNG, WEBP)"
**And** file bị từ chối

### AC3: Validate file size
**Given** tôi cố upload ảnh > 10MB
**When** file được chọn
**Then** hiển thị thông báo lỗi: "File size must be under 10MB"
**And** file bị từ chối

### AC4: Loading state khi đang phân tích
**Given** tôi đã upload ảnh hợp lệ
**When** tôi click "Analyze"
**Then** hiển thị loading spinner
**And** button "Analyze" bị disable để tránh double-submit

### AC5: Reset để upload ảnh mới
**Given** tôi đã xem kết quả của 1 ảnh
**When** tôi click "Analyze New Photo"
**Then** form reset về trạng thái ban đầu
**And** kết quả cũ bị xóa

---

## Definition of Done
- [ ] Drag-and-drop và file browser đều hoạt động
- [ ] Validation file type và size hoạt động
- [ ] Preview ảnh hiển thị sau khi chọn
- [ ] Loading state hiển thị khi đang chờ
- [ ] Reset hoạt động đúng
