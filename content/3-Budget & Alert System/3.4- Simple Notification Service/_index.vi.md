---
title : "Simple Notification Service"

weight : 3
chapter : false
pre : " <b> 3.4 </b> "
---

### 📢 Thiết lập SNS Topic cho AWS Budget Alerts

#### 📝 Mục tiêu
Trong phần này, bạn sẽ:
- Tạo một **SNS Topic** để gửi thông báo khi ngân sách vượt ngưỡng.
- Đăng ký email nhận thông báo.
- Kiểm tra thử gửi tin nhắn.
- (Tùy chọn) Tích hợp với AWS Budget.

---

#### Tạo SNS Topic
1. Đăng nhập **AWS Management Console**.
2. Tìm kiếm "SNS" → Chọn **Simple Notification Service**.
![imple Notification Service](/images/3/23.png?featherlight=false&width=90pc)
3. Nhấn **Create topic**.
4. Nhập **Topic Name**: `MySNS`
![imple Notification Service](/images/3/24.png?featherlight=false&width=90pc)
5. Cấu hình:
   - **Type**: `Standard`
   - **Name**: `MySNS`
   - **Display name**: `Budget Alerts`
   ![imple Notification Service](/images/3/25.png?featherlight=false&width=90pc)
6. Nhấn **Create topic**.
   ![imple Notification Service](/images/3/26.png?featherlight=false&width=90pc)

---

#### Tạo Subscription cho Topic
1. Sau khi tạo topic thành công, nhấn **Create subscription**.
   ![imple Notification Service](/images/3/27.png?featherlight=false&width=90pc)

2. Cấu hình:
   - **Topic ARN**: (được tự động điền, ví dụ: `arn:aws:sns:ap-southeast-1:886149544526:MySNS`)
   - **Protocol**: `Email`
   - **Endpoint**: Địa chỉ email nhận thông báo (ví dụ: `duypt6123@gmail.com`)
3. Nhấn **Create subscription**.
   ![imple Notification Service](/images/3/28.png?featherlight=false&width=90pc)
   ![imple Notification Service](/images/3/29.png?featherlight=false&width=90pc)



---

#### Xác nhận Email Subscription
1. Mở email vừa đăng ký.

2. Tìm email xác nhận từ AWS.
3. Nhấn **Confirm subscription** trong email.
   ![imple Notification Service](/images/3/30.png?featherlight=false&width=90pc)

4. Sau khi xác nhận thành công, trạng thái trong AWS Console sẽ hiển thị **Confirmed**.
   ![imple Notification Service](/images/3/31.png?featherlight=false&width=90pc)
   ![imple Notification Service](/images/3/32.png?featherlight=false&width=90pc)

---

#### Test gửi tin nhắn
1. Mở topic `MySNS`.
2. Nhấn **Publish message**.
   ![imple Notification Service](/images/3/36.png?featherlight=false&width=90pc)
3. Cấu hình:
   - **Subject**: `test message from sns`
   - **Message body**: `test sns`
   - **Message group ID**: `35bad533-6199-469b-af15-412400fe77a6`
4. Nhấn **Publish message**.
   ![imple Notification Service](/images/3/38.png?featherlight=false&width=90pc)
   ![imple Notification Service](/images/3/37.png?featherlight=false&width=90pc)



---

#### Kiểm tra kết quả
- Email nhận được tin nhắn test.
- Trạng thái gửi hiển thị thành công trong AWS Console.
   ![imple Notification Service](/images/3/39.png?featherlight=false&width=90pc)



---

#### Tích hợp với AWS Budget
1. Vào **Billing and Cost Management** → **Budgets**→ **Usage-Budget**.
      ![imple Notification Service](/images/3/41.png?featherlight=false&width=90pc)

2. Chỉnh sửa budget (ví dụ: `Usage-Budget`).
      ![imple Notification Service](/images/3/42.png?featherlight=false&width=90pc)
      - Chọn next
      ![imple Notification Service](/images/3/43.png?featherlight=false&width=90pc)

3. Trong mục **SNS Alerts**, thêm **SNS topic ARN** vừa tạo.
      ![imple Notification Service](/images/3/44.png?featherlight=false&width=90pc)
      ![imple Notification Service](/images/3/45.png?featherlight=false&width=90pc)

4.  Kiểm tra lại toàn bộ cấu hình.  
      ![imple Notification Service](/images/3/46.png?featherlight=false&width=90pc)
      - Nhấn Save
      ![imple Notification Service](/images/3/47.png?featherlight=false&width=90pc)
      

💡 **Tip**:  
- Có thể dùng chung một SNS topic cho nhiều Budget.
- Kết hợp với **Cost Anomaly Detection** để nhận cảnh báo sớm hơn.