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
> *Khi temperature càng thấp (0.0 và 0.5) thì câu trả lời càng ngắn gọn, súc tích. Temperature 1.0 thì nó đưa nhiều thông tin hơn. Cuối cùng là temperature 1.5 thì trả lời bắt đầu lan man, sau 1-2 câu nói về Việt Nam thì bắt đầu trả kết quả ra những vấn đề khác. *

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *Tôi sẽ đặt temperature bằng 1.0 cho chatbot hỗ trợ khách hàng. Vì nó đưa ra thông tin vừa ngắn gọn vừa đủ ý với request của khách hàng, không lan man qua những vấn đề khác. *

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> *Tổng số token/ngày: 10.000x3x350=10.500.000. Hiện tại GPT-4o giá 2,5$/1 triệu input token; GPT-4o-mini giá 0,15$/1 triệu input token. Ước tính GPT-4o đắt hơn GPT-4o-mini: 2,5/0,15 ~= 16,67 lần  *

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> *GPT-4o phù hợp với trường hợp các ứng dụng cần tính suy luận sâu, độ chính xác cao hoặc xử lý multi models. GPT-4o-mini phù hợp với các tác vụ như chatbot trả lời các câu hỏi cơ bản, nhanh thường thấy ở các ứng dụng chatbot bán hàng, ... *

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> *Streaming quan trọng nhất trong trường hợp user chờ phản hồi, ví dụ như các chatbot hoặc các hệ thống tạo ảnh, video để user có thể biết được rằng AI đang trong tiến trình xử lý. Ngược lại non-streaming phù hợp cho những trường hợp xử lý xong tác vụ trước khi đưa ra kết quả cuối cùng cho user. *


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
