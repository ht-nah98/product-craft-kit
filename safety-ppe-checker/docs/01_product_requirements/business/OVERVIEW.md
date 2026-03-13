# Product Overview — Safety PPE Checker

> Tài liệu này dành cho stakeholders và người dùng không có nền tảng kỹ thuật.
> Giải thích sản phẩm bằng ngôn ngữ đơn giản, tập trung vào giá trị và cách hoạt động.

---

## Sản phẩm này là gì?

**Safety PPE Checker** là một hệ thống AI giúp tự động kiểm tra xem nhân viên kỹ thuật điện có đang mặc đầy đủ thiết bị bảo hộ cá nhân (PPE) trước khi bắt đầu công việc hay không.

Thay vì phải có giám sát viên đứng kiểm tra từng người — hệ thống chỉ cần **1 tấm ảnh chụp toàn thân** và cho ra kết quả trong vòng **3 giây**.

---

## Vấn đề đang giải quyết

Mỗi ngày, hàng chục đến hàng trăm nhân viên kỹ thuật điện bắt đầu ca làm việc. Trước khi tiếp cận thiết bị điện, họ **bắt buộc phải mặc đầy đủ PPE** theo quy định an toàn:

- Mũ bảo hộ (Helmet)
- Áo phản quang (Safety Vest)
- Găng tay cách điện (Gloves)
- Kính bảo hộ (Safety Goggles)
- Giày bảo hộ (Safety Boots)

**Vấn đề với cách làm hiện tại:**

| Vấn đề | Hậu quả |
|--------|---------|
| Kiểm tra thủ công bởi giám sát viên | Tốn 2–5 phút/người, phụ thuộc vào sự có mặt của giám sát |
| Không có bằng chứng hình ảnh | Khi xảy ra tai nạn, không thể chứng minh đã kiểm tra |
| Dễ bỏ sót trong lúc bận | Human error dẫn đến rủi ro thực sự |
| Không scale được | 1 giám sát viên không thể quản lý nhiều điểm kiểm tra cùng lúc |

---

## Cách hoạt động — 3 bước đơn giản

```
Bước 1                    Bước 2                   Bước 3
──────────                ──────────               ──────────
Nhân viên chụp ảnh  →    AI phân tích ảnh   →    Kết quả ngay lập tức
toàn thân trước         trong 1-3 giây            PASS hoặc FAIL
khi vào làm việc                                  + chi tiết thiếu gì
```

### Ví dụ kết quả PASS:
```
✅ COMPLIANT — All PPE requirements met

  ✓ Helmet         — 92%
  ✓ Safety Vest    — 88%
  ✓ Gloves         — 79%
  ✓ Safety Goggles — 83%
  ✓ Boots          — 91%
```

### Ví dụ kết quả FAIL:
```
❌ NON-COMPLIANT — 2 items missing

  ✓ Helmet         — 94%
  ✓ Safety Vest    — 87%
  ✗ Gloves         — NOT DETECTED
  ✗ Safety Goggles — NOT DETECTED
  ✓ Boots          — 88%

  → Nhân viên cần trang bị Gloves và Safety Goggles trước khi vào làm.
```

---

## Ai sẽ sử dụng hệ thống này?

| Người dùng | Họ làm gì với hệ thống |
|------------|------------------------|
| **Nhân viên kỹ thuật điện** | Chụp ảnh bản thân tại điểm kiểm tra trước ca làm việc |
| **Giám sát an toàn (Safety Supervisor)** | Xem kết quả kiểm tra theo thời gian thực, nhận cảnh báo khi có vi phạm |
| **Quản lý an toàn lao động (EHS Manager)** | Xem báo cáo tổng hợp tuân thủ, phân tích xu hướng vi phạm |

---

## Giai đoạn hiện tại: Demo / Proof of Concept

Hệ thống hiện tại là **bản demo** để chứng minh công nghệ hoạt động được. Mục tiêu:

1. ✅ Chứng minh AI có thể phát hiện PPE chính xác từ ảnh chụp
2. ✅ Thuyết phục ban lãnh đạo về tính khả thi
3. ⬜ Thu thập dữ liệu ảnh thực tế từ môi trường làm việc thực
4. ⬜ Triển khai hệ thống production đầy đủ

---

## Lợi ích kỳ vọng

| Lợi ích | Mô tả |
|---------|-------|
| **Giảm rủi ro tai nạn** | Phát hiện vi phạm PPE trước khi xảy ra sự cố |
| **Tiết kiệm thời gian** | Kiểm tra tự động < 5 giây thay vì 2–5 phút thủ công |
| **Bằng chứng kiểm tra** | Mỗi lần kiểm tra có ảnh và kết quả lưu lại để audit |
| **Scale dễ dàng** | 1 hệ thống quản lý nhiều điểm kiểm tra, nhiều ca làm việc |
| **Giảm phụ thuộc giám sát viên** | Hệ thống hoạt động 24/7, không cần người kiểm tra trực tiếp |

---

## Câu hỏi thường gặp

**H: AI có chính xác 100% không?**
Không có hệ thống AI nào đạt 100%. Demo hiện tại đạt khoảng 85–90% độ chính xác trên ảnh thông thường. Sau khi có dữ liệu thực từ môi trường của công ty, độ chính xác có thể tăng lên 90–95%.

**H: Nếu AI nhận diện sai thì sao?**
Hệ thống hiển thị confidence score cho từng item. Khi confidence thấp (< 70%), có cảnh báo để giám sát viên kiểm tra lại thủ công.

**H: Có thể phân biệt loại găng tay (voltage class) không?**
Hiện tại không — AI chỉ phát hiện sự có mặt của găng tay. Phân loại chất lượng PPE là mục tiêu Phase 3 sau khi có đủ dữ liệu training chuyên biệt.

**H: Dữ liệu ảnh của nhân viên có được lưu không?**
Trong bản demo hiện tại: không lưu gì cả — xử lý và xóa ngay. Trong production: sẽ có chính sách lưu trữ rõ ràng theo quy định bảo mật của công ty.

**H: Hệ thống cần internet không?**
Demo hiện tại chạy hoàn toàn offline. Production có thể chạy on-premise (máy chủ nội bộ) để đảm bảo bảo mật dữ liệu.
