# Lessons Learned — Safety PPE Checker

> Ghi nhận các bài học quan trọng trong quá trình nghiên cứu và xây dựng.
> Cập nhật liên tục khi có thêm insights mới.

---

## L01: Đừng bắt đầu với Arc Flash Suit detection

**Bài học**: Nhiều người sẽ nghĩ arc flash suit là PPE quan trọng nhất trong electrical work, nên cần detect đầu tiên. Thực tế ngược lại.

**Tại sao KHÔNG nên:**
- Không có dataset công khai nào đủ cho arc suit
- Fabric metallic của arc suit gây specular reflection khó detect
- Suit che toàn thân làm khó phân biệt các parts khác
- Không thể verify arc rating (4 cal vs 40 cal) bằng camera

**Làm đúng**: Bắt đầu với 5 PPE dễ detect nhất (Helmet, Vest, Gloves, Goggles, Boots) → chứng minh concept → thu thập dữ liệu thực → thêm arc suit ở Phase sau.

---

## L02: Domain shift là vấn đề THỰC SỰ, không phải lý thuyết

**Bài học**: Model train trên construction site (crane operators, scaffold workers) sẽ có accuracy đáng kể thấp hơn khi deploy ở electrical substation.

**Biểu hiện thực tế:**
- Background construction (bê tông, cẩu trục) khác hoàn toàn background electrical (tủ điện xám, cable tray)
- Màu uniform: construction thường orange/blue; electrical có thể khác
- Camera angle ở kiosk entry khác góc camera substation cố định

**Cách xử lý:**
- Phase 1 (demo): chấp nhận accuracy 85% với ảnh diverse
- Phase 2: bắt buộc fine-tune trên ít nhất 500 ảnh môi trường thực
- Luôn test model trên ảnh từ chính environment sẽ deploy

---

## L03: Không nên dùng confidence score để PASS/FAIL trực tiếp

**Bài học**: Với threshold cứng 0.5, một item có confidence 0.51 sẽ PASS nhưng 0.49 sẽ FAIL. Ranh giới này không có ý nghĩa thực tế.

**Cách xử lý tốt hơn:**
- Confidence ≥ 0.70: Detected ✓ (strong)
- Confidence 0.50–0.69: Detected nhưng cảnh báo ⚠️ (verify manually)
- Confidence < 0.50: Not detected ✗
- Compliance: PASS chỉ khi tất cả items ≥ 0.50, nhưng cảnh báo nếu có item 0.50–0.69

**Đã áp dụng**: US-WEB-005 — low confidence warning (màu vàng khi < 70%).

---

## L04: Single-photo approach có ưu điểm không ngờ

**Bài học**: Ban đầu nghĩ real-time video monitoring là gold standard. Nhưng photo-based pre-shift check có ưu điểm riêng:

- **Bằng chứng rõ ràng**: 1 ảnh = 1 record kiểm tra = dễ lưu, dễ audit
- **Không cần CCTV infrastructure**: Chụp bằng điện thoại hoặc kiosk tablet
- **Worker accountability**: Worker chủ động chụp → biết mình đang được check
- **Xử lý nhẹ hơn**: Không cần streaming pipeline
- **Privacy**: Không record liên tục, chỉ chụp tại điểm kiểm tra

**Recommendation**: Photo-based pre-shift check là đúng approach cho Phase 1 và Phase 2. Real-time monitoring chỉ cần ở Phase 3 cho high-risk zones.

---

## L05: Gloves và Goggles sẽ là nguồn gốc của hầu hết false positives/negatives

**Bài học từ literature review:**
- Gloves: nhỏ, màu sắc đa dạng (đen, vàng, xanh), overlap với màu da, thường bị occlude bởi body
- Safety Goggles: nhỏ, thường bị che bởi mũ bảo hộ
- Literature: accuracy của 2 class này thường thấp hơn Helmet 10–15%

**Hậu quả thực tế:**
- Nếu demo với Gloves/Goggles bị missed → stakeholder lo lắng
- Nếu Gloves được detect nhưng thực ra là găng tay thường → false positive

**Cách xử lý:**
- Trong demo: ưu tiên ảnh mẫu có gloves/goggles rõ ràng, màu sáng, không occluded
- Trong UI: hiển thị confidence score → giải thích được khi accuracy thấp
- Phase 2: pose estimation pipeline giải quyết vấn đề này bằng cách crop hand zone

---

## L06: Model weights không được commit vào git

**Bài học**: YOLOv8m weights file (.pt) có kích thước 25–50MB. Nếu commit vào git → repo nặng, clone chậm, GitHub có thể từ chối.

**Giải pháp:**
- Thêm `*.pt` và `models/` vào `.gitignore`
- Tạo script `scripts/download_model.py` để download weights khi setup lần đầu
- Hoặc dùng Git LFS nếu cần version control weights
- Document rõ cách download trong README

---

## L07: CORS phải được configure đúng trước khi demo

**Bài học từ kinh nghiệm**: Ngày demo, frontend call backend nhưng bị CORS block. Demo fail tại chỗ.

**Cách tránh:**
- Configure CORS trong FastAPI ngay từ đầu
- Test cross-origin request trong Docker Compose environment (không chỉ local dev)
- Tạo test case TC-API riêng cho CORS (TC-API-011)

```python
# main.py — CORS config đúng
app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000", "http://frontend:3000"],
    allow_methods=["GET", "POST"],
    allow_headers=["*"],
)
```

---

## L08: Cần ít nhất 4 ảnh demo với scenarios khác nhau

**Bài học**: Demo với 1 ảnh PASS và 1 ảnh FAIL là không đủ. Stakeholder sẽ hỏi "Thế nếu thiếu nhiều cái thì sao?" hoặc "Góc chụp khác thì sao?"

**Bộ demo images cần có:**
1. PASS — đủ tất cả PPE, ánh sáng tốt
2. FAIL — thiếu 1 item (Helmet hoặc Gloves)
3. FAIL — thiếu nhiều items (3+ missing)
4. Edge case — ánh sáng khó / góc chụp khác
5. (Optional) FAIL — nhân viên thường phục, không mặc PPE gì

---

## L09: Stakeholder hỏi về privacy — chuẩn bị sẵn câu trả lời

**Bài học từ kinh nghiệm tương tự**: Gần như 100% demo sẽ có câu hỏi "Ảnh nhân viên có bị lưu không?"

**Câu trả lời chuẩn bị sẵn:**
- Demo hiện tại: hoàn toàn stateless, không lưu bất kỳ ảnh nào
- Production: có thể lưu ảnh phục vụ audit trail, nhưng:
  - Chỉ lưu ảnh tại điểm kiểm tra (không phải liên tục)
  - Có chính sách retention rõ ràng
  - On-premise deployment → dữ liệu không ra ngoài
  - Nhân viên được thông báo và đồng ý

---

## Template ghi nhận lessons mới

```markdown
## L[N]: [Tên ngắn gọn]

**Bài học**: [Phát hiện quan trọng]

**Tại sao quan trọng**: [Hậu quả nếu không biết]

**Cách xử lý**: [Action đã/cần thực hiện]

**Ngày ghi nhận**: [Date]
```
