# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Ở temperature 0.0, câu trả lời khá chắc và ít "bay", thường đi thẳng vào một ý quen thuộc. Khi tăng dần lên 0.5, 1.0 rồi 1.5 thì câu trả lời nghe thú vị hơn, có nhiều cách diễn đạt hơn, nhưng mức cao quá thì bắt đầu có cảm giác hơi lan man và khó kiểm soát hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Với chatbot hỗ trợ khách hàng, tôi sẽ chọn khoảng 0.3. Lý do là phần này cần trả lời ổn định và đúng thông tin hơn là sáng tạo; chỉ cần đủ tự nhiên để người dùng không cảm thấy quá máy móc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Tổng số token mỗi ngày là 10.000 x 3 x 350 = 10.500.000 token, tức khoảng 10.500 lần 1K token. Tính theo giá trong bài thì GPT-4o khoảng 10.500 x 0.010 = 105 USD/ngày, còn GPT-4o-mini khoảng 10.500 x 0.0006 = 6.3 USD/ngày. Như vậy GPT-4o đắt hơn khoảng 105 / 6.3 = 16.7 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> Tôi nghĩ GPT-4o đáng dùng khi câu hỏi khó, cần suy luận tốt hoặc ảnh hưởng trực tiếp tới quyết định của người dùng, ví dụ phân tích tài liệu dài hay hỗ trợ một ca khách hàng quan trọng. Còn GPT-4o-mini hợp hơn cho những việc lặp lại nhiều và không quá rủi ro, như FAQ, tóm tắt ngắn, phân loại nội dung hoặc tạo câu trả lời nháp.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Theo tôi, streaming hữu ích nhất khi câu trả lời dài, vì người dùng có thể thấy nội dung xuất hiện ngay thay vì phải nhìn màn hình chờ. Ví dụ như chatbot tư vấn, giải thích code hoặc viết một đoạn nội dung dài thì streaming làm trải nghiệm dễ chịu hơn nhiều. Ngược lại, non-streaming vẫn phù hợp khi câu trả lời ngắn, hoặc khi hệ thống cần nhận đủ kết quả trước để kiểm tra format, lưu log, kiểm duyệt hoặc trả về JSON cho đúng.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
