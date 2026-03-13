# US-WEB-005: Xem confidence score cho từng PPE item

> **Epic**: [EPIC-WEB-001](./EPIC-WEB-001.md)
> **Priority**: 🟠 Should Have | **Points**: 1

---

## User Story

**As a** demo viewer or developer,
**I want to** see the AI confidence score (%) for each detected PPE item,
**So that** I can understand how certain the AI is about each detection and explain the technology credibly to stakeholders.

---

## Context

Confidence score giúp stakeholder hiểu rằng AI không chỉ trả Yes/No mà còn có thước đo mức độ chắc chắn. Điều này tăng tính thuyết phục khi demo. Với developer, đây là thông tin debug quan trọng.

---

## Acceptance Criteria

### AC1: Confidence score hiển thị trong checklist cho detected items
**Given** Helmet được phát hiện với confidence 0.924
**When** checklist render
**Then** dòng Helmet hiển thị: "✓ Helmet — 92%"
**And** số % được format là số nguyên (không decimal)

### AC2: Confidence không hiển thị cho missing items
**Given** Gloves không được phát hiện
**When** checklist render
**Then** dòng Gloves hiển thị: "✗ Gloves — Not detected"
**And** không hiển thị "0%" (misleading)

### AC3: Confidence thấp được cảnh báo
**Given** Safety Vest được phát hiện với confidence 0.52 (vừa qua threshold)
**When** checklist render
**Then** dòng đó hiển thị màu vàng/amber thay vì xanh lá
**And** tooltip: "Low confidence detection — verify visually"
**And** ngưỡng cảnh báo: confidence < 0.70

### AC4: Confidence trên bounding box đồng nhất với checklist
**Given** Helmet confidence là 92% trong checklist
**When** xem ảnh annotated
**Then** label trên bounding box cũng hiển thị "Helmet 92%"
**And** 2 số phải khớp nhau

---

## Definition of Done
- [ ] Confidence % hiển thị đúng trong checklist
- [ ] Format: số nguyên + % (vd: 92%)
- [ ] "Not detected" cho missing items (không hiện 0%)
- [ ] Cảnh báo màu vàng cho confidence < 70%
- [ ] Nhất quán giữa checklist và bounding box label
