# Báo cáo kiểm thử Jmeter
Ngày kiểm thử: 01/07/2025  

Người kiểm thử: Vũ Thành Dương  

Tên dự án: Kiểm thử hiệu năng youtube với Jmeter  

Mục đích kiểm thử: 
- Đánh giá hiệu năng của YouTube khi có nhiều truy cập đồng thời.

- Đo thời gian phản hồi trung bình của trang chủ.
  
- Phát hiện lỗi phản hồi chậm hoặc kết nối thất bại.

- Xác định tính ổn định của hệ thống dưới tải cao.

# Kịch bản kiểm tra
### Thread Group

| Tham số                | Giá trị    |
|------------------------|------------|
| Số lượng luồng (users) | 50         |
| Ramp-Up Period (giây)  | 10         |
| Số lần lặp (loop)      | 3          |

### HTTP Request
- **Phương thức:** GET  
- **Đường dẫn:** `/`  
- **Mô tả:** Truy cập trang chủ YouTube.

### Listener được sử dụng

- View Results Tree
- Summary Report
- Aggregate Report
- Graph Results

### Kết quả kiểm thử 

Dưới đây là thống kê kết quả kiểm thử hiệu năng trang chủ YouTube:

| Chỉ số                | Giá trị                        |
|-----------------------|--------------------------------|
| Tổng số mẫu (Samples) | 450                            |
| Thời gian phản hồi TB | 1788 ms                        |
| Thời gian phản hồi cao nhất | 14,193 ms              |
| Thời gian phản hồi thấp nhất | 741 ms               |
| Độ lệch chuẩn (Std. Dev)     | 3056 ms              |
| Tỷ lệ lỗi (Error %)   | 70.44% tổng thể *(11.33% cho HTTP thành công)* |
| Throughput (Thông lượng) | ~2.8 request/giây        |
| Dung lượng nhận trung bình | 490 KB/s                |
| Dung lượng gửi trung bình  | 0.76 KB/s               |  

![image](https://github.com/user-attachments/assets/9bcf0988-a6d8-4f09-9ba6-bbac2b1bffc9)

![image](https://github.com/user-attachments/assets/5754b558-71be-41c3-8924-99281e477131) 

![image](https://github.com/user-attachments/assets/5fc98f9e-8e82-4629-96a8-0b4d1fade89b)

### Nhận xét:

- **Tỷ lệ lỗi cao (70.44%)**, có thể do YouTube chặn bot hoặc từ chối truy cập bất thường.
- **Thời gian phản hồi cao** và độ lệch chuẩn lớn → hệ thống phản hồi không ổn định dưới tải.
- Cần thêm Header mô phỏng trình duyệt và kiểm thử lại.



