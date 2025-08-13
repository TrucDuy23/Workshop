---
title : "Auto Scaling – Quản lý chi phí động"

weight : 5
chapter : false
pre : " <b> 5.1 </b> "
---


---

#### Truy cập Auto Scaling Groups

**Từ AWS Console:**
1. Vào *Search → EC2**

2. Trong màn hình **EC2 dashboard**, cuộn menu bên trái xuống
3. Tìm mục **AUTO SCALING**
4. Click **Auto Scaling Groups**
![Auto Scaling ](/images/5/13.png?featherlight=false&width=90pc)

---

### Tạo Auto Scaling Group (nếu chưa có)
![Auto Scaling ](/images/5/14.png?featherlight=false&width=90pc)

#### Tạo Launch Template
1. Trong EC2 console, click **Launch Templates** (menu trái)
2. Click **Create launch template**
![Auto Scaling ](/images/5/15.png?featherlight=false&width=90pc)

3. Cấu hình:
   - **Name:** `web-app-template`
![Auto Scaling ](/images/5/16.png?featherlight=false&width=90pc)

   - **AMI:** Amazon Linux 2 (hoặc AMI có sẵn)
![Auto Scaling ](/images/5/17.png?featherlight=false&width=90pc)

   - **Instance type:** `t2.micro`
![Auto Scaling ](/images/5/18.png?featherlight=false&width=90pc)

   - **Key pair:** your-key-pair
![Auto Scaling ](/images/5/19.png?featherlight=false&width=90pc)

4. Click **Create launch template**
![Auto Scaling ](/images/5/22.png?featherlight=false&width=90pc)


---

#### Tạo Auto Scaling Group
1. Quay lại **Auto Scaling Groups**
2. Click **Create Auto Scaling group**

3. ** Chọn launch template:**
   - Name: `web-app-asg`
![Auto Scaling ](/images/5/23.png?featherlight=false&width=90pc)

   - Launch template: `web-app-template`
  
![Auto Scaling ](/images/5/24.png?featherlight=false&width=90pc)

4. **Network:**
   - VPC: Default (hoặc custom)
   - Subnets: chọn **3+ subnets** ở các AZ khác nhau
![Auto Scaling ](/images/5/25.png?featherlight=false&width=90pc)

5. ** Load balancing** (tùy chọn):
   - Gắn với ALB có sẵn (nếu có)
![Auto Scaling ](/images/5/26.png?featherlight=false&width=90pc)

6. ** Group size:**
   - Desired: `2`
   - Minimum: `1`
   - Maximum: `5`
![Auto Scaling ](/images/5/27.png?featherlight=false&width=90pc)
![Auto Scaling ](/images/5/28.png?featherlight=false&width=90pc)
    - SNS Topic: chọn sns topic đã tạo
![Auto Scaling ](/images/5/29.png?featherlight=false&width=90pc)

7. **Review** và click **Create**
![Auto Scaling ](/images/5/30.png?featherlight=false&width=90pc)


---
### Cấu hình Dynamic Scaling

#### Truy cập Scaling Policies
1. Trong danh sách **Auto Scaling Groups**, click tên ASG
2. Màn hình chi tiết ASG có các tab:  
   **Details | Activity | Instance management | Monitoring | Automatic scaling**
3. Click tab **Automatic scaling**
![Auto Scaling ](/images/5/33.png?featherlight=false&width=90pc)



---

#### Bước 3.2 – Tạo Target Tracking Policy
1. Trong tab **Automatic scaling** → mục **Dynamic scaling policies**
2. Click **Create dynamic scaling policy**
![Auto Scaling ](/images/5/32.png?featherlight=false&width=90pc)
![Auto Scaling ](/images/5/34.png?featherlight=false&width=90pc)
![Auto Scaling ](/images/5/35.png?featherlight=false&width=90pc)

**Mẹo cấu hình nâng cao:**
- **Disable scale-in** nếu chỉ muốn **scale out**
- Điều chỉnh **instance warmup** tùy workload:
  - 300s (5 phút): Web app thông thường
  - 600s (10 phút): App khởi động chậm
  - 120s (2 phút): App nhẹ
