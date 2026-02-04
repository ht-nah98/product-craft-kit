# Template: README cho Folder Tài liệu Kỹ thuật

> Đây là file hướng dẫn cho AI và team khi làm việc với thư mục này.

---

## Tổng quan

Đây là thư mục chứa tài liệu kỹ thuật của dự án, bao gồm:
- Kiến trúc tổng quan hệ thống
- Tài liệu kỹ thuật dùng chung
- Tài liệu kỹ thuật theo từng module

---

## Cấu trúc thư mục

```
3_technical_docs/
├── README.md                       # File hướng dẫn này
├── architecture.md                 # Kiến trúc tổng quan hệ thống
│
├── shared/                         # Tài liệu kỹ thuật dùng chung
│   ├── authentication.md           # Authentication
│   ├── development_setup.md        # Hướng dẫn setup môi trường
│   ├── database_conventions.md     # Quy tắc database
│   └── coding_conventions.md       # Quy tắc code
│
├── [module_01]/                    # Module 1
│   ├── README.md                   # Tổng quan module
│   ├── database_schema.md          # Database schema (ERD)
│   ├── api_endpoints.md            # REST API specifications
│   └── authorization.md            # Phân quyền và Authorization
│
└── [module_02]/                    # Module 2
    └── ...
```

---

## Quy tắc

### Quy tắc tổ chức

1. **Thư mục shared/**: Chứa tài liệu kỹ thuật dùng chung cho toàn hệ thống

2. **Thư mục module/**: Mỗi module một thư mục riêng
   - Chứa tài liệu kỹ thuật chi tiết cho module đó

3. **Đặt tên file**: Sử dụng snake_case (ví dụ: `database_schema.md`, `api_endpoints.md`)

### Quy tắc viết tài liệu

1. Sử dụng markdown
2. Sử dụng mermaid hoặc text-based để vẽ diagram
3. Luôn link đến các tài liệu liên quan ở cuối mỗi file
4. Database Schema nên dùng mermaid ERD

### Quy tắc DRY

- Không lặp lại mô tả đã có trong shared/
- Tham chiếu bằng link: `[Xem Authentication](./shared/authentication.md)`
- Chỉ mô tả các chi tiết đặc thù của module

---

## Hướng dẫn đọc tài liệu

1. Đọc `architecture.md` - hiểu tổng quan kiến trúc
2. Đọc `shared/development_setup.md` - setup môi trường
3. Đọc tài liệu module cần làm việc

---

## Tài liệu liên quan

- [Tài liệu nghiệp vụ](../1_business_docs/)
- [Tài liệu tính năng](../2_features_docs/)
- [Kế hoạch triển khai](../4_plans_docs/)

