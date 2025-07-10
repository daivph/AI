# 📃 Báo Cáo CRISP-DM: Dự Báo Năng Suất Sản Xuất Nông Nghiệp Hoa Kỳ

## 1. ✨ Mục Tiêu & Xác Định Vấn Đề

### Bài Toán:

Dự báo năng suất cho các loại cây trồng tại Hoa Kỳ dựa trên dữ liệu lịch sử từ FAOSTAT.

### Mục Tiêu:

* Xác định xu hướng tăng/giảm năng suất.
* Hỗ trợ lập kế hoạch sản xuất, cung ứng, và định hướng chính sách.

## 2. 📊 Hiểu Dữ Liệu

* Nguồn: FAOSTAT - Crops and Livestock Products
* Khu vực: United States of America
* Các trường dữ liệu:

  * `Area`, `Element`, `Item`, `Year`, `Value`
* Tổng sản phẩm: ≥ 100 loại (Almonds, Maize, Wheat, etc.)
* Chỉ số phân tích: `Yield` (kg/ha)

## 3. 🔧 Xử Lý Dữ Liệu

### Bước xử lý:

1. Lọc `Area = United States of America` và `Element = Yield`
2. Bỏ NaN, chuẩn hóa kiểu dữ liệu
3. Chuyển `Year` → `datetime` (đặt tên `ds`) để dùng Prophet
4. Tách từng `Item` để dự báo riêng lẻ

## 4. 🧠 Xây Dựng Mô Hình

* Mô hình dùng: **Prophet**
* Tính năng:

  * Tính xu hướng dài hạn
  * Tự động bù dữ liệu thiếu
  * Hỗ trợ chuỗi thời gian không đều
* Dự báo: 5 năm tiếp theo cho từng sản phẩm

## 5. 📊 Đánh Giá Mô Hình

* **Chỉ số đánh giá:**

  * MAE (Mean Absolute Error): 456.94 kg/ha
  * R² (R-squared): 0.7418

### ✨ Nhận định:

* Sai số \~457 kg/ha là đáng kể nhưng chấp nhận được.
* Mô hình Prophet bám sát xu hướng, dự báo tốt cho chuỗi thời gian lâu dài.

## 6. 🚀 Triển Khai & Đề Xuất Cải Thiện

### ✅ Kết Quả:

* Mô hình Prophet hoạt động tốt với R² > 0.7
* Tự động vẽ biểu đồ xu hướng & dự báo

### ⚠️ Hạn chế:

* Chưa tính yếu tố khí hậu, chi phí, đầu vào
* Một số sản phẩm dữ liệu thiếu nhiều năm

### 🔄 Đề Xuất Mở Rộng:

* Thêm biến để huấn luyện: mưa, nhiệt độ, chi phí, v.v.
* Dự báo theo từng tiểu bang (nếu dữ liệu hỗ trợ)

---

## 📄 Tài Liệu Liên Quan

### ▶️ Mã Demo Trên Google Colab:

[https://colab.research.google.com/drive/1IjK__-x5-q4HHBGEzhPuw-VlEb_VtV3L?usp=sharing)

### 🔗 Dữ liệu:

[Data](https://raw.githubusercontent.com/daivph/AI/refs/heads/main/FAOSTAT_Crops_and_Livestock_Products.csv)

---
