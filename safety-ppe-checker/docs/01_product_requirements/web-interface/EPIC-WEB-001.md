# EPIC-WEB-001: Web Demo Interface

> Giao diện web cho phép upload ảnh và xem kết quả kiểm tra PPE

---

## 1. Thông tin chung

| Mục | Nội dung |
|-----|----------|
| Epic ID | EPIC-WEB-001 |
| Module | Web Interface |
| Status | 📝 Draft |
| Priority | 🔴 Critical |
| Phase | Phase 1 — Demo |

---

## 2. Tổng quan

### Bối cảnh
Để demo tính năng AI PPE detection cho stakeholders, cần một giao diện web đơn giản, trực quan. Người xem demo phải hiểu ngay kết quả mà không cần giải thích kỹ thuật.

### Mục tiêu
- Cho phép upload ảnh toàn thân nhân viên
- Hiển thị kết quả AI một cách trực quan: ảnh annotated + checklist + PASS/FAIL
- Có bộ ảnh demo mẫu để presenter có thể dùng ngay

### Business Value
Demo thành công → stakeholders hiểu và tin tưởng vào khả năng của AI → phê duyệt thu thập dữ liệu thực

---

## 3. Phạm vi

### In-scope ✅
- Upload ảnh (JPG, PNG, WEBP, ≤ 10MB)
- Hiển thị loading state trong khi AI xử lý
- Hiển thị ảnh annotated với bounding boxes
- Hiển thị PPE checklist với ✓/✗ và confidence score
- PASS/FAIL banner nổi bật
- Demo mode với ảnh mẫu có sẵn
- Responsive layout cho màn hình laptop

### Out-of-scope ❌
- Authentication / login
- Lưu lịch sử kết quả
- Download/export report
- Mobile layout tối ưu
- Multi-language (chỉ Tiếng Anh cho demo)

---

## 4. User Stories

| Story ID | Tên | Priority | Points |
|----------|-----|----------|--------|
| [US-WEB-001](./US-WEB-001.md) | Upload ảnh để kiểm tra | Must Have | 3 |
| [US-WEB-002](./US-WEB-002.md) | Xem kết quả annotated image | Must Have | 3 |
| [US-WEB-003](./US-WEB-003.md) | Xem PPE compliance checklist | Must Have | 2 |
| [US-WEB-004](./US-WEB-004.md) | Sử dụng demo mode với ảnh mẫu | Must Have | 2 |

**Total: 10 points**

---

## 5. UI Layout

```
┌──────────────────────────────────────────────────────────┐
│  🦺 Safety PPE Compliance Checker                  [Logo] │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ┌────────────────────┐  ┌───────────────────────────┐  │
│  │   Upload / Demo    │  │      Results Panel         │  │
│  │                    │  │                            │  │
│  │  ┌──────────────┐  │  │  [Annotated Image]         │  │
│  │  │ Drag & Drop  │  │  │                            │  │
│  │  │    or        │  │  │  ┌────────────────────┐   │  │
│  │  │  [Browse...] │  │  │  │ ✅ PASS / ❌ FAIL   │   │  │
│  │  └──────────────┘  │  │  └────────────────────┘   │  │
│  │                    │  │                            │  │
│  │  Demo Images:      │  │  PPE Checklist:            │  │
│  │  [img1][img2]      │  │  ✓ Helmet      (92%)       │  │
│  │  [img3][img4]      │  │  ✓ Safety Vest (88%)       │  │
│  │                    │  │  ✗ Gloves      (missing)   │  │
│  │  [Analyze ▶]       │  │  ✓ Goggles     (79%)       │  │
│  └────────────────────┘  │  ✓ Boots       (85%)       │  │
│                          └───────────────────────────┘  │
└──────────────────────────────────────────────────────────┘
```

---

## 6. Definition of Done

- [ ] Upload hoạt động với JPG, PNG, WEBP ≤ 10MB
- [ ] Loading state hiển thị trong khi chờ AI
- [ ] Annotated image hiển thị đúng bounding boxes
- [ ] PASS/FAIL banner hiển thị đúng màu
- [ ] Checklist hiển thị đủ 5 PPE items
- [ ] 4 demo images sẵn có và hoạt động
- [ ] Chạy được trong Docker (localhost:3000)
- [ ] Tested trên Chrome, Firefox

---

## Related
- [PRD](../prd/PRD-safety-ppe-checker.md)
- [EPIC-CV-001](../cv-engine/EPIC-CV-001.md)
