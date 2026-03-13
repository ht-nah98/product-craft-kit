# Business Case — Safety PPE Checker

> Tài liệu này dành cho ban lãnh đạo và decision makers.
> Phân tích vấn đề, chi phí hiện tại, giá trị đề xuất, và lý do đầu tư.

---

## 1. Tóm tắt điều hành (Executive Summary)

Tai nạn điện do thiếu PPE là một trong những nguyên nhân hàng đầu gây thương tích nghiêm trọng và tử vong trong ngành điện. Chi phí một vụ tai nạn nghiêm trọng (điều trị y tế + ngừng hoạt động + phạt vi phạm an toàn lao động) có thể lên tới hàng trăm triệu đồng.

**Safety PPE Checker** sử dụng AI để tự động phát hiện thiếu sót PPE TRƯỚC khi nhân viên tiếp cận vùng nguy hiểm — biến kiểm tra an toàn từ một quy trình thủ công, phụ thuộc con người, thành một hệ thống tự động, có bằng chứng, có thể scale.

---

## 2. Phân tích vấn đề

### Chi phí của việc không tuân thủ PPE

### Hạn chế của quy trình kiểm tra thủ công hiện tại

```
Quy trình hiện tại:
┌─────────────────────────────────────────────────────┐
│  Nhân viên đến    →   Giám sát kiểm tra   →   Vào làm  │
│  điểm làm việc        (2-5 phút/người)              │
└─────────────────────────────────────────────────────┘

Vấn đề:
  ✗ Giám sát viên phải có mặt tại chỗ → không scale
  ✗ Không có bằng chứng hình ảnh → không thể audit
  ✗ Human error: bỏ sót item khi bận hoặc mệt
  ✗ Không phát hiện được vi phạm trong lúc làm việc
  ✗ Không có dữ liệu phân tích xu hướng vi phạm
```

### Quy mô vấn đề (ước tính)

| Chỉ số | Ước tính |
|--------|----------|
| Số nhân viên kỹ thuật điện cần kiểm tra/ngày | 50–200 người |
| Thời gian kiểm tra thủ công/người | 2–5 phút |
| Tổng thời gian kiểm tra/ngày | 100–1000 phút (1.7–16.7 giờ) |
| Tỷ lệ vi phạm PPE (industry average) | 15–30% |
| Vi phạm không bị phát hiện do human error | Ước tính 5–20% |

---

## 3. Giải pháp đề xuất

### Quy trình mới với Safety PPE Checker

```
Quy trình mới:
┌──────────────────────────────────────────────────────────┐
│  Nhân viên chụp ảnh   →   AI phân tích   →   PASS → Vào  │
│  tại kiosk/mobile         (< 3 giây)         FAIL → Sửa  │
│                                                    rồi thử│
└──────────────────────────────────────────────────────────┘

Lợi ích:
  ✓ Không cần giám sát viên có mặt trực tiếp → scale tốt
  ✓ Mỗi kiểm tra có ảnh + kết quả lưu lại → full audit trail
  ✓ AI không mệt, không bỏ sót → consistent
  ✓ Phát hiện ngay tại điểm vào → ngăn chặn trước khi nguy hiểm
  ✓ Data → phân tích xu hướng, nhóm vi phạm nhiều nhất
```

---

## 4. Phân tích ROI (Return on Investment)

---

## 5. Rủi ro và biện pháp giảm thiểu

| Rủi ro | Xác suất | Biện pháp |
|--------|----------|-----------|
| AI accuracy < kỳ vọng trên dữ liệu thực | Trung bình | Bắt đầu với demo để validate; fine-tune trên dữ liệu thực |
| Nhân viên từ chối chụp ảnh (privacy) | Thấp-Trung | Chính sách rõ ràng; xử lý ảnh on-premise; không lưu trường kỳ |
| Chi phí vượt ngân sách | Thấp | Phase-based approach; Phase 1 chi phí thấp trước khi cam kết Phase 2 |
| Hệ thống bị bypass (nhân viên tìm cách qua mặt) | Trung bình | Kết hợp với process (cần PASS mới mở cửa/cấp permit) |

---

## 6. Lộ trình đề xuất

```
Phase 1 — Demo (Hiện tại, 3 tuần)
  └─ Mục tiêu: Chứng minh công nghệ hoạt động
  └─ Output: Web demo chạy được, accuracy ~85%+
  └─ Quyết định: Go/No-go cho Phase 2

Phase 2 — Production MVP (3–6 tháng)
  └─ Mục tiêu: Hệ thống thực trong 1 địa điểm thí điểm
  └─ Cần: Thu thập 500–2000 ảnh thực + gán nhãn + fine-tune model
  └─ Output: Hệ thống chạy thực tế với accuracy ≥ 90%

Phase 3 — Scale (6–18 tháng)
  └─ Mục tiêu: Mở rộng ra tất cả địa điểm
  └─ Thêm: Real-time camera, permit-to-work integration, dashboard
```

---

## 7. Yêu cầu để tiến hành Phase 2

---

## 8. Kết luận

Safety PPE Checker là một đầu tư có ROI rõ ràng: **ngăn chặn 1 tai nạn điện nghiêm trọng đã đủ để hoàn vốn toàn bộ dự án**. Ngoài ra, hệ thống xây dựng nền tảng dữ liệu cho các ứng dụng AI an toàn lao động khác trong tương lai.

**Đề xuất hành động**: Xem demo → Phê duyệt thu thập dữ liệu thực → Bắt đầu Phase 2.
