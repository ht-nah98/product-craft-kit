# US-CV-003: Backend trả về ảnh đã annotated (base64)

> **Epic**: [EPIC-CV-001](./EPIC-CV-001.md)
> **Priority**: 🔴 Must Have | **Points**: 3

---

## User Story

**As a** frontend application,
**I want to** receive the annotated image (with bounding boxes drawn) directly in the API response as a base64 string,
**So that** I can display it immediately without making a second API call or storing files on disk.

---

## Context

Thiết kế stateless: backend không lưu file, không cần URL riêng cho ảnh. Toàn bộ kết quả trả về trong 1 JSON response duy nhất. Frontend decode base64 và render trực tiếp.

---

## Acceptance Criteria

### AC1: Response chứa annotated image dạng base64
**Given** inference chạy xong với detections
**When** API trả response
**Then** field `annotated_image` chứa string bắt đầu bằng `"data:image/jpeg;base64,"`
**And** string decode được thành ảnh JPEG hợp lệ

### AC2: Bounding boxes vẽ đúng trên ảnh gốc
**Given** Helmet được detect tại bbox [145, 23, 312, 198] với confidence 0.92
**When** annotator vẽ lên ảnh
**Then** hình chữ nhật màu xanh lá được vẽ tại tọa độ [145, 23, 312, 198]
**And** label "Helmet 92%" được vẽ phía trên box

### AC3: Màu sắc bounding box nhất quán
**Given** nhiều PPE items được detected
**When** annotator xử lý
**Then** tất cả detected items đều dùng màu xanh lá (RGB: 0, 200, 0)
**And** font size và độ dày đường kẻ đồng nhất

### AC4: Ảnh annotated cùng resolution với ảnh gốc
**Given** ảnh gốc kích thước 1080×1920px
**When** annotated image được encode
**Then** annotated image vẫn là 1080×1920px
**And** không bị resize hay crop

### AC5: JPEG quality đủ để xem rõ bounding boxes
**Given** ảnh được encode thành JPEG
**When** encode với quality=85
**Then** bounding boxes và labels vẫn nhìn rõ, không bị artifact nặng
**And** file size annotated image ≤ 3× file size ảnh gốc (compression efficient)

### AC6: Xử lý đúng khi không có detection nào
**Given** model không detect được bất kỳ PPE item nào (ảnh không có người)
**When** annotator chạy
**Then** trả về ảnh gốc không thay đổi (không có boxes)
**And** field `annotated_image` vẫn có giá trị (ảnh gốc dạng base64)

---

## Technical Notes
- Encoding: `cv2.imencode(".jpg", image, [cv2.IMWRITE_JPEG_QUALITY, 85])`
- Base64: `base64.b64encode(buffer).decode("utf-8")`
- Prefix: `"data:image/jpeg;base64," + b64_string`
- Màu bounding box BGR (OpenCV): `(0, 200, 0)` = xanh lá

---

## Definition of Done
- [ ] `annotated_image` field trong response là valid base64 JPEG
- [ ] Bounding boxes vẽ đúng tọa độ
- [ ] Màu xanh lá cho tất cả detected items
- [ ] Resolution ảnh annotated = ảnh gốc
- [ ] JPEG quality = 85
- [ ] Edge case: không có detection → trả ảnh gốc
- [ ] Unit test: decode base64 → valid image
