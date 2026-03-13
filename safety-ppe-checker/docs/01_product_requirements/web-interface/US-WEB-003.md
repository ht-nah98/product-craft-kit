# US-WEB-003: Xem PPE compliance checklist và PASS/FAIL

> **Epic**: [EPIC-WEB-001](./EPIC-WEB-001.md)
> **Priority**: 🔴 Must Have | **Points**: 2

---

## User Story

**As a** safety supervisor or demo viewer,
**I want to** see a clear checklist showing which PPE items are present and which are missing, plus an overall PASS or FAIL verdict,
**So that** I can immediately know the compliance status without having to interpret the annotated image.

---

## Context

Checklist là phần "kết luận" của toàn bộ analysis. Người xem demo cần thấy 2 thứ ngay lập tức: (1) Nhân viên này có đủ PPE không? (PASS/FAIL) và (2) Nếu thiếu, thiếu cái gì?

---

## Acceptance Criteria

### AC1: Banner PASS màu xanh khi đủ tất cả PPE
**Given** AI phát hiện đủ cả 5 PPE required items
**When** kết quả được hiển thị
**Then** banner lớn màu xanh lá hiển thị: "✅ COMPLIANT — All PPE requirements met"

### AC2: Banner FAIL màu đỏ khi thiếu PPE
**Given** AI không phát hiện được Helmet và Gloves
**When** kết quả được hiển thị
**Then** banner lớn màu đỏ hiển thị: "❌ NON-COMPLIANT — 2 items missing"

### AC3: Checklist hiển thị trạng thái từng PPE item
**Given** kết quả analysis hoàn thành
**When** checklist render
**Then** hiển thị đủ 5 dòng:
  - ✓ Helmet — detected (màu xanh)
  - ✓ Safety Vest — detected (màu xanh)
  - ✗ Gloves — NOT DETECTED (màu đỏ, bold)
  - ✓ Safety Goggles — detected (màu xanh)
  - ✗ Boots — NOT DETECTED (màu đỏ, bold)

### AC4: Missing items được highlight rõ ràng
**Given** có items bị thiếu
**When** checklist render
**Then** các dòng FAIL có background đỏ nhạt hoặc icon cảnh báo
**And** các dòng PASS có background xanh nhạt hoặc icon check

### AC5: Tóm tắt số lượng
**Given** có 2 items bị thiếu
**When** hiển thị summary
**Then** hiển thị: "5/5 items checked — 3 detected, 2 missing"

### AC6: Checklist hiển thị trước khi analysis (placeholder state)
**Given** chưa có ảnh nào được phân tích
**When** trang load lần đầu
**Then** checklist hiển thị 5 dòng với icon chờ (⬜) và màu xám
**And** không hiển thị PASS/FAIL banner

---

## Definition of Done
- [ ] PASS banner màu xanh + FAIL banner màu đỏ đúng logic
- [ ] Tất cả 5 PPE items luôn hiển thị trong checklist
- [ ] Detected = icon ✓ xanh, Missing = icon ✗ đỏ bold
- [ ] Summary count chính xác
- [ ] Placeholder state khi chưa có kết quả
- [ ] Tested: PASS case, FAIL-1-item, FAIL-all-5 case
