---
title : "Thêm nhiều mức cảnh báo"

weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---

### 📊 Thêm nhiều mức cảnh báo cho AWS Budget

#### 📝 Mục tiêu
Thiết lập 2 mức cảnh báo:
- **Alert #1**: 80% ngân sách
- **Alert #2**: 100% ngân sách

---

#### Truy cập Budget Management
1. Đăng nhập **AWS Management Console**.
2. Điều hướng: **Billing and Cost Management** → **Budgets**.
3. Click vào budget đã tạo (ví dụ: `Cost-budgets`).
![imple Notification Service](/images/3/48.png?featherlight=false&width=90pc)


---

### Thêm cấu hình cảnh báo
#### Tạo cảnh báo mới
1. Trong **Budget details**, chọn tab **Alerts**.

2. Click **Edit alerts** (góc phải màn hình).
![imple Notification Service](/images/3/49.png?featherlight=false&width=90pc)

3. Click **Add alert threshold**.
![imple Notification Service](/images/3/50.png?featherlight=false&width=90pc)


#### Cấu hình Alert #2 (100%)
- Nhập cấu hình:
   - **Threshold**: `100`
   - **Type**: `% of budgeted amount`
   - **Trigger**: `Actual`
   - **Email recipients**: Ví dụ `xxxxxxxx@mail.com`
![imple Notification Service](/images/3/51.png?featherlight=false&width=90pc)



💡 **Tip**:  
- **Actual**: dựa trên chi phí thực tế.  
- **Forecasted**: dựa trên dự đoán (giúp cảnh báo sớm).  
- Bạn có thể gửi đến nhiều email bằng dấu phẩy (`,`) để phân tán thông báo.

---

#### Review và Save
1. Kiểm tra lại cấu hình:
   - **Alert #1**: 80% threshold
   - **Alert #2**: 100% threshold

![imple Notification Service](/images/3/52.png?featherlight=false&width=90pc)
2. Click **Next** → **Save**.
![imple Notification Service](/images/3/53.png?featherlight=false&width=90pc)


---

#### 📬 Kết quả
- Nhận email khi **cost đạt 80%** ngân sách (VD: $40 nếu budget $50).
- Nhận email khác khi **cost đạt 100%** ngân sách.
- Có thể thêm **Budget Actions** để tự động thực hiện (VD: stop EC2 instances).

⚠ **Lưu ý**: Email cảnh báo có thể mất vài phút để gửi sau khi vượt ngưỡng.