- Target value gợi ý:
  - Web servers: **70% CPU**
  - Database: **60% CPU**
  - Background workers: **80% CPU**

---

### Advanced Scaling (Step Scaling)

**Khi nên dùng Step Scaling:**
✅ Cần điều khiển chi tiết  
✅ Nhiều ngưỡng scaling khác nhau  
✅ Logic scaling phức tạp  
✅ Tích hợp với custom metrics  

❌ Không nên dùng nếu:
- Chỉ cần scaling đơn giản
- Lần đầu setup Auto Scaling
- Muốn scaling tự động hoàn toàn

---

#### Bước 4.1 – Tạo CloudWatch Alarm
1. Vào **Services → CloudWatch**  
![Auto Scaling ](/images/5/36.png?featherlight=false&width=90pc)

2. Click **Alarms** (menu trái) → **Create alarm**
![Auto Scaling ](/images/5/37.png?featherlight=false&width=90pc)

3. **Chọn metric**:
![Auto Scaling ](/images/5/38.png?featherlight=false&width=90pc)
- Chọn EC2
![Auto Scaling ](/images/5/39.png?featherlight=false&width=90pc)

- Chọn By Auto Scaling Group
![Auto Scaling ](/images/5/40.png?featherlight=false&width=90pc)
- Chọn Web-app-asg
   ![Auto Scaling ](/images/5/41.png?featherlight=false&width=90pc)



4. **Cấu hình điều kiện**:
   - Statistic: Average  
   - Period: 5 minutes
   ![Auto Scaling ](/images/5/42.png?featherlight=false&width=90pc)

   - Threshold type: Static  
   - Điều kiện: `CPUUtilization > 80`
   ![Auto Scaling ](/images/5/43.png?featherlight=false&width=90pc)

5. **Hành động** (tùy chọn):
   - Alarm state: In alarm  
   - Gửi thông báo qua SNS (nếu muốn)
   ![Auto Scaling ](/images/5/44.png?featherlight=false&width=90pc)

   - Nhấn Next
   ![Auto Scaling ](/images/5/45.png?featherlight=false&width=90pc)


6. **Tên**: `High-CPU-Alarm-ASG`  
   **Mô tả**: Báo khi CPU > 80% cho ASG  
   ![Auto Scaling ](/images/5/46.png?featherlight=false&width=90pc)

7. Xem lại → **Create alarm**
   ![Auto Scaling ](/images/5/47.png?featherlight=false&width=90pc)
   ![Auto Scaling ](/images/5/48.png?featherlight=false&width=90pc)
   ![Auto Scaling ](/images/5/49.png?featherlight=false&width=90pc)


---

#### Tạo Step Scaling Policy
1. Vào **Auto Scaling Groups** → chọn ASG

2. Click tab **Automatic scaling**
3. **Tạo dynamic scaling policy**:
   ![Auto Scaling ](/images/5/50.png?featherlight=false&width=90pc)

   - Policy type: **Step scaling**
   - Policy name: `Scale-Out-Step-Policy`
   - CloudWatch alarm: `High-CPU-Alarm-ASG`

4. **Scaling adjustment**:
   - Action: Add
5. **Step adjustments**:
   - **Bước 1:**  
     Lower bound: 0 → Upper bound: 80
6. **Instance warmup:** 300 giây
7. **Tạo policy**
   ![Auto Scaling ](/images/5/51.png?featherlight=false&width=90pc)


---

## ✅ Kiểm tra kết quả
- Tab **Automatic scaling** trong ASG → thấy các policies vừa tạo  
   ![Auto Scaling ](/images/5/52.png?featherlight=false&width=90pc)

- Tab **Activity** → theo dõi sự kiện scaling  
- **CloudWatch → Alarms** → xem trạng thái alarm

---

## 💡 Ghi chú:
- Instance warmup giúp instance mới sẵn sàng trước khi nhận traffic
- Step scaling cho phép điều chỉnh linh hoạt hơn so với target tracking
- Có thể test bằng cách **tăng CPU load thủ công**