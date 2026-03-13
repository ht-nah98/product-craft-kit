# US-WEB-004: Demo mode với ảnh mẫu

> **Epic**: [EPIC-WEB-001](./EPIC-WEB-001.md)
> **Priority**: 🔴 Must Have | **Points**: 2

---

## User Story

**As a** demo presenter,
**I want to** click on pre-loaded sample images instead of uploading real photos,
**So that** I can run a live demo without needing actual worker photos available.

---

## Acceptance Criteria

### AC1: Hiển thị demo images
**Given** tôi mở web app
**When** trang load xong
**Then** thấy section "Demo Images" với ít nhất 4 ảnh thumbnail
**And** mỗi ảnh có label mô tả: "Fully Compliant", "Missing Helmet", "Missing Gloves", "Multiple Violations"

### AC2: Click demo image tự động analyze
**Given** tôi thấy section demo images
**When** tôi click một ảnh thumbnail
**Then** ảnh đó được load vào upload zone
**And** analysis tự động bắt đầu mà không cần click "Analyze"

### AC3: Demo images đa dạng scenarios
**Given** bộ demo images được chuẩn bị
**Then** phải bao gồm:
- Ít nhất 1 ảnh: PASS (đủ tất cả 5 PPE)
- Ít nhất 1 ảnh: FAIL thiếu 1 item
- Ít nhất 1 ảnh: FAIL thiếu nhiều items
- Ít nhất 1 ảnh: điều kiện ánh sáng/góc chụp khác

---

## Definition of Done
- [ ] 4+ demo images được tích hợp sẵn trong app
- [ ] Click demo image → auto analyze hoạt động
- [ ] Mỗi demo image cover một scenario khác nhau
- [ ] Demo images được lưu trong frontend bundle (không cần fetch từ server)
