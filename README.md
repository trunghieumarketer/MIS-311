# MIS-311
# Dự án: Phân tích Dữ liệu Chi phí Sinh hoạt (Part 1: Data Analysis and Insight)

Đây là dự án đầu tiên của tôi cho môn MIS 311. Mục tiêu là thực hiện Phân tích Dữ liệu Khám phá (EDA) trên bộ dữ liệu "Cost of Living" (Chi phí Sinh hoạt) để tìm ra các thông tin chi tiết (insights) có ý nghĩa.

## 1. Tổng quan dữ liệu (Data Overview)

* **Nguồn:** [Bạn lấy dữ liệu từ đâu, ví dụ: Kaggle]
* **Kích thước:** 201 hàng và 5 cột.
* **Các cột:** `Country`, `Year`, `Average_Monthly_Income`, `Cost_of_Living`, `Region`.

## 2. Làm sạch dữ liệu (Data Cleaning)

Quá trình làm sạch bao gồm hai bước chính:

1.  **Xử lý giá trị thiếu (Missing Values):**
    * Phát hiện 2 giá trị thiếu ở cột `Region` (cho "Mexico") và 2 giá trị ở cột `Average_Monthly_Income` (cho "Australia" và "Mexico").
    * **Giải pháp:**
        * `Region`: Điền "North America" cho "Mexico" dựa trên tra cứu logic.
        * `Average_Monthly_Income`: Sử dụng phương pháp **"Trung vị theo Nhóm" (Grouped Median)**. Điền thu nhập thiếu của "Australia" bằng trung vị của `Region="Oceania"`, và của "Mexico" bằng trung vị của `Region="North America"`.

2.  **Xử lý dữ liệu trùng lặp (Duplicate Rows):**
    * [Viết kết quả của bạn, ví dụ: "Không tìm thấy hàng nào trùng lặp." hoặc "Đã xóa X hàng trùng lặp."]

## 3. Thống kê mô tả & Thông tin chi tiết (Descriptive Statistics & Insights)

Sau khi làm sạch, tôi đã thực hiện thống kê mô tả và tạo các biểu đồ để trực quan hóa dữ liệu.

*(💡 Mẹo: Bạn hãy chụp ảnh màn hình 2 biểu đồ Excel của bạn, sau đó kéo-thả ảnh trực tiếp vào đây khi đang chỉnh sửa file README)*

### 🚀 Insight 1: Có sự chênh lệch rõ rệt về kinh tế giữa các khu vực.

* [Dán ảnh Biểu đồ Cột nhóm của bạn vào đây]
* **Giải thích (2-3 câu):** [Ví dụ: "Biểu đồ cột nhóm cho thấy [Khu vực A] có cả thu nhập trung bình và chi phí sinh hoạt trung bình cao nhất, trong khi [Khu vực B] thấp nhất. Điều này cho thấy sự phân hóa rõ rệt về mức sống..."]

### 🚀 Insight 2: Thu nhập trung bình và chi phí sinh hoạt có mối tương quan dương.

* [Dán ảnh Biểu đồ Phân tán của bạn vào đây]
* **Giải thích (2-3 câu):** [Ví dụ: "Biểu đồ phân tán cho thấy rõ xu hướng 'thu nhập càng cao, chi phí càng cao'. Hàm ý là mặc dù người dân ở một số quốc gia có thu nhập cao, họ cũng phải đối mặt với chi phí đắt đỏ tương ứng..."]
