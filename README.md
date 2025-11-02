# MIS-311
# MIS 311 - Dự án: Phân tích Dữ liệu Chi phí Sinh hoạt (Cost of Living EDA)

Đây là dự án Phân tích Dữ liệu Khám phá (EDA) cho môn học MIS 311. Mục tiêu là phân tích bộ dữ liệu "Cost of Living" để làm sạch, trực quan hóa và rút ra 2 thông tin chi tiết (key insights) có ý nghĩa về bối cảnh kinh tế toàn cầu.

---

## 1. Tổng quan & Làm sạch Dữ liệu (Data Overview & Cleaning)

Quá trình này tập trung vào việc đảm bảo tính toàn vẹn và độ tin cậy của dữ liệu trước khi phân tích.

### Xử lý Giá trị bị thiếu (Missing Values)

Khi kiểm tra ban đầu, tôi phát hiện 4 ô dữ liệu bị thiếu:
* 2 ô trống ở cột `Region` (dữ liệu phân loại).
* 2 ô trống ở cột `Average_Monthly_Income` (dữ liệu số).

**Giải pháp của tôi:**

1.  **Với `Region` (Tra cứu logic):**
    * Tôi phát hiện 2 hàng của quốc gia "Mexico" bị thiếu `Region`.
    * Thay vì xóa, tôi đã lọc các hàng "Mexico" khác trong bộ dữ liệu và xác định `Region` chính xác của họ là **"North America"** rồi điền vào.

2.  **Với `Average_Monthly_Income` (Trung vị theo Nhóm):**
    * Tôi phát hiện 1 hàng "Australia" và 1 hàng "Mexico" bị thiếu thu nhập.
    * Sử dụng phương pháp **"Trung vị theo Nhóm" (Grouped Median)**. Đây là phương pháp chính xác nhất, vì thu nhập trung vị của "Oceania" (cho Australia) sẽ khác với thu nhập trung vị của "North America" (cho Mexico).
    * Quá trình này đã gặp một số thách thức kỹ thuật (chi tiết ở mục 3).

### Xử lý Dữ liệu Trùng lặp (Duplicates)

* Tôi đã sử dụng chức năng "Remove Duplicates" của Excel để kiểm tra.
* **Kết quả:** [Điền kết quả của bạn, ví dụ: "Không tìm thấy hàng nào trùng lặp." hoặc "Đã tìm và xóa X hàng trùng lặp."]

---

## 2. Phân tích, Trực quan hóa & Insights

Sau khi có bộ dữ liệu sạch, tôi tiến hành thống kê mô tả và trực quan hóa để tìm ra câu chuyện.

### Insight 1: Có sự phân hóa sâu sắc về kinh tế giữa các khu vực.

Biểu đồ cột nhóm dưới đây so sánh Thu nhập trung bình (`Average`) và Chi phí sinh hoạt trung bình (`Average`) của các khu vực.

**⚠️ Lưu ý:** *Ban đầu tôi đã dùng `Sum` (Tổng) nhưng nhanh chóng nhận ra đây là một lỗi nghiêm trọng, vì số lượng bản ghi ở mỗi khu vực khác nhau (ví dụ: Europe có 73 hàng, S.America chỉ có 12). Việc so sánh `Sum` là vô nghĩa. Tôi đã chuyển sang dùng **`Average`** để có một sự so sánh công bằng.*

**Biểu đồ 1: So sánh Thu nhập và Chi phí Sinh hoạt Trung bình theo Khu vực**

> `[!!! DÁN ẢNH BIỂU ĐỒ CỘT NHÓM CỦA BẠN VÀO ĐÂY !!!]`
> 
> *Bạn có thể kéo thả file ảnh .png hoặc .jpg vào đây*

**Giải thích:**
Biểu đồ cho thấy rõ ràng **[Tên Khu Vực Cao Nhất, ví dụ: Europe]** có cả thu nhập và chi phí sinh hoạt trung bình cao vượt trội so với phần còn lại. Ngược lại, **[Tên Khu Vực Thấp Nhất, ví dụ: Africa]** có cả hai chỉ số này thấp nhất. Hàm ý là mức sống và chi phí trên toàn cầu rất không đồng đều, đòi hỏi các doanh nghiệp phải có chiến lược giá và sản phẩm riêng biệt cho từng thị trường.

---

### Insight 2: Thu nhập cao thường đi đôi với chi phí sinh hoạt đắt đỏ.

Biểu đồ Phân tán (Scatter Plot) dưới đây khám phá mối quan hệ thực sự giữa hai biến số Thu nhập và Chi phí.

**Biểu đồ 2: Mối quan hệ giữa Thu nhập Hàng tháng và Chi phí Sinh hoạt**

> `[!!! DÁN ẢNH BIỂU ĐỒ PHÂN TÁN (SCATTER PLOT) CỦA BẠN VÀO ĐÂY !!!]`
> 
> *Bạn có thể kéo thả file ảnh .png hoặc .jpg vào đây*

**Giải thích:**
Biểu đồ cho thấy một **mối tương quan dương (positive correlation)** rõ rệt (các điểm dữ liệu đi chéo từ dưới lên trên). Hàm ý là khi thu nhập của một quốc gia tăng lên, chi phí sinh hoạt tại đó cũng có xu hướng tăng theo. Điều này thách thức quan niệm đơn giản rằng "cứ lương cao là sống sướng" mà phải xét đến sức mua thực tế sau khi trừ đi chi phí đắt đỏ tương ứng.

---

## 3. Thách thức Kỹ thuật & Giải pháp (Excel trên MacBook)

Đây là một phần quan trọng của dự án, thể hiện khả năng giải quyết vấn đề. Khi cố gắng tính **"Trung vị theo Nhóm"** (Kế hoạch A), tôi đã liên tiếp gặp 3 rào cản do hạn chế của phiên bản Excel trên MacBook của mình:

1.  **Lỗi 1: PivotTable không có hàm `Median`**
    * Phiên bản Excel của tôi không hiển thị `Median` trong "Value Field Settings...".

2.  **Lỗi 2: Không có tính năng "Add to Data Model"**
    * Kế hoạch B (dùng "Data Model" để mở khóa `Median`) thất bại, vì phiên bản Mac này không có checkbox "Add to Data Model".

3.  **Lỗi 3: Không có hàm `MEDIANIFS`**
    * Kế hoạch C (dùng công thức `=MEDIANIFS(...)`) thất bại, vì hàm này không được hỗ trợ.

**🏆 Giải pháp (Kế hoạch D - Vượt qua khó khăn):**
Tôi đã quay về phương pháp thủ công 100% nhưng vẫn đảm bảo độ chính xác:
1.  Sử dụng **Filter (Lọc)** để chỉ hiển thị `Region = "Oceania"`.
2.  Bôi đen các con số `Average_Monthly_Income` và đọc số `Median` hiển thị trên **Thanh trạng thái (Status Bar)**.
3.  Lặp lại quy trình cho `Region = "North America"`.

Bằng cách này, tôi vẫn áp dụng được phương pháp phân tích tốt nhất (Trung vị theo Nhóm) thay vì chấp nhận một phương pháp đơn giản nhưng kém chính xác hơn (như dùng Trung bình chung).
