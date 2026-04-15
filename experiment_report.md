# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600432
**Name:** (Trần Thị Kim Ngân)
**Date:** (4/15/2026)

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dữ liệu sạch, nhất quán, có category `Electronics` và giá hợp lệ. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Dữ liệu nhiễu, outlier và giá trị sai định dạng làm agent chọn sai. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Trong `garbage_data.csv`, agent vẫn dùng cùng truy vấn: "What is the best electronic product?" nhưng dữ liệu đầu vào bị lỗi.

- Duplicate IDs: có hai bản ghi cùng `id=1`, làm giảm độ tin cậy của bảng dữ liệu.
- Wrong data types: giá trị `price` là `ten dollars` không thể chuyển thành số, gây lỗi nếu có xử lý nghiêm túc.
- Outliers: bản ghi `Nuclear Reactor` có giá `999999` là ngoại lai quá lớn, khiến thuật toán chọn giá cao nhất mặc dù không thực tế.
- Null values/missing fields: có một mục `Ghost Item` thiếu `category`, khiến lọc theo `electronics` có thể bị sai nếu không kiểm soát tốt.

Do hàm `simulate_agent_response()` chỉ đơn giản chọn sản phẩm điện tử có `price` lớn nhất, nên dữ liệu garbage đã khiến agent trả về `Nuclear Reactor` là lựa chọn "tốt nhất" theo giá. Đây không phải câu trả lời hợp lý, mà là kết quả của dữ liệu sai, không phải do prompt.

Vì vậy, agent sai không phải vì câu hỏi, mà vì chất lượng dữ liệu đầu vào quá kém. Dữ liệu không sạch dẫn đến output sai ngay cả khi prompt rõ ràng và cố định.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Prompt tốt giúp chỉ dẫn agent, nhưng nếu dữ liệu đầu vào nhiễu, sai định dạng, hoặc chứa ngoại lai thì agent vẫn trả lời sai. Chất lượng dữ liệu là yếu tố quan trọng hơn để đảm bảo kết quả đúng và đáng tin cậy.
