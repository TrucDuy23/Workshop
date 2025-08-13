---
title : "Thiết lập Time Ranges và Grouping"

weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

1. **Chọn Time Range (Khoảng thời gian):**  
    ![time ranges và grouping](/images/1/006.png?featherlight=false&width=90pc)
   - **Last 3 months / 6 months:** Dùng khi cần xem xu hướng chi phí gần đây.  
   - **Custom:** Chọn khoảng thời gian cụ thể để phân tích giai đoạn triển khai, chạy chiến dịch, hoặc xử lý sự cố.  
   ![time ranges và grouping](/images/1/007.png?featherlight=false&width=90pc)

2. **Granularity (Độ chi tiết dữ liệu):**  
   - **Daily:** Xem chi phí từng ngày – hữu ích để phát hiện đột biến chi phí trong ngắn hạn.  
   - **Monthly:** Dùng để phân tích xu hướng dài hạn, tổng quan ngân sách.  
   - **Hourly:** Thường áp dụng cho dịch vụ tính phí theo giờ như EC2, phù hợp để debug khi có spike chi phí bất thường.  
   ![time ranges và grouping](/images/1/008.png?featherlight=false&width=90pc)

3. **Group By (Nhóm dữ liệu):**  
   - **Service:** Xem chi phí theo từng dịch vụ AWS (EC2, S3, RDS…).  
   - **Region:** Phân tích chi phí theo khu vực (us-east-1, ap-southeast-1…), giúp tối ưu khi cần chuyển workload sang region rẻ hơn.  
   - **Tag:** Sử dụng khi đã bật **Cost Allocation Tags** để phân loại chi phí theo dự án, môi trường (dev, staging, prod) hoặc team.  
   ![time ranges và grouping](/images/1/009.png?featherlight=false&width=90pc)

**💡 Tips:**  
- Kết hợp **Time Range dài + Granularity Monthly** để xem xu hướng dài hạn và dự đoán chi phí.  
- Kết hợp **Time Range ngắn + Granularity Daily/Hourly** khi điều tra chi phí tăng đột ngột.  
- Khi dùng **Group by Tag**, nên đặt quy tắc đặt tag thống nhất để phân tích chính xác (VD: `Project=ClothingWeb`, `Environment=Prod`).  
- Luôn kiểm tra **Region** nếu có dịch vụ bị triển khai ngoài ý muốn ở khu vực khác (chi phí có thể cao hơn).  
