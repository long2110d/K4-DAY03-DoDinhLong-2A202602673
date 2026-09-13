# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Đỗ Đình Long  
> **Mã Sinh Viên / Mã Học viên:** 2A202602673
> **Chủ đề Lựa chọn:** Trợ lý Dịch vụ Khách hàng VinBus
---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4/5 | Agent có thể xử lý các yêu cầu có tính chuỗi như tra cứu thông tin sinh viên rồi đặt lịch hẹn; tuy nhiên trong một vài trường hợp, vì quota API bị giới hạn, hệ thống fallback sang mock nên chuỗi suy luận chưa hoàn toàn tự nhiên như khi dùng API thật. |
| **2. Tool Interaction** | 5/5 | MCP Server đã gọi đúng các tool `academic_query` và `schedule_appointment` theo đúng dữ liệu trong trace log, phản hồi JSON rõ ràng và có cấu trúc hợp lệ. |
| **3. Dynamic Decision** | 4/5 | Hệ thống biết phân biệt câu hỏi trực tiếp với câu hỏi cần tool; ví dụ direct_query không gọi công cụ, còn tra cứu/đặt lịch thì gọi tool phù hợp. |
| **4. Long Horizon Goal** | 3/5 | Có khả năng thực hiện nhiệm vụ theo tiến trình nhiều bước, nhưng độ tự động và tính liên tục còn hạn chế khi chưa có orchestration mạnh hơn hoặc API live ổn định. |
| **TỔNG ĐIỂM AGENTIC FIT** | **16/20** | *Nếu tổng điểm > 12/20: Bài toán rất phù hợp triển khai Agentic System.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (DỰA TRÊN FILE JSON THỰC TẾ)

Dưới đây là đoạn log tiêu biểu lấy từ file [docs/trace_waterfall.json](docs/trace_waterfall.json), phản ánh xử lý thực tế của test case đặt lịch hẹn:

```json
[
  {
    "step": 1,
    "query": "Hãy đặt lịch hẹn tư vấn học vụ cho sinh viên SV2026001 vào lúc 14:00 ngày 15/09/2026 với cố vấn PGS.TS Nguyễn Văn A.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026001",
      "datetime_str": "14:00 15/09/2026",
      "advisor_name": "PGS.TS Nguyễn Văn A"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026001-99",
      "student_id": "SV2026001",
      "datetime": "14:00 15/09/2026",
      "advisor": "PGS.TS Nguyễn Văn A",
      "message": "Đặt lịch thành công cho sinh viên SV2026001 với PGS.TS Nguyễn Văn A vào lúc 14:00 15/09/2026."
    },
    "latency_ms": 5038.19
  }
]
```

> Ghi chú: Trong thời điểm chạy thử thực tế, Gemini API đã gặp lỗi quota (`429 RESOURCE_EXHAUSTED`) nên hệ thống tự động fallback về mock mode cho một số case. Tuy nhiên cấu trúc trace và tool call vẫn được ghi đúng theo bạn dạng thực tế từ app.

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [ ] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** 5/5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** 4 lượt.
- **Kết quả đẩy Repo nộp bài:** [ ] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
