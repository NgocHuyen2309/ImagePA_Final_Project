# 🔍 Surface Defect Detection: Morphological & Machine Learning Approach
**Đồ án môn học: Xử lý và Phân tích ảnh** | **Giảng viên hướng dẫn: TS. Đặng N.H. Thành**

[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.9.0-green.svg)](https://opencv.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.4-orange.svg)](https://scikit-learn.org/)
[![ReactJS](https://img.shields.io/badge/React-18.x-61DAFB.svg)](https://reactjs.org/)

## 📖 Tổng quan dự án (Project Overview)
Dự án tập trung xây dựng hệ thống tự động phát hiện và phân loại khiếm khuyết trên bề mặt sản phẩm công nghiệp (PCB, vải dệt). Hệ thống kết hợp sức mạnh của **3 kỹ thuật xử lý ảnh truyền thống** để trích xuất vùng lỗi và **1 mô hình Machine Learning** để phân loại chính xác loại lỗi.

## 🛠 Quy trình xử lý (Pipeline 3+1)
Dự án được thiết kế theo luồng xử lý chuẩn công nghiệp, bám sát chương trình giảng dạy:
1.  **Tiền xử lý (Kỹ thuật 1):** Khử nhiễu (Median/Gaussian) và nhị phân hóa bằng phương pháp Otsu.
2.  **Xử lý hình thái học (Kỹ thuật 2):** Sử dụng các toán tử Erosion, Dilation, Opening, Closing để tách biệt và làm rõ vùng lỗi.
3.  **Trích xuất đặc trưng (Kỹ thuật 3):** Tính toán diện tích (Area), chu vi (Perimeter), độ lệch tâm (Eccentricity) và các thuộc tính hình học của đối tượng lỗi.
4.  **Phân loại Machine Learning (Mô hình AI):** Sử dụng mô hình SVM hoặc Random Forest để phân loại lỗi dựa trên bộ đặc trưng đã trích xuất.

---

## 📁 Cấu trúc thư mục (Repository Structure)

```text
📦 ImagePA_Final_Project
 ┣ 📂 app                  # Web Application Source Code
 ┃ ┣ 📂 backend            # FastAPI Server (Tích hợp API và Model)
 ┃ ┗ 📂 frontend           # Giao diện người dùng (ReactJS & Tailwind)
 ┣ 📂 data                 # Quản lý dữ liệu hình ảnh
 ┃ ┣ 📂 processed          # Ảnh sau khi qua các bước tiền xử lý/morphological
 ┃ ┗ 📂 raw                # Dataset ảnh lỗi gốc (PCB, dệt may)
 ┣ 📂 docs                 # Báo cáo mẫu AI & Slide thuyết trình
 ┣ 📂 models               # Lưu trữ file mô hình ML đã huấn luyện (.pkl)
 ┣ 📂 notebooks            # Jupyter Notebooks phục vụ thử nghiệm thuật toán
 ┣ 📂 src                  # Core Logic (Chia theo chuẩn 3+1)
 ┃ ┣ 📜 preprocessing.py   # Kỹ thuật 1: Tiền xử lý ảnh
 ┃ ┣ 📜 morphological.py   # Kỹ thuật 2: Xử lý hình thái học
 ┃ ┣ 📜 feature_extraction.py # Kỹ thuật 3: Trích xuất đặc trưng vùng lỗi
 ┃ ┗ 📜 ml_classifier.py   # Mô hình ML: Phân loại khiếm khuyết
 ┣ 📜 .gitignore           # Cấu hình bỏ qua các tệp rác môi trường
 ┣ 📜 README.md            # Tài liệu hướng dẫn dự án
 ┗ 📜 requirements.txt     # Danh sách thư viện Python cần thiết
```

---

## 🚀 Hướng dẫn Cài đặt & Khởi chạy (Getting Started)

### 1. Cài đặt Môi trường
Clone repository về máy local:
```bash
git clone [https://github.com/NgocHuyen2309/ImagePA_Final_Project.git](https://github.com/NgocHuyen2309/ImagePA_Final_Project.git)
cd ImagePA_Final_Project
```

Thiết lập môi trường ảo và cài đặt thư viện:
```bash
python -m venv .venv

# Kích hoạt môi trường (Windows)
.venv\Scripts\activate
# Kích hoạt môi trường (macOS/Linux)
source .venv/bin/activate

pip install -r requirements.txt
```

### 2. Khởi chạy Ứng dụng

**Terminal 1 - Khởi chạy Backend:**
```bash
# Chạy từ thư mục gốc
uvicorn app.backend.main:app --reload
```

**Terminal 2 - Khởi chạy Frontend:**
```bash
cd app/frontend
npm install
npm start
```
*Giao diện sẽ hiển thị tại: `http://localhost:3000`*

---

## 👥 Thành viên nhóm & Phân công (Team Members)

| STT | Họ và Tên | Vai trò chính | Task kỹ thuật (3+1) |
| :---: | :--- | :--- | :--- |
| 1 | **Hứa Thị Ngọc Huyền** | Team Lead & Frontend | **Kỹ thuật 2:** Morphological Processing |
| 2 | **Phan Lê Trường An** | QA & Report | **Kỹ thuật 1:** Image Pre-processing |
| 3 | **Huỳnh Minh Trí** | Backend Architecture | **Kỹ thuật 3:** Feature Extraction |
| 4 | **Phạm Duy Hoàng** | AI & Data Engineer | **Mô hình ML:** Defect Classification |

---

## 📊 Báo cáo và Đánh giá (Report & Evaluation)
Tài liệu báo cáo chi tiết theo chuẩn format môn học được lưu trữ tại thư mục `docs/`. 

Phần thực nghiệm bao gồm:
- Phân tích và so sánh kết quả khi thay đổi kích thước Structuring Elements trong xử lý Morphological.
- Đánh giá mô hình ML thông qua Confusion Matrix, Accuracy và F1-Score trên tập dữ liệu thử nghiệm.
- So sánh thời gian thực thi của luồng xử lý trên nền tảng Web.

---
*Mọi thay đổi mã nguồn và cập nhật tiến độ được quản lý nghiêm ngặt qua GitHub Issues và Project Board của nhóm.*