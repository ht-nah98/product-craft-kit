# US-WEB-002: Xem ảnh annotated với bounding boxes

> **Epic**: [EPIC-WEB-001](./EPIC-WEB-001.md)
> **Priority**: 🔴 Must Have | **Points**: 3

---

## User Story

**As a** demo viewer or safety supervisor,
**I want to** see the original photo with colored bounding boxes drawn around each detected PPE item,
**So that** I can visually understand exactly which items the AI detected and where on the worker's body.

---

## Context

Đây là bằng chứng trực quan quan trọng nhất trong demo. Stakeholder nhìn vào ảnh annotated ngay lập tức hiểu AI đang làm gì — không cần đọc số liệu hay giải thích kỹ thuật.

---

## Acceptance Criteria

### AC1: Hiển thị ảnh annotated sau khi phân tích xong
**Given** tôi đã upload ảnh và nhấn Analyze
**When** AI xử lý xong và trả kết quả
**Then** ảnh annotated hiển thị trong Results Panel
**And** loading spinner biến mất

### AC2: Bounding box màu xanh lá cho item được phát hiện
**Given** AI phát hiện Helmet với confidence 0.92
**When** ảnh annotated được render
**Then** có hình chữ nhật màu xanh lá bao quanh khu vực mũ bảo hộ
**And** label hiển thị: "Helmet 92%"

### AC3: Không vẽ box cho item không detect được (chỉ dùng checklist)
**Given** AI không phát hiện Gloves
**When** ảnh annotated được render
**Then** không có bounding box màu đỏ/không liên quan vẽ trên ảnh
**And** thông tin missing Gloves chỉ hiển thị trong Checklist (US-WEB-003)

### AC4: Label text rõ ràng, không bị cắt
**Given** bounding box nằm gần mép ảnh
**When** label được vẽ
**Then** label text không bị cắt ngoài rìa ảnh
**And** text vẫn đọc được (contrast đủ)

### AC5: Ảnh gốc và ảnh annotated hiển thị cạnh nhau
**Given** kết quả được trả về
**When** trang hiển thị results
**Then** ảnh gốc (trái) và ảnh annotated (phải) hiển thị song song
**And** cả 2 ảnh cùng kích thước hiển thị

### AC6: Ảnh annotated có thể xem to hơn
**Given** tôi muốn xem chi tiết bounding boxes
**When** tôi click vào ảnh annotated
**Then** ảnh mở rộng ra (modal hoặc lightbox)
**And** có thể đóng lại bằng click bên ngoài hoặc button X

---

## Definition of Done
- [ ] Bounding boxes vẽ đúng vị trí trên ảnh
- [ ] Màu xanh lá cho detected items
- [ ] Label gồm tên PPE + confidence %
- [ ] Layout 2 cột: original | annotated
- [ ] Click-to-enlarge hoạt động
- [ ] Tested: ảnh dọc, ảnh ngang, ảnh vuông đều hiển thị đúng
