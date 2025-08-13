---
title : "Dọn Dẹp Tài nguyên"

weight : 6
chapter : false
pre : " <b> 6. </b> "
---


### ** Xóa AWS Budgets**

### 1. Mục đích
Xóa các budget tạo trong lab để:
- Dọn gọn tài khoản  
- Ngừng nhận cảnh báo không cần thiết  
- Tránh nhầm lẫn

---

### 2. Các bước
1. **Mở Budgets**  
   AWS Console → Tìm **Billing and Cost Management** → **Budgets**
2. **Chọn Budget**  
![Auto Scaling ](/images/6/01.png?featherlight=false&width=90pc)
   Tick checkbox → Click **Delete**
3. **Xác nhận**  
   Kiểm tra tên → **Confirm**

4. **Lặp lại** cho tất cả budget của lab
![Auto Scaling ](/images/6/02.png?featherlight=false&width=90pc)


---

### 3. Lưu ý
💡 Xuất dữ liệu trước khi xóa budget production.  
⚠️ Xóa là vĩnh viễn – kiểm tra kỹ trước khi xác nhận.

---

### 4. Kiểm tra
Refresh trang **Budgets** → Không còn budget của lab.

## Simple Notification Service
#### Xóa Topics 
1. Truy cập **SNS** → **Topics**
2. Chọn topic cần xóa
3. Nhấn nút **Delete**
![Auto Scaling ](/images/6/03.png?featherlight=false&width=90pc)

4. Nhập chính xác `delete me` vào ô xác nhận
5. Nhấn **Delete** để hoàn tất
![Auto Scaling ](/images/6/04.png?featherlight=false&width=90pc)

#### Xóa Subscriptions 
1. Truy cập **AWS Console** → **SNS** → **Subscriptions**
2. Chọn subscription cần xóa
3. Nhấn nút **Delete**
4. Xác nhận xóa trong hộp thoại
![Auto Scaling ](/images/6/05.png?featherlight=false&width=90pc)


#### ** Xóa CloudWatch Alarms**
1. Vào **CloudWatch → Alarms**
2. Chọn các alarm liên quan đến Auto Scaling Group
3. **Actions → Delete** → Xác nhận xóa
![Clean Up Resources](/images/6/10.png?featherlight=false&width=90pc)

---

#### ** Xóa Auto Scaling Groups**
1. Vào **EC2 → Auto Scaling Groups**
2. Chọn group → **Actions → Delete**
![Clean Up Resources](/images/6/08.png?featherlight=false&width=90pc)
3. ⚠️ **Cảnh báo**: Tất cả instance đang chạy sẽ bị xóa  
4. Gõ `delete` để xác nhận
![Clean Up Resources](/images/6/09.png?featherlight=false&width=90pc)


---
### ** Xóa Launch Templates**
1. Vào **EC2 → Launch Templates**
2. Chọn template → **Actions → Delete template**
3. Xác nhận xóa
![Clean Up Resources](/images/6/07.png?featherlight=false&width=90pc)

💡 **Mẹo**: Đảm bảo không còn tài nguyên production nào liên kết trước khi xóa.