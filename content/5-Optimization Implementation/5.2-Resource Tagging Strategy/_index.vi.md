---
title : "Chiến lược Resource Tagging"

weight : 5
chapter : false
pre : " <b> 5.2 </b> "
---

---

### 1. Mở Tag Editor (Resource Groups & Tag Editor)
1. Vào AWS Console → tìm **Resource Groups & Tag Editor** (hoặc Resource Groups → Tag Editor).  
2. Mở **Tag Editor**.
![Enable Detailed Billing Reports](/images/5/01.png?featherlight=false&width=90pc)

---

### 2. Chọn vùng & loại tài nguyên
1. Ở mục **Regions**: chọn **All regions** (hoặc chọn thủ công region cần thao tác).  
![Enable Detailed Billing Reports](/images/5/02.png?featherlight=false&width=90pc)

![Enable Detailed Billing Reports](/images/5/03.png?featherlight=false&width=90pc)

2. Ở **Resource types**: chọn **All supported resource types** hoặc chọn loại cụ thể (VD: `AWS::EC2::Instance`).  
![Enable Detailed Billing Reports](/images/5/04.png?featherlight=false&width=90pc)

   - Gợi ý: thường chọn "All regions" + "All resource types" nếu bạn muốn quét toàn bộ tài khoản.

---

### 3. (Tùy chọn) Lọc theo tag hiện có
- Nếu muốn chỉ chọn các tài nguyên có/không có tag nhất định: nhập **Tag key** và (tùy chọn) **Tag value**, rồi click **Add**.


---

### 4. Tìm và chọn tài nguyên
1. Nhấn **Search resources**.  
![Enable Detailed Billing Reports](/images/5/05.png?featherlight=false&width=90pc)

2. Danh sách kết quả hiện ra (tối đa 500 resource / lần).  
3. Chọn những resource bạn muốn gán/sửa tag (tick chọn từng item hoặc chọn nhiều).  
4. Nhấn **Manage tags of selected resources**.
![Enable Detailed Billing Reports](/images/5/08.png?featherlight=false&width=90pc)


---

### 5. Gán / sửa tag cho resource
1. Trong dialog **Manage tags**, nhập **Tag key** và **Tag value** (ví dụ `Project = ClothingWeb`, `Environment = Prod`).  
2. Nhấn **Add** cho mỗi cặp key/value.  
3. Kiểm tra danh sách tag áp dụng → nhấn **Save** (hoặc **Apply**).  
4. Kiểm tra lại bảng resource: cột **Tags** sẽ hiển thị số tag gán.

**Lưu ý:** thao tác này thay đổi tag trực tiếp trên tài nguyên. Hãy cẩn thận với tag dùng cho automation hoặc billing.

---

### 6. Kích hoạt Cost Allocation Tags (Billing)
1. Vào **AWS Console** → **Billing** (Billing and Cost Management).  

2. Bên menu trái chọn **Cost Allocation Tags**.  
3. Có 2 tab:
   - **User-defined cost allocation tags** (tag do bạn tạo trên resource),
   - **AWS generated cost allocation tags** (tag do AWS tạo tự động cho 1 số dịch vụ).
![Enable Detailed Billing Reports](/images/5/09.png?featherlight=false&width=90pc)

4. Chọn/đánh dấu các tag muốn dùng làm **cost allocation** (ví dụ `Project`, `Environment` hoặc các `aws:*` tag).  
![Enable Detailed Billing Reports](/images/5/10.png?featherlight=false&width=90pc)

5. Nhấn **Activate**. Xác nhận trong popup → **Activate**.
![Enable Detailed Billing Reports](/images/5/11.png?featherlight=false&width=90pc)



---

### 7. Sau khi Activate
- AWS sẽ chuyển trạng thái tag sang **Active** (mất vài giờ — có thể lên đến ~24 giờ để dữ liệu xuất hiện đầy đủ trong Cost Explorer / CUR).  
- Nếu cần, nhấn **Backfill tags** (nếu có) để áp dụng dữ liệu tag cho dữ liệu lịch sử (tùy chọn có sẵn).  
- Bạn có thể **Download CSV** danh sách tag nếu muốn kiểm tra offline.
![Enable Detailed Billing Reports](/images/5/12.png?featherlight=false&width=90pc)

---

### 8. Kiểm tra trong Cost Explorer / báo cáo
1. Mở **Cost Explorer** → sử dụng filter hoặc group by theo tag key (ví dụ `Project`) để phân bổ chi phí theo tag.  
2. Nếu tag chưa xuất hiện, đợi vài giờ rồi thử lại.

---

### Best practices (mẹo)
- Thiết lập chuẩn **tagging convention**: `Project`, `Owner`, `Environment`, `CostCenter`, `BillingCode`.  
- Yêu cầu đặt tag bắt buộc cho resources mới (Tag Policies trong AWS Organizations).  
- Không dùng tag chứa thông tin nhạy cảm.  
- Dùng lifecycle rules và kiểm soát số lượng resource trả về khi dùng Tag Editor (limit 500).  
- Kiểm tra quyền IAM trước khi gán tag (tránh bị access denied).
