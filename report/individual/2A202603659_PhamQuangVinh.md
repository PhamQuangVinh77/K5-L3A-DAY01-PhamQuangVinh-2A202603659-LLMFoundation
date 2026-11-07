# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV: 2A202603659**
- **Họ và tên: Phạm Quang Vinh**
- **SEED** (in ở ô đầu notebook):

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | ☑ |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | ☑ |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | ☐ |

## 2. Kết quả chính



## 3. Dự đoán và thực tế



## 4. Phân tích 50 case khó



## 5. Thử thách cá nhân



## 6. Phương án cho sản phẩm thật

- Chọn phương án: Cascade Classifier (Mô hình kết hợp đa tầng) — Dùng mô hình truyền thống nhẹ (BoW/ML) làm tuyến đầu xử lý phần lớn tin nhắn, chỉ chuyển các tin nhắn khó/mập mờ sang LLM ở tuyến sau.
- Dẫn số liệu:
+ Tải hệ thống: 10 triệu SMS/ngày (~116 tin/giây).
+ SLA: p95 < 50 ms.
+ Mô hình truyền thống đạt độ trễ chỉ vài ms (đáp ứng tốt SLA), trong khi gọi LLM đơn lẻ mất 200ms (vi phạm nghiêm trọng SLA).
- Chấp nhận đánh đổi:
+ Giảm nhẹ độ chính xác tổng thể (F1) so với việc dùng 100% LLM, do tuyến đầu có thể bỏ sót các ca đánh đố (ham_looks_spam, obfuscation).
+ Tăng độ phức tạp kiến trúc hệ thống (cần logic định tuyến động giữa các tier) và chi phí API phát sinh cho các tin nhắn chuyển tiếp lên LLM.

## 7. AI log và điều đã học

Hỏi gì: Cách khắc phục lỗi RateLimitError (429) và NotFoundError (404) của OpenAI, tối ưu tham số max_tokens/temperature, dự đoán biểu đồ Pareto và thiết kế hệ thống đạt SLA cho 10 triệu tin nhắn/ngày.

Nhận gì: Hướng dẫn chuyển đổi sang endpoint OpenAI-compatible của Gemini, mẫu code xử lý linh hoạt cho cả môi trường test lẫn thực tế, cùng phân tích chi tiết về cơ chế suy luận ngầm của LLM.

Bạn sửa gì: Cập nhật logic phân nhánh nhà cung cấp (LLM_PROVIDER) trong hàm call_openai, tinh chỉnh thông số prompt và chuẩn hóa hồ sơ nộp bài theo đúng quy định.
