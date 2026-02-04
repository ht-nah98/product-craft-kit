# Documentation Templates for AI Systems

> Bộ template tài liệu tinh hoa được trích xuất từ các dự án thực tế. Dành cho AI đọc hiểu và tạo tài liệu cho các dự án mới.

---

## Mục đích

Bộ template này cung cấp:
1. **Cấu trúc chuẩn** cho 5 loại tài liệu phần mềm
2. **Quy tắc viết** tài liệu hiệu quả
3. **Template có thể tái sử dụng** cho mọi dự án, bất kể ngôn ngữ/công nghệ
4. **Hướng dẫn cho AI** để đọc hiểu và tạo tài liệu tương tự

---

## Cấu trúc thư mục

```
_documentation_templates/
├── README.md                           # File này - Hướng dẫn tổng quan
├── 00_ai_instructions.md               # Hướng dẫn cho AI đọc và viết tài liệu
│
├── 01_business_docs/                   # Tài liệu nghiệp vụ
│   ├── _template_folder_readme.md      # Template README cho folder
│   ├── _template_overview.md           # Template tổng quan nghiệp vụ
│   ├── _template_glossary.md           # Template thuật ngữ
│   └── _template_module.md             # Template module nghiệp vụ
│
├── 02_features_docs/                   # Tài liệu tính năng/UI
│   ├── _template_folder_readme.md      # Template README cho folder
│   ├── _template_screen.md             # Template màn hình
│   └── _template_shared_component.md   # Template component dùng chung
│
├── 03_technical_docs/                  # Tài liệu kỹ thuật
│   ├── _template_folder_readme.md      # Template README cho folder
│   ├── _template_architecture.md       # Template kiến trúc hệ thống
│   └── _template_database_schema.md    # Template database schema
│
├── 04_plans_docs/                      # Tài liệu kế hoạch triển khai
│   ├── _template_folder_readme.md      # Template README cho folder
│   ├── _template_phase.md              # Template phase triển khai
│   └── _template_sub_phase.md          # Template sub-phase chi tiết
│
└── 05_testing_docs/                    # Tài liệu kiểm thử
    ├── _template_folder_readme.md      # Template README cho folder
    ├── _template_test_strategy.md      # Template chiến lược test
    └── _template_test_guide.md         # Template hướng dẫn viết test
```

---

## 5 Pillars của Tài liệu Phần mềm

| Pillar | Mục đích | Đối tượng đọc |
|--------|----------|---------------|
| **Business Docs** | Mô tả WHAT - Nghiệp vụ, quy trình, vai trò | BA, PO, Stakeholders, Developers |
| **Features Docs** | Mô tả HOW IT LOOKS - UI/UX, màn hình, flows | Designer, Frontend Dev, QA |
| **Technical Docs** | Mô tả HOW IT WORKS - Kiến trúc, database, API | Developers, DevOps |
| **Plans Docs** | Mô tả HOW TO BUILD - Kế hoạch triển khai từng bước | Developers, PM |
| **Testing Docs** | Mô tả HOW TO VERIFY - Chiến lược & hướng dẫn test | QA, Developers |

---

## Nguyên tắc cốt lõi

### 1. DRY (Don't Repeat Yourself)
- Tách nội dung dùng chung thành file riêng
- Tham chiếu bằng link thay vì copy nội dung
- Mỗi thông tin chỉ xuất hiện ở 1 nơi duy nhất

### 2. Single Source of Truth
- Mỗi loại tài liệu có vị trí riêng, không chồng chéo
- Cập nhật tại 1 nơi, reflect everywhere

### 3. AI-Readable
- Cấu trúc nhất quán giúp AI parse dễ dàng
- README.md ở mỗi folder giải thích cấu trúc
- Sử dụng tables, lists, code blocks rõ ràng

### 4. Navigable
- Luôn có navigation/links giữa các tài liệu liên quan
- Breadcrumb-style organization
- Cross-references between pillars

### 5. Actionable
- Tài liệu Plans phải có checklist để track tiến độ
- Tài liệu Features phải có đủ thông tin để implement
- Tài liệu Technical phải có đủ chi tiết để setup

---

## Hướng dẫn sử dụng

### Cho AI
1. Đọc file `00_ai_instructions.md` đầu tiên
2. Copy templates cần thiết vào dự án mới
3. Điền thông tin theo hướng dẫn trong template
4. Tuân thủ quy tắc DRY và cross-references

### Cho Developer/BA
1. Fork cấu trúc thư mục này vào dự án mới
2. Tùy chỉnh templates theo ngữ cảnh dự án
3. Xóa các sections không cần thiết
4. Thêm sections đặc thù của dự án

---

## Ngôn ngữ và Format

- **Format**: Markdown (.md)
- **Diagrams**: Mermaid hoặc Text-based (ASCII art)
- **Ngôn ngữ**: Tùy theo dự án, các template này có thể dịch sang bất kỳ ngôn ngữ nào

---

## Tác giả và Nguồn gốc

Bộ templates này được trích xuất và tổng quát hóa từ các dự án phần mềm thực tế, đúc kết kinh nghiệm 20 năm viết tài liệu.

