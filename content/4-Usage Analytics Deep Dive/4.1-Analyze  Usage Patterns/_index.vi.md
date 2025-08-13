---
title : "Phân tích Usage Patterns"

weight : 4
chapter : false
pre : " <b> 4.1 </b> "
---


---

#### – Chuyển sang Usage Type Analysis
Từ màn hình Cost Explorer hiện tại:
   ![Analyze Usage Patterns](/images/4/01.png?featherlight=false&width=90pc)
1. Ở phần **Group by** (bên phải màn hình)
2. Click vào dropdown đang hiển thị **Service**
   ![Analyze Usage Patterns](/images/4/02.png?featherlight=false&width=90pc)


3. Chọn **Usage Type** từ danh sách
   ![Analyze Usage Patterns](/images/4/03.png?featherlight=false&width=90pc)

4. Click **Apply** hoặc chờ màn hình tự động cập nhật


**🎯 Kết quả mong đợi:**
- Biểu đồ hiển thị theo **usage types** thay vì theo service
- Các loại usage type phổ biến:
  - `BoxUsage`
  - `HeavyUsage`
  - `SpotUsage`
  - `TimedStorage`
  - ...
   ![Analyze Usage Patterns](/images/4/04.png?featherlight=false&width=90pc)

---

#### – Phân tích EC2 Usage Patterns
**Thêm Service Filter để tập trung vào EC2:**
1. Ở phần **Filters** (bên phải), click **Service**
2. Click **Choose services**
   ![Analyze Usage Patterns](/images/4/04.png?featherlight=false&width=90pc)

3. Tìm và tick ☑️ **Amazon Elastic Compute Cloud – Compute**
4. Bỏ tick các services khác
5. Click **Apply filters**
   ![Analyze Usage Patterns](/images/4/05.png?featherlight=false&width=90pc)

**🔍 Phân tích các Usage Types quan trọng:**
   ![Analyze Usage Patterns](/images/4/06.png?featherlight=false&width=90pc)

### 📊 BoxUsage
- On-Demand EC2 instances
- Ví dụ: `BoxUsage:m5.large`, `BoxUsage:t3.medium`
- **Đặc điểm**: Chi phí cao nhất, linh hoạt nhất
- 💡 **Tối ưu**: Chuyển sang Reserved Instances hoặc Spot Instances nếu workload ổn định

### 📊 HeavyUsage
- Reserved Instances
- Ví dụ: `HeavyUsage:m5.large`
- **Đặc điểm**: Chi phí thấp hơn On-Demand **30–70%**
- 💡 **Phân tích thêm**: Kiểm tra tỷ lệ sử dụng (utilization rate)

### 📊 SpotUsage
- Spot Instances
- Ví dụ: `SpotUsage:m5.large`
- **Đặc điểm**: Chi phí rẻ nhất, nhưng có thể bị gián đoạn
- 💡 **Cơ hội tối ưu**: Tăng Spot usage cho workloads chịu lỗi (fault-tolerant)

---

#### – Phân tích sâu theo Instance Types
**Chuyển Group By sang Instance Type:**
1. Group by dropdown → chọn **Instance Type**
2. Giữ nguyên Service filter = EC2
   ![Analyze Usage Patterns](/images/4/07.png?featherlight=false&width=90pc)

3. Quan sát biểu đồ kết quả
   ![Analyze Usage Patterns](/images/4/08.png?featherlight=false&width=90pc)

**📈 High Usage Instance Types phổ biến:**
- `m5.large`: General purpose, balanced
- `t3.medium`: Burstable, tiết kiệm chi phí cho workload biến động
- `c5.xlarge`: Compute optimized
- `r5.large`: Memory optimized

---

## ❓ Các câu hỏi phân tích cần trả lời:
- Instance nào chiếm **chi phí cao nhất**?
- Có **oversized instances** không? (chi phí cao, sử dụng thấp)
- Có thể **gộp nhiều instance nhỏ** thành ít instance lớn hơn không?
- Workload có **phù hợp** với instance type hiện tại không?

---
