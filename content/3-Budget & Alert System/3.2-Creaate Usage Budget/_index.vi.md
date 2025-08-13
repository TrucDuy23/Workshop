---
title : "Tạo Usage Budget"

weight : 3
chapter : false
pre : " <b> 3.2 </b> "
---


##  Tổng quan
Trong phần này, bạn sẽ thực hành tạo **Usage Budget** – công cụ giúp bạn theo dõi và kiểm soát mức sử dụng tài nguyên AWS.  

ℹ️ **Lưu ý:** Nếu bạn đã tạo **Cost Budget**, quy trình rất giống nhau.  
- **Cost Budget** → dựa trên **chi phí**.  
- **Usage Budget** → dựa trên **mức sử dụng tài nguyên** (ví dụ: số giờ EC2, dung lượng S3 GB).  

---

#### Truy cập tạo Budget
1. Đăng nhập **AWS Management Console**.  
2. Ở thanh tìm kiếm, nhập **Billing** và chọn **Billing and Cost Management**.  
3. Trong menu bên trái, chọn **Budgets**.  
4. Nhấn **Create budget**.  
![Create Cost Budget](/images/3/12.png?featherlight=false&width=90pc)
---


#### Chọn loại Budget
1. Ở mục **Budget setup**, chọn **Customize**.  
2. Trong **Budget types**, chọn **Usage budget**.  
3. Nhấn **Next**. 
![Create Cost Budget](/images/3/13.png?featherlight=false&width=90pc)


---

#### Thiết lập chi tiết Budget
1. Trong **Set your budget**:  
   - **Budget name** → đặt tên mô tả (ví dụ: `Usage-Budget`).  
2. Ở **Usage type**:  
   - Chọn **Usage type groups**.  
   - Chọn **EC2:Running Hours** để theo dõi số giờ chạy của EC2 instances.  
![Create Cost Budget](/images/3/14.png?featherlight=false&width=90pc)
3. Trong **Set budget amount**:  
   - **Period** → Hàng ngày, Hàng tháng, Hàng quý, hoặc Hàng năm.  
   - **Budget renewal type** → Lặp lại hoặc Hết hạn.  
   - **Budgeting method** → Cố định hoặc Lập kế hoạch.  
   - Nhập **số giờ sử dụng tối đa** muốn giới hạn.  
![Create Cost Budget](/images/3/15.png?featherlight=false&width=90pc)

4. Giữ nguyên **Budget scope** mặc định và nhấn **Next**.  
![Create Cost Budget](/images/3/16.png?featherlight=false&width=90pc)

---
#### Thiết lập cảnh báo
1. Trong **Configure alerts**, chọn **Add an alert threshold**.  
![Create Cost Budget](/images/3/17.png?featherlight=false&width=90pc)

2. Thiết lập **ngưỡng cảnh báo** (ví dụ: 80% ngân sách).  

3. Thêm một hoặc nhiều **địa chỉ email** để nhận thông báo.  
4. Nhấn **Next**.  
![Create Cost Budget](/images/3/18.png?featherlight=false&width=90pc)


---
#### Xem lại & Tạo Budget
1. Kiểm tra lại toàn bộ cấu hình.  
![Create Cost Budget](/images/3/19.png?featherlight=false&width=90pc)

2. Nhấn **Create budget**.  
![Create Cost Budget](/images/3/20.png?featherlight=false&width=90pc)

---

#### Theo dõi & Quản lý
- Sau khi tạo, bạn sẽ thấy ngân sách trong danh sách.   
![Create Cost Budget](/images/3/21.png?featherlight=false&width=90pc)


---

💡 **Mẹo:**  
- Sử dụng Usage Budget cho các dịch vụ tính phí theo đơn vị sử dụng (ví dụ: EC2 hours, S3 GB-month) để tránh vượt quá mức dự kiến.  

🔒 **Lưu ý bảo mật:**  
- Chỉ những người quản lý chi phí được ủy quyền mới nên nhận thông báo để tránh lộ thông tin tài chính.
