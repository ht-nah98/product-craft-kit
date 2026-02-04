# Template: Phase [X]: [Tên Phase]

> Mô tả ngắn gọn mục tiêu của phase.

---

## Tổng quan

[Mô tả chi tiết phase này làm gì, bao gồm những gì]

**Tham chiếu patterns**: [Nếu có module/phase trước đã hoàn thành để tham khảo]

---

## Trạng thái: ⬜ Chưa bắt đầu

| Sub-phase | File | Trạng thái |
|-----------|------|------------|
| [X.1] [Tên sub-phase 1] | [sub-1-name.md](./sub-1-name.md) | ⬜ Chưa bắt đầu |
| [X.2] [Tên sub-phase 2] | [sub-2-name.md](./sub-2-name.md) | ⬜ Chưa bắt đầu |
| [X.3] [Tên sub-phase 3] | [sub-3-name.md](./sub-3-name.md) | ⬜ Chưa bắt đầu |

**Trạng thái:**
- ✅ Hoàn thành
- 🔄 Đang thực hiện
- ⬜ Chưa bắt đầu

---

## Thứ tự triển khai

```
Sub-phase X.1 → Sub-phase X.2 → Sub-phase X.3
```

**Dependencies:**
- X.1 → X.2: [Mô tả tại sao X.2 phụ thuộc X.1]
- X.2 → X.3: [Mô tả dependency]

---

## Tài liệu tham chiếu

### Tài liệu nghiệp vụ
- [Tài liệu 1](../../1_business_docs/[path])
- [Tài liệu 2](../../1_business_docs/[path])

### Tài liệu tính năng
- [Màn hình 1](../../2_features_docs/[path])
- [Màn hình 2](../../2_features_docs/[path])

### Tài liệu kỹ thuật
- [Kiến trúc](../../3_technical_docs/architecture.md)
- [Database Schema](../../3_technical_docs/[module]/database_schema.md)

### Code tham chiếu (nếu có)
- [Path to reference code]

---

## Ghi chú triển khai

> **QUAN TRỌNG:** Trong quá trình triển khai, mỗi khi hoàn thành một task/sub-phase, hãy cập nhật trạng thái vào file này và file [README.md](../README.md).

