# CLAUDE.md

Đây là file hướng dẫn cho Claude Code khi làm việc trong dự án này.

## Tổng quan dự án

ProjectName - Description.
Mô tả về các kỹ thuật và công nghệ dùng trong dự án

___
## Cấu trúc thư mục
```
name_project/
    docs/                       # Tài liệu cho dự án
        1_business_docs/        # Tài liệu về nghiệp vụ
        2_features_docs/        # Tài liệu về thiết kế màn hình và tính năng
        3_technical_docs/       # Tài liệu kỹ thuật dự án
        4_plans_docs/           # Các kế hoạch triển khai
        5_testing_docs/         # Tài liệu về chiến lược và hướng dẫn testing
    src/                        # Source code dự án
    tests/                      # Unit tests và intergration tests
```

___
## Quy tắc
### Quy tắc chung
- Luôn sử dụng Tiếng Việt để giao tiếp.

### Quy tắc tài liệu
- Sử dụng Tiếng Việt để viết tài liệu.
- Luôn đặt tài liệu vào đúng thư mục tương ứng.
- Sử dụng định dạng markdown.
- Sử dụng mermaid hoặc text-based để vẽ diagram.
- Quy tắc DRY (don't repeat yourself): khi thấy có một phần nội dung tài liệu là nội dung dùng chung, hoặc có thể dùng chung ở nhiều files khác, thì hãy tách phần nội dung đó ra thành file riêng, và link file này vào để thay thế nội dung.
- Tài liệu viết đủ các ý chính, không dài dòng và không quá chi tiết.

### Quy tắc triển khai code

___
## Hướng dẫn
1. Luôn luôn đọc thật kỹ các file sau để hiểu cấu trúc repo, để dễ tìm được các thông tin cần thiết khi cần:
   1. [README.md - Business document](./docs/1_business_docs/README.md)
   2. [README.md - Features document](./docs/2_features_docs/README.md)
   3. [README.md - Technical document](./docs/3_technical_docs/README.md)
   4. [README.md - Plans document](./docs/4_plans_docs/README.md)
   5. [README.md - Testing document](./docs/5_testing_docs/README.md)
   6. [README.md - Source code](./src/README.md)