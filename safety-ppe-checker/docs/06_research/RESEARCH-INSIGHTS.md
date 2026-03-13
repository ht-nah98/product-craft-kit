# Research Insights — PPE Detection with Computer Vision

> Tổng hợp nghiên cứu thị trường và công nghệ trước khi bắt đầu xây dựng.
> Nguồn: Khảo sát thị trường 2025–2026, academic papers, vendor analysis.

---

## 1. Thị trường hiện tại

### Các giải pháp thương mại chính

| Vendor | Điểm mạnh | Điểm yếu | Giá ước tính |
|--------|-----------|----------|-------------|
| **Intenseye** | Enterprise-scale, contextual reasoning, multi-hazard | Rất đắt, cần CCTV sẵn có | $60,000–$200,000+/năm |
| **Protex AI** | Predictive insights, video evidence, SME-friendly | Không có arc suit module | $15,000–$50,000/năm |
| **viAct** | 50+ EHS modules, tích hợp ePTW, Asia market | Ít tài liệu tiếng Anh | Trung bình |
| **Vehant (PPEye)** | Có arc suit detection module | Ít tài liệu công khai | N/A |
| **Voxel AI** | Privacy-first (on-site), tiết kiệm hơn Intenseye | Mới, ít track record | 30–50% < Intenseye |

### Insight quan trọng
- **Không có vendor nào** tập trung 100% vào electrical worker PPE — tất cả đều general construction/industrial
- **Vehant là vendor duy nhất** có arc suit detection module được ghi rõ trong sản phẩm
- **Hầu hết giải pháp** cần CCTV infrastructure sẵn có — không phải photo-based như hướng tiếp cận của chúng ta

---

## 2. State of the Art — Kỹ thuật

### Các kiến trúc model phổ biến nhất (2025)

| Model | mAP@0.5 | Inference (GPU) | Best for |
|-------|---------|-----------------|----------|
| YOLOv8m | ~88–91% | 30–80ms | Demo, balanced |
| YOLOv8l/x | ~91–93% | 50–150ms | Production |
| YOLO11x (PPE-EYE) | **96.9%** | 7.3ms | SOTA benchmark |
| YOLOv9-e | ~70.9% | Varies | Harder datasets |
| InternImage-L + ViTPose + YOLOv7 | ~93%+ | Slow | Research pipeline |

**Quyết định**: Chọn **YOLOv8m** cho Phase 1 vì:
- Pre-trained Construction-PPE weights có sẵn
- Inference ≤ 3s trên CPU — phù hợp demo
- Đủ tốt cho demo (85–90% real-world accuracy)
- Dễ fine-tune lên YOLOv8l/x trong Phase 2

### Pipeline tốt nhất hiện tại (2-stage approach)
```
Person detection (YOLOv8)
    ↓
Pose estimation (ViTPose — 17 body keypoints)
    ↓
Crop body zones: head / torso / hands / feet
    ↓
Per-zone PPE classifier
```

**Tại sao chúng ta KHÔNG dùng approach này trong Phase 1:**
- Phức tạp hơn nhiều, cần thêm ViTPose model
- Không có sẵn pre-trained weights cho electrical PPE
- Demo không cần độ chính xác production
- Phase 2 có thể upgrade nếu cần

---

## 3. Các dataset PPE phổ biến

| Dataset | Số ảnh | Classes | Phù hợp cho |
|---------|--------|---------|-------------|
| **Ultralytics Construction-PPE** | Large | Helmet, Vest, Gloves, Boots, Goggles | Demo Phase 1 ✅ |
| **SH17** | 8,099 | 17 classes (comprehensive) | Fine-tuning Phase 2 |
| **CHV** | 1,330 | Helmet + Vest (colors) | Helmet/Vest focused |
| **SHEL5K** | 5,000 | Helmet-focused | Helmet focused |
| **PT PLN (Indonesia)** | 589 | 7 classes, electrical workers | Most relevant, too small |

### Khoảng trống dữ liệu nghiêm trọng
- **Chỉ có 1 paper** (PT PLN, 2025) dùng dữ liệu nhân viên điện thực tế
- Dataset đó chỉ có 589 ảnh — không đủ để fine-tune production model
- **Phần lớn dữ liệu công khai là construction site** — có domain shift khi áp dụng cho substation/electrical environments
- **Không có dataset nào** bao gồm arc flash suit với đủ diversity

---

## 4. Limitations được xác nhận từ nghiên cứu

### Limitations về mặt kỹ thuật

| Limitation | Mức độ | Cách xử lý |
|------------|--------|------------|
| **Arc flash suit rating** không thể phát hiện bằng CV | Permanent | Chỉ detect sự có mặt, không phân biệt rating |
| **Glove voltage class** không thể phân biệt | Permanent | Chỉ detect có/không có găng tay |
| **Harness strap trên arc suit** rất khó detect | Hard | Phase 3: pose estimation pipeline |
| **Domain shift**: model train trên construction → accuracy giảm trên electrical | Important | Fine-tune với dữ liệu thực (Phase 2) |
| **Gloves và Goggles** là 2 class khó nhất (nhỏ, dễ bị che khuất) | Medium | Giải quyết với pose estimation |
| **False positives** với items nhìn giống PPE (túi xách giống helmet...) | Medium | Tăng confidence threshold |

### Khoảng cách giữa benchmark và thực tế
```
Published benchmark accuracy:  91–96% mAP@0.5
Real-world deployment accuracy: 85–93%
Our demo target:                ≥ 85%

Nguyên nhân gap:
  - Domain shift (training vs deployment environment)
  - Lighting variation
  - Occlusion
  - Camera angle/distance variation
  - Image quality (phone camera vs professional)
```

---

## 5. Insight về tích hợp hệ thống (Phase 2+)

### Permit-to-Work integration pattern (best practice từ viAct)
```
1. Worker chụp ảnh tại kiosk
      ↓
2. AI verify PPE (< 3 giây)
      ↓
3. PASS → Permit activated → Door/gate opened
   FAIL → Cảnh báo → Worker sửa → Thử lại
      ↓
4. Event log: timestamp + worker ID + image + result
      ↓
5. Supervisor nhận alert ngay nếu FAIL
```

### Wearable + CV combination (industry trend)
- **Spot-r Clip** (Triax) + Camera = best practice
- Camera phát hiện PPE compliance
- Wearable phát hiện falls, location, distress signal
- Hai hệ thống bổ sung nhau

---

## 6. Competitive Positioning của chúng ta

| Dimension | Commercial Vendors | Our Approach |
|-----------|-------------------|--------------|
| Scope | General industrial | Electrical-specific |
| Input | Continuous CCTV | Photo-based (pre-shift check) |
| Pricing | $15K–$200K/year | Internal build |
| Data | Generic dataset | Company-specific (Phase 2) |
| Customization | Limited | Full control |
| Electrical expertise | Low | High (domain-specific training data) |

**Advantage**: Chúng ta sẽ là hệ thống duy nhất được fine-tune trên dữ liệu thực tế của công ty điện này → accuracy cao hơn bất kỳ generic vendor nào trong môi trường cụ thể.
