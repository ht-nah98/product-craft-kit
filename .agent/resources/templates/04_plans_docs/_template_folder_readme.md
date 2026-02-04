# Template: README cho Folder Kế hoạch Triển khai

> Đây là file hướng dẫn cho AI và team khi làm việc với thư mục này.

---

## Tổng quan

Đây là thư mục chứa tài liệu kế hoạch triển khai của dự án.

---

## Cấu trúc thư mục

```
4_plans_docs/
├── README.md                       # File hướng dẫn này
│
├── [module_01]/                    # Module 1
│   ├── phase-1-[name].md           # Phase 1
│   ├── phase-2-[name]/             # Phase 2 (có sub-phases)
│   │   ├── README.md               # Tổng quan Phase
│   │   ├── sub-1-[name].md         # Sub-phase 1
│   │   └── sub-2-[name].md         # Sub-phase 2
│   └── phase-3-[name].md           # Phase 3
│
├── [module_02]/                    # Module 2
│   └── ...
│
└── testing/                        # Testing Plans
    ├── testing-plan.md             
    └── phase-X-[name].md
```

---

## Tổng quan tiến độ [Module 1]

| Phase | Mô tả | Trạng thái |
|-------|-------|------------|
| Phase 1 | [Mô tả] | ⬜ Chưa bắt đầu |
| Phase 2 | [Mô tả] | ⬜ Chưa bắt đầu |
| Phase 3 | [Mô tả] | ⬜ Chưa bắt đầu |

**Trạng thái:**
- ✅ Hoàn thành
- 🔄 Đang thực hiện  
- ⬜ Chưa bắt đầu

---

## Tổng quan tiến độ [Module 2]

| Phase | Mô tả | Trạng thái |
|-------|-------|------------|
| Phase 1 | [Mô tả] | ⬜ Chưa bắt đầu |

---

## Quy tắc

### Quy tắc tài liệu
1. Mỗi khi có file kế hoạch mới, hãy cập nhật cấu trúc thư mục trong README.md này.
2. Sử dụng định dạng markdown cho tất cả tài liệu.

### Quy tắc viết tài liệu triển khai

1. **Tính năng lớn/phức tạp**: Tạo thư mục, chia thành nhiều files sub-phase
2. **Triển khai theo chiều DỌC**: 
   - ✅ Triển khai từng màn hình, từng tính năng hoàn chỉnh
   - ❌ KHÔNG triển khai theo chiều ngang (viết hết backend → viết hết frontend)
3. **Luôn link đến tài liệu liên quan**: nghiệp vụ, tính năng, kỹ thuật
4. **Cấu trúc tài liệu**:
   - Chia thành phases
   - Chia thành sub-phases nếu cần
   - Checklist tasks trong mỗi bước
5. **Không viết code chi tiết**: Chỉ ghi chú ngắn gọn
6. **Cập nhật trạng thái**: Sau mỗi task/phase hoàn thành

---

## Hướng dẫn viết tài liệu

1. Bắt đầu: Đọc kỹ tài liệu tính năng
2. Đọc kỹ tài liệu kỹ thuật liên quan
3. Đọc kỹ tài liệu nghiệp vụ liên quan
4. Nghiên cứu source code và test (nếu có)
5. Viết tài liệu dựa trên quy tắc

---

## Tài liệu liên quan

- [Tài liệu nghiệp vụ](../1_business_docs/)
- [Tài liệu tính năng](../2_features_docs/)
- [Tài liệu kỹ thuật](../3_technical_docs/)
- [Tài liệu testing](../5_testing_docs/)

