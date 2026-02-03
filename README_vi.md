# Product Craft Kit

> 🌐 **Ngôn ngữ / Language**: [Tiếng Việt](README_vi.md) | [English](README.md)

> 🚀 Hệ thống phương pháp luận và tài liệu toàn diện để xây dựng sản phẩm - từ Khám phá đến Mở rộng

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Language](https://img.shields.io/badge/Ngôn%20ngữ-EN%20%7C%20VI-blue.svg)](README.md)

---

## Đây là gì?

Một hệ thống hoàn chỉnh cho:
- **📝 Tài liệu Sản phẩm** - Templates có cấu trúc cho PRD, Epic, User Story, v.v.
- **🚀 Xây dựng Sản phẩm** - Phương pháp 5 giai đoạn (Khám phá → Định nghĩa → Phát triển → Triển khai → Mở rộng)
- **🤖 Phát triển AI Agent** - Patterns và kiến trúc để xây dựng AI agents

Được thiết kế để hoạt động liền mạch với AI assistants (như Gemini/Claude) giúp Product Owners và builders làm việc hiệu quả.

---

## Bắt đầu nhanh

### Cho AI Assistant (Gemini/Claude)

1. Mở workspace này
2. AI sẽ tự động đọc `GEMINI.md` để lấy hướng dẫn
3. Sử dụng slash commands:
   - `/new-project` - Tạo project mới
   - `/discovery` - Bắt đầu giai đoạn nghiên cứu
   - `/define-problem` - Định nghĩa vấn đề
   - `/shape-solution` - Thiết kế giải pháp
   - `/build-agent` - Xây dựng AI Agent

### Cho Người dùng

1. Duyệt `_master/skills/` để hiểu phương pháp luận
2. Sử dụng templates trong `_master/templates/`
3. Tạo projects trong folder `projects/`

---

## Cấu trúc

```
.
├── GEMINI.md                   # Hướng dẫn cho AI (đọc đầu tiên)
├── _master/
│   ├── skills/
│   │   ├── SKILL.md            # Router (điểm vào chính)
│   │   ├── 1_documentation/    # Skills viết tài liệu PO
│   │   ├── 2_product_building/ # Skills vòng đời sản phẩm
│   │   └── 3_ai_agent/         # Skills xây dựng AI agent
│   ├── templates/              # Templates tài liệu
│   └── knowledge/              # Tài liệu tham khảo phương pháp
├── projects/                   # Projects của bạn ở đây
│   └── _project-template/      # Template cho project mới
└── .agent/workflows/           # Định nghĩa slash commands
```

---

## Tổng quan Skills

### 📝 Documentation Skills (Viết tài liệu)
| Skill | Mục đích |
|-------|----------|
| Write Epic | Đặc tả tính năng lớn |
| Write User Story | Yêu cầu tính năng cá nhân |
| Write PRD | Tài liệu Yêu cầu Sản phẩm |
| Write AC | Tiêu chí Chấp nhận |
| Backlog Management | Ưu tiên và lập kế hoạch |

### 🚀 Product Building Skills (5 Giai đoạn)
| Giai đoạn | Skill | Đầu ra |
|-----------|-------|--------|
| 1. Khám phá | Nghiên cứu & Insights | Kết quả nghiên cứu |
| 2. Định nghĩa | Định nghĩa Vấn đề | Problem canvas |
| 3. Phát triển | Định hình Giải pháp | Giải pháp shaped |
| 4. Triển khai | Build & Ship | Launch checklist |
| 5. Mở rộng | Lặp lại | Kế hoạch iteration |

### 🤖 AI Agent Skills
| Skill | Mục đích |
|-------|----------|
| Agent Discovery | Xác nhận vấn đề, phân tích người dùng |
| Agent Architecture | Chọn pattern, thiết kế components |
| Agent Patterns | Tham khảo implementation |

---

## Workflows (Slash Commands)

| Lệnh | Mô tả |
|------|-------|
| `/new-project` | Tạo project mới từ template |
| `/write-prd` | Viết tài liệu PRD |
| `/write-user-story` | Viết User Story |
| `/discovery` | Bắt đầu giai đoạn Discovery |
| `/define-problem` | Giai đoạn Define Problem |
| `/shape-solution` | Giai đoạn Shape Solution |
| `/launch-checklist` | Checklist trước launch |
| `/build-agent` | Workflow xây dựng AI Agent |

---

## Tạo Project Mới

```bash
# Copy template
cp -r projects/_project-template projects/ten-project-cua-ban

# Chỉnh sửa project context
vim projects/ten-project-cua-ban/project-context.md
```

Hoặc sử dụng lệnh `/new-project` với AI assistant.

---

## Phương pháp luận bao gồm

### Product Building Methodology
Dựa trên:
- **Shape Up** (Basecamp) - Phát triển dựa trên "appetite"
- **Lean Startup** - Build-Measure-Learn
- **Jobs to be Done** - Tư duy tập trung vào vấn đề
- **Design Thinking** - Tiếp cận lấy con người làm trung tâm

### AI Agent Building Methodology
Nguyên tắc cốt lõi:
- Bắt đầu Hẹp, Mở rộng Sau
- Kiến trúc Hybrid (LLM + Deterministic)
- Hạ tầng Trước tiên
- Chuyên gia Domain > Generic
- Components Tái sử dụng
- Đo lường Mọi thứ

---

## License

MIT License - Xem file [LICENSE](LICENSE)

---

## Đóng góp

Hoan nghênh đóng góp! Vui lòng đọc tài liệu methodology trong `_master/knowledge/` trước.
