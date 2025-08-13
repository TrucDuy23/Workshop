---
title : "Bật Detailed Billing Reports (CUR)"

weight : 2
chapter : false
pre : " <b> 2.3 </b> "
---

**Mục tiêu:** Bật “Detailed billing reports (legacy)” và cấu hình 1 S3 bucket để AWS gửi báo cáo vào đó.

###  Mở Billing Preferences
1. Đăng nhập AWS Console → vào **Billing and Cost Management**.  
2. Ở menu trái chọn **Billing Preferences**.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/010.png?featherlight=false&width=90pc)
   
###  Bật Legacy report delivery to S3
1. Nhấn **Edit** (góc khung Detailed billing reports (legacy)).  
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/011.png?featherlight=false&width=90pc)
2. Tích chọn **Legacy report delivery to S3**.  
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/012.png?featherlight=false&width=90pc)
3. Nhấn link **Configure an S3 bucket to activate** (xuất hiện bên dưới khi bạn tích).
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/013.png?featherlight=false&width=90pc)

###  Configure S3 bucket (Modal Step 1: Select or create bucket)
1. Trong popup **Configure S3 Bucket**, chọn:
   - **Create a new S3 bucket** — nếu bạn chưa có bucket cho báo cáo, hoặc
   - **Use an existing S3 bucket** — nếu muốn dùng bucket hiện có.
2. Nếu tạo mới:
   - Nhập **S3 bucket name** (phải global-unique, không có dấu cách; ví dụ `billing-reports`).  
   - Chọn **Region** (chọn region phù hợp; lưu ý một số region có thể bị disable cho báo cáo).  
3. Nhấn **Next**.
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/014.png?featherlight=false&width=90pc)
**Lưu ý:** tên bucket phải là duy nhất trên toàn AWS. Không làm bucket public; để mặc định “Block public access”.
   
###  Verify policy (Modal Step 2)
1. AWS hiển thị **default policy** sẽ gán cho bucket (để `billingreports.amazonaws.com` có quyền ghi).  
2. Đọc nhanh policy (thường mặc định OK). Tích **I have confirmed that this policy is correct**.  
3. Nhấn **Save**.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/016.png?featherlight=false&width=90pc)

###  Hoàn tất cấu hình và kích hoạt báo cáo
1. Quay lại trang **Billing Preferences**, trạng thái bucket hiện **Valid bucket** (hoặc hiển thị số reports delivered).  
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/017.png?featherlight=false&width=90pc)
2. Nhấn **Update** để lưu thay đổi. Bạn sẽ thấy banner xanh báo “preferences were updated successfully”.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/018.png?featherlight=false&width=90pc)

   
###  Kích hoạt báo cáo bạn cần (Report activation)
1. Ở phần **Report activation**, tích chọn report bạn muốn (ví dụ **Monthly report**, **Cost allocation report**).  
2. Nhấn **Activate**. Trạng thái **Report delivery** sẽ chuyển sang **Activated** (vòng xanh).  
3. Sau khi báo cáo chạy, file sẽ được lưu vào S3 theo đường dẫn do AWS định nghĩa.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/020.png?featherlight=false&width=90pc)

   ## Tips
- **Bucket lifecycle:** đặt lifecycle rule tự xoá file cũ (vd giữ 365 ngày) để tiết kiệm S3 storage.  
- **Encryption:** bật SSE (S3 default encryption) nếu cần tuân thủ bảo mật.  
- **Không public:** tuyệt đối giữ bucket **Block public access**.  
- **Cross-account / Organizations:** nếu bạn dùng AWS Organizations, nên bật và cấu hình trên **payer/management account**. Nếu báo cáo cần ghi từ nhiều account, bucket policy phải cho phép billing service (và account payer) ghi.  
- **Nếu báo cáo không xuất hiện / lỗi 'invalid bucket':** vào S3 kiểm tra bucket policy và quyền; thử **Reverify** trên Billing Preferences.  
- **Tham khảo phân tích nâng cao:** kết nối CUR (Cost & Usage Report) với Athena / QuickSight để truy vấn chi tiết.
