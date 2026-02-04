# Template: README cho Folder Tài liệu Tính năng

> Đây là file hướng dẫn cho AI và team khi làm việc với thư mục này.

---

## Tổng quan

Đây là thư mục chứa tài liệu mô tả tính năng của hệ thống, bao gồm:
- Mô tả màn hình (screens)
- Wireframes (text-based)
- Thành phần UI dùng chung
- Nguyên tắc thiết kế

---

## Nguyên tắc thiết kế: [TÊN NGUYÊN TẮC]

> **QUAN TRỌNG**: Mô tả nguyên tắc thiết kế chính của dự án (VD: Compact UI, Material Design, etc.)

### Đặc điểm

| Thành phần | Kích thước/Giá trị |
|------------|-------------------|
| [Component 1] | [Value] |
| [Component 2] | [Value] |

### Nguyên tắc chung

1. [Nguyên tắc 1]
2. [Nguyên tắc 2]
3. [Nguyên tắc 3]

---

## Cấu trúc thư mục

```
2_features_docs/
├── README.md                       # File hướng dẫn này
├── _template-screen.md             # Template cho tài liệu màn hình
│
├── shared/                         # Thành phần dùng chung
│   ├── layouts/                    # Bố cục giao diện
│   │   ├── main-layout.md
│   │   ├── header.md
│   │   ├── sidebar.md
│   │   └── footer.md
│   ├── components/                 # UI components
│   │   ├── buttons.md
│   │   ├── forms.md
│   │   ├── tables.md
│   │   ├── modals.md
│   │   └── cards.md
│   └── patterns/                   # Nguyên tắc thiết kế
│       ├── responsive.md
│       ├── validation.md
│       ├── pagination.md
│       └── error-handling.md
│
├── [module_01]/                    # Module 1
│   ├── [screen-1].md
│   └── [screen-2].md
│
└── [module_02]/                    # Module 2
    └── ...
```

---

## Quy tắc

### Quy tắc tổ chức

1. **Thư mục shared/**: Chứa các thành phần dùng chung
   - layouts/: Bố cục giao diện
   - components/: UI components
   - patterns/: Nguyên tắc thiết kế

2. **Thư mục module/**: Mỗi module một thư mục riêng
   - Mỗi màn hình là một file markdown
   - File README.md tổng hợp danh sách màn hình

3. **Đặt tên file**: Sử dụng kebab-case (ví dụ: `user-list.md`, `order-detail.md`)

### Quy tắc viết tài liệu màn hình

1. Sử dụng template màn hình làm cấu trúc chuẩn
2. Mô tả wireframe bằng text-based (ASCII art)
3. Liệt kê đầy đủ các tính năng với ID
4. Mô tả chi tiết validation và business logic
5. **Quan trọng**: Ưu tiên sử dụng thành phần dùng chung
6. Link đến các thành phần dùng chung trong shared/

### Quy tắc DRY

- Không lặp lại mô tả thành phần đã có trong shared/
- Tham chiếu bằng link: `[Xem chi tiết Button](../shared/components/buttons.md)`
- Chỉ mô tả các behavior đặc thù của màn hình

---

## Hướng dẫn đọc tài liệu

1. **Bắt đầu với shared/**: Hiểu các thành phần dùng chung trước
2. **Chọn module**: Vào thư mục module cần xem
3. **Đọc README.md**: Xem tổng quan danh sách màn hình
4. **Đọc từng màn hình**: Chi tiết UI và logic

---

## Hướng dẫn viết tài liệu mới

1. Copy file `_template-screen.md`
2. Đổi tên file theo quy tắc kebab-case
3. Điền nội dung theo template
4. Cập nhật README.md của module
5. Cập nhật cấu trúc thư mục trong file này

---

## Tài liệu liên quan

- [Tài liệu nghiệp vụ](../1_business_docs/)
- [Tài liệu kỹ thuật](../3_technical_docs/)
- [Kế hoạch triển khai](../4_plans_docs/)

