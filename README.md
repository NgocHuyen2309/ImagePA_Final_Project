# 🔍 Surface Defect Detection using Morphological Processing
**Đồ án môn học: Xử lý và Phân tích ảnh** | **Giảng viên hướng dẫn: TS. Đặng N.H. Thành**

[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.9.0-green.svg)](https://opencv.org/)
[![ReactJS](https://img.shields.io/badge/React-18.x-61DAFB.svg)](https://reactjs.org/)

## 📖 Tổng quan dự án (Project Overview)
Dự án này ứng dụng các kỹ thuật xử lý hình thái học (Morphological Image Processing) để tự động nhận diện và trích xuất các khiếm khuyết (defect) trên bề mặt sản phẩm công nghiệp. Các bài toán ứng dụng tiêu biểu bao gồm: phát hiện vết xước/lỗi đường mạch trên bảng mạch in (PCB) và lỗi đứt chỉ/thủng lỗ trên bề mặt sản phẩm dệt may.

Hệ thống cung cấp một Web Application trực quan, cho phép người dùng upload ảnh sản phẩm, tùy chỉnh cấu hình thuật toán và so sánh trực tiếp kết quả phát hiện lỗi.

### ✨ Tính năng chính (Key Features)
- **Tiền xử lý thông minh:** Chuyển đổi ảnh xám, khử nhiễu và nhị phân hóa tự động sử dụng phương pháp Otsu (Otsu's Thresholding).
- **Phân tích hình thái học:** Hỗ trợ các toán tử cốt lõi: `Erosion`, `Dilation`, `Opening`, `Closing` với khả năng tùy chỉnh kernel (Structuring Elements).
- **Trích xuất & Đánh giá đặc trưng:** Phân đoạn ảnh (Segmentation), tìm vùng liên thông (Connected Components) và làm nổi bật vùng lỗi (Bounding box/Contours).
- **Giao diện trực quan:** Ứng dụng Web cho phép so sánh Before/After một cách rõ ràng.

---

## 🛠 Công nghệ sử dụng (Tech Stack)
- **Core Vision & Algorithm:** Python, OpenCV, Scikit-Image, NumPy.
- **Backend API:** FastAPI / Flask.
- **Frontend Web App:** ReactJS, HTML5, CSS3/Tailwind.

---

## 📁 Cấu trúc thư mục (Repository Structure)

```text
📦 ImagePA_Final_Project
 ┣ 📂 app                  # Web Application Source Code
 ┃ ┣ 📂 backend            # API xử lý ảnh (FastAPI/Flask)
 ┃ ┗ 📂 frontend           # Giao diện người dùng (ReactJS)
 ┣ 📂 data                 # Dữ liệu hình ảnh
 ┃ ┣ 📂 processed          # Ảnh đã qua tiền xử lý (được sinh ra tự động)
 ┃ ┗ 📂 raw                # Ảnh gốc mẫu (Sample dataset)
 ┣ 📂 docs                 # Tài liệu, slide và Báo cáo tổng kết (Format AI)
 ┣ 📂 notebooks            # Jupyter Notebooks cho EDA và thử nghiệm thuật toán
 ┣ 📂 src                  # Core Image Processing Modules
 ┃ ┣ 📜 morphological.py   # Thuật toán hình thái học
 ┃ ┣ 📜 segmentation.py    # Thuật toán phân đoạn, nhị phân hóa
 ┃ ┗ 📜 utils.py           # Helper functions (I/O, visualization)
 ┣ 📜 .gitignore           # File cấu hình bỏ qua của Git
 ┣ 📜 README.md            # Tài liệu dự án
 ┗ 📜 requirements.txt     # Danh sách thư viện Python phụ thuộc
```

---

## 🚀 Hướng dẫn Cài đặt & Khởi chạy (Getting Started)

### 1. Yêu cầu hệ thống (Prerequisites)
- [Python 3.9+](https://www.python.org/downloads/)
- [Node.js & npm](https://nodejs.org/en/) (dành cho Frontend)

### 2. Cài đặt Môi trường (Installation)
Clone repository về máy local:
```bash
git clone [https://github.com/NgocHuyen2309/ImagePA_Final_Project.git](https://github.com/NgocHuyen2309/ImagePA_Final_Project.git)
cd ImagePA_Final_Project
```

Tạo môi trường ảo và cài đặt thư viện Python:
```bash
# Tạo virtual environment (khuyến nghị)
python -m venv .venv

# Active môi trường ảo
# Trên Windows:
.venv\Scripts\activate
# Trên macOS/Linux:
source .venv/bin/activate

# Cài đặt packages
pip install -r requirements.txt
```

### 3. Khởi chạy Ứng dụng (Running the App)

**Terminal 1 - Chạy Backend API:**
```bash
cd app/backend
# Lệnh chạy server (Ví dụ với FastAPI)
uvicorn main:app --reload
```

**Terminal 2 - Chạy Frontend:**
```bash
cd app/frontend
npm install
npm start
```
*Truy cập ứng dụng tại địa chỉ: `http://localhost:3000`*

---

## 📊 Báo cáo và Đánh giá (Report & Evaluation)
Bản báo cáo chi tiết được trình bày theo chuẩn format môn Trí tuệ Nhân tạo (AI) và được lưu trữ tại thư mục `docs/`. 

Phần đánh giá tập trung vào việc **phân tích, so sánh kết quả** giữa các phương pháp tiếp cận khác nhau:
- Sự khác biệt khi sử dụng các Structuring Elements (hình vuông, hình elip, dấu thập) với các kích thước (3x3, 5x5, 7x7...).
- So sánh thời gian thực thi (Execution Time) và độ nhiễu dư thừa giữa các tổ hợp toán tử (Opening vs. Closing) đối với từng loại bề mặt chất liệu.

---

## 👥 Thành viên nhóm (Team Members)

| STT | Họ và Tên | Vai trò |
| :---: | :--- | :--- |
| 1 | **Hứa Thị Ngọc Huyền** | Frontend & Web App Lead |
| 2 | **Huỳnh Minh Trí** | Core Vision & Algorithm |
| 3 | **Phan Lê Trường An** | Data & Backend API |
| 4 | **Phạm Duy Hoàng** | QA, Evaluation & Report |

---
*Mọi thao tác phát triển, cập nhật tiến độ đều được quản lý thông qua GitHub Issues và Project Board của repository này.*