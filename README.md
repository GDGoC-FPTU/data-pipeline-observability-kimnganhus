[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574180&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** kinngantran2k3@gmail.com
**Name:** Trần Thị Kim Ngân

---

## Mo ta

Bài lab này xây dựng một ETL pipeline đơn giản để xử lý dữ liệu sản phẩm.
- `solution.py` đọc dữ liệu từ `raw_data.json`.
- Kiểm tra và loại bỏ các record không hợp lệ.
- Tính `discounted_price` = 90% của `price`.
- Chuẩn hóa `category` thành Title Case.
- Thêm cột `processed_at` để quan sát thời điểm xử lý.
- Ghi dữ liệu sạch ra `processed_data.csv`.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
├── agent_simulation.py      # Script de so sanh Clean va Garbage data
├── garbage_data.csv         # Du lieu nhiem nhieu de test
└── README.md                # File nay
```

---

## Ket qua

Pipeline đã xử lý 5 bản ghi từ `raw_data.json`, giữ lại 3 bản ghi hợp lệ và loại 2 bản ghi không hợp lệ.
- 3 bản ghi hợp lệ được ghi vào `processed_data.csv`
- 2 bản ghi bị loại vì: `price <= 0` và `missing category`
