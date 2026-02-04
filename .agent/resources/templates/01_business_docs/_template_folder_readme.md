# Template: README cho Folder Tài liệu Nghiệp vụ

> Đây là file hướng dẫn cho AI và team khi làm việc với thư mục này.

---

## Tổng quan

Đây là thư mục chứa tài liệu logic nghiệp vụ của dự án.

---

## Cấu trúc thư mục

```
1_business_docs/
├── README.md                       # File hướng dẫn này
├── overview.md                     # Tổng quan nghiệp vụ hệ thống
├── glossary.md                     # Thuật ngữ và viết tắt
│
├── [module_01]/                    # Module nghiệp vụ 1
│   ├── [topic_1].md
│   └── [topic_2].md
│
├── [module_02]/                    # Module nghiệp vụ 2
│   └── ...
│
└── shared/                         # Nghiệp vụ dùng chung
    └── [shared_topic].md
```

> **Hướng dẫn**: Thay `[module_xx]` và `[topic_x]` bằng tên thực của dự án

---

## Quy tắc

1. Mỗi khi có file tài liệu nghiệp vụ mới, hãy cập nhật cấu trúc thư mục trong README này.
2. Đặt tên file: sử dụng `snake_case` (ví dụ: `user_roles.md`, `approval_workflow.md`)
3. Mỗi module nghiệp vụ đặt trong folder riêng

---

## Hướng dẫn đọc tài liệu

1. **Bắt đầu**: Đọc `overview.md` để hiểu tổng quan nghiệp vụ
2. **Theo module**: Đọc tài liệu theo từng module tương ứng
3. **Thuật ngữ**: Tra cứu `glossary.md` khi gặp thuật ngữ chưa rõ

---

## Tài liệu liên quan

- [Tài liệu tính năng](../2_features_docs/)
- [Tài liệu kỹ thuật](../3_technical_docs/)
- [Kế hoạch triển khai](../4_plans_docs/)

