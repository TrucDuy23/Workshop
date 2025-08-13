---
title : "Usage Patterns Analysis"

weight : 4
chapter : false
pre : " <b> 4.1 </b> "
---


---

#### – Switch to Usage Type Analysis
From your current Cost Explorer view:
   ![Analyze Usage Patterns](/images/4/01.png?featherlight=false&width=90pc)
1. In the **Group by** section (right side)
2. Click the dropdown showing **Service**
   ![Analyze Usage Patterns](/images/4/02.png?featherlight=false&width=90pc)


3. Select **Usage Type** from the list
   ![Analyze Usage Patterns](/images/4/03.png?featherlight=false&width=90pc)

4. Click **Apply** or wait for the chart to auto-refresh


**🎯 Expected result:**
- Chart now displays **usage types** instead of services
- Common usage types include:
  - `BoxUsage`
  - `HeavyUsage`
  - `SpotUsage`
  - `TimedStorage`
  - ...
   ![Analyze Usage Patterns](/images/4/04.png?featherlight=false&width=90pc)

---

#### – Analyze EC2 Usage Patterns
**Add a Service Filter for EC2 only:**
1. In **Filters** (right side), click **Service**
2. Click **Choose services**
   ![Analyze Usage Patterns](/images/4/04.png?featherlight=false&width=90pc)

3. Search and check ☑️ **Amazon Elastic Compute Cloud – Compute**
4. Uncheck all other services
5. Click **Apply filters**
   ![Analyze Usage Patterns](/images/4/05.png?featherlight=false&width=90pc)

**🔍 Key Usage Types to analyze:**
   ![Analyze Usage Patterns](/images/4/06.png?featherlight=false&width=90pc)

###  BoxUsage
- On-Demand EC2 instances
- Ví dụ: `BoxUsage:m5.large`, `BoxUsage:t3.medium`
- **Đặc điểm**: Chi phí cao nhất, linh hoạt nhất
- 💡 **Tối ưu**: Chuyển sang Reserved Instances hoặc Spot Instances nếu workload ổn định

###  HeavyUsage
- Reserved Instances
- Ví dụ: `HeavyUsage:m5.large`
- **Đặc điểm**: Chi phí thấp hơn On-Demand **30–70%**
- 💡 **Phân tích thêm**: Kiểm tra tỷ lệ sử dụng (utilization rate)

###  SpotUsage
- Spot Instances
- Ví dụ: `SpotUsage:m5.large`
- **Đặc điểm**: Chi phí rẻ nhất, nhưng có thể bị gián đoạn
- 💡 **Cơ hội tối ưu**: Tăng Spot usage cho workloads chịu lỗi (fault-tolerant)

---

#### – Deep Dive into Instance Types
**Switch Group By to Instance Type:**
1. Group by dropdown → select **Instance Type**
2. Keep Service filter = EC2
   ![Analyze Usage Patterns](/images/4/07.png?featherlight=false&width=90pc)

3. Review the results
   ![Analyze Usage Patterns](/images/4/08.png?featherlight=false&width=90pc)

**Common High Usage Instance Types:**
- `m5.large`: General purpose, balanced
- `t3.medium`: Burstable, cost-effective for variable workloads
- `c5.xlarge`: Compute optimized
- `r5.large`: Memory optimized

---

##  Key Analysis Questions:
- Which instance type has the **highest cost**?
- Are there **oversized instances**? (high cost, low utilization)
- Can smaller instances be **consolidated** into fewer larger ones?
- Is the current workload **well-matched** to the chosen instance type?
---
