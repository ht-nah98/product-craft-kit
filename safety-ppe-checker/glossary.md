# Glossary — Safety PPE Checker

Các thuật ngữ chuyên ngành dùng trong dự án này.

---

## PPE (Personal Protective Equipment)
Thiết bị bảo hộ cá nhân — trang thiết bị mà nhân viên phải mặc để bảo vệ bản thân khỏi các nguy hiểm tại nơi làm việc.

## Hard Hat / Helmet (Mũ bảo hộ)
Mũ cứng bảo vệ đầu khỏi vật rơi và va chạm. Với công việc điện, phải là loại non-conductive (Class E, chịu 20,000V).

## Safety Vest / High-Vis Vest (Áo phản quang)
Áo vest có dải phản quang giúp nhân viên dễ nhìn thấy.

## Protective Gloves (Găng tay bảo hộ)
Trong context điện: găng tay cách điện cao su. Trong demo: phát hiện sự có mặt, không phân cấp voltage rating.

## Safety Goggles / Safety Glasses (Kính bảo hộ)
Kính bảo vệ mắt. Chuẩn ANSI Z87.1.

## Safety Boots (Giày bảo hộ)
Giày mũi thép, đế cách điện. Với công việc điện: loại dielectric.

## Arc Flash (Hồ quang điện)
Phóng điện đột ngột tạo nhiệt độ cực cao, gây bỏng nặng. Nguy hiểm chính cần PPE đặc biệt trong công việc điện.

## Arc Flash Suit (Quần áo chống hồ quang)
Bộ quần áo chống cháy, đánh giá theo cal/cm². Chưa phát hiện trong Phase 1 (thiếu dữ liệu training).

## NFPA 70E
Tiêu chuẩn Mỹ về an toàn điện tại nơi làm việc. Định nghĩa 4 PPE Category theo mức arc energy.

## PASS / FAIL
- **PASS**: Tất cả PPE bắt buộc được phát hiện → nhân viên đủ điều kiện vào vùng làm việc
- **FAIL**: Thiếu ít nhất 1 PPE bắt buộc → phải trang bị đầy đủ trước khi vào

## YOLOv8m
Kiến trúc object detection của Ultralytics. Phiên bản `m` (medium) — cân bằng tốt giữa tốc độ và độ chính xác cho demo.

## mAP@0.5 (Mean Average Precision)
Metric đánh giá độ chính xác object detection khi IoU threshold = 0.5. Cao hơn = tốt hơn (max 100%).

## Confidence Score
Điểm tin cậy của model (0–1). Ví dụ: 0.87 = model 87% chắc đây là helmet.

## Bounding Box
Hình chữ nhật vẽ quanh vật thể được phát hiện trong ảnh.

## Annotated Image (Ảnh đã chú thích)
Ảnh gốc với bounding boxes, labels và confidence scores cho từng PPE item.

## Inference
Quá trình model AI xử lý ảnh đầu vào và trả kết quả phát hiện.

## Permit-to-Work (PTW)
Hệ thống cấp phép làm việc nguy hiểm. Phase 2 sẽ tích hợp PPE check vào PTW workflow.

## Domain Shift
Hiện tượng model được training trên dữ liệu một môi trường (construction) nhưng deploy ở môi trường khác (electrical substation), dẫn đến giảm accuracy. Giải quyết trong Phase 2 bằng fine-tuning trên dữ liệu thực.

## Fine-tuning
Quá trình tiếp tục training model pre-trained trên dữ liệu mới (domain-specific) để tăng accuracy trong môi trường cụ thể.
