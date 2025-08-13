---
title : "Optimization Implementation"

weight : 5
chapter : false
pre : " <b> 5. </b> "
---

# 🚀 Triển khai Tối ưu hóa: Auto Scaling & Chiến lược Gắn Tag Resource

## 1️⃣ Giới thiệu
Quản lý chi phí đám mây hiệu quả không chỉ là cắt giảm chi tiêu — mà là đảm bảo mỗi đồng bỏ ra mang lại giá trị tối đa. Hai chiến lược quan trọng trong tối ưu chi phí AWS là:

- **Auto Scaling** – Tự động điều chỉnh tài nguyên theo nhu cầu, tránh dư thừa mà vẫn đảm bảo hiệu năng.
- **Chiến lược Tag Resource** – Gắn nhãn hệ thống cho tài nguyên để phân bổ, theo dõi và quản trị chi phí.

---

## 2️⃣ Auto Scaling – Quản lý Tài nguyên & Chi phí Động

### 🎯 Mục tiêu:
Tự động tăng hoặc giảm tài nguyên tính toán theo tải công việc, đảm bảo tối ưu chi phí mà không làm giảm hiệu năng.

### 🔹 Lợi ích chính:
- **Tự động đúng kích thước** – Mở rộng khi tải cao, thu nhỏ khi tải thấp.
- **Tránh lãng phí** – Không trả tiền cho năng lực không dùng đến.
- **Duy trì SLA** – Tự động đáp ứng yêu cầu hiệu suất.

### 🔹 Các bước triển khai:
1. **Tạo Launch Template hoặc Launch Configuration** cho cấu hình chuẩn.
2. **Tạo Auto Scaling Group (ASG)** với:
   - Minimum capacity
   - Desired capacity
   - Maximum capacity
3. **Cấu hình Scaling Policy**:
   - **Target Tracking** – Duy trì chỉ số mục tiêu (ví dụ CPU 70%).
   - **Step Scaling** – Tăng/giảm theo ngưỡng cụ thể.
4. **Tích hợp với CloudWatch** để giám sát và cảnh báo.
5. **Kiểm thử scaling** bằng load test.

### 💡 Mẹo hay:
- Dùng **nhiều AZ** để tăng tính sẵn sàng.
- Thiết lập **cooldown & warmup time** để tránh scaling liên tục.
- Kết hợp **Spot Instances** trong ASG cho workload không quan trọng.

---

## 3️⃣ Chiến lược Tag Resource – Phân bổ & Hiển thị Chi phí

### 🎯 Mục tiêu:
Tạo cấu trúc gắn tag chuẩn để dễ dàng theo dõi, phân bổ và tối ưu chi tiêu đám mây.

### 🔹 Lợi ích chính:
- **Phân bổ chi phí rõ ràng** theo dự án, nhóm hoặc môi trường.
- **Tăng khả năng quản trị** và kiểm soát bảo mật.
- **Báo cáo dễ dàng** qua AWS Cost Explorer và Budgets.

### 🔹 Các loại tag:
| Tag Key        | Giá trị ví dụ  | Mục đích |
|----------------|---------------|----------|
| `Environment`  | `Prod` / `Dev`| Phân biệt môi trường |
| `Project`      | `EcommerceApp`| Gán chi phí cho dự án |
| `Owner`        | `TeamA`       | Xác định
