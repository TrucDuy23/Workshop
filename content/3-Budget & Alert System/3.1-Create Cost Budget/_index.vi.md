---
title : "Tạo Cost Budget"

weight : 3
chapter : false
pre : " <b> 3.1 </b> "
---

## 1. Đăng nhập AWS Console
- Truy cập **https://console.aws.amazon.com**.
- Tìm **Budgets** trong thanh tìm kiếm và chọn.
![Create Cost Budget](/images/3/01.png?featherlight=false&width=90pc)

## 2. Tạo ngân sách mới
- Nhấn **Create budget**.
![Create Cost Budget](/images/3/02.png?featherlight=false&width=90pc)
- Chọn **Customize(advanced)** → Nhấn **Cost budget - recommended**→ Nhấn **Next**.
![Create Cost Budget](/images/3/04.png?featherlight=false&width=90pc)
> Loại ngân sách này phổ biến nhất để kiểm soát chi phí AWS.

## 3. Cài đặt chi tiết ngân sách
- **Budget name**:  `Cost-budgets`
- **Period**: Chọn Monthly, Quarterly, hoặc Annually.
![Create Cost Budget](/images/3/05.png?featherlight=false&width=90pc)
- **Budgeted amount**: e.g., `50 USD`
- Nhấn **Next**.  
![Create Cost Budget](/images/3/06.png?featherlight=false&width=90pc)
> Chu kỳ quyết định tần suất reset ngân sách.

## 4. Cấu hình thông báo
- Add **Notification**.
![Create Cost Budget](/images/3/07.png?featherlight=false&width=90pc)
- Cài **Threshold** (e.g., 80% of budget).
- Nhập **Email** Nhận cảnh báo.
- Nhấn **Next**.
![Create Cost Budget](/images/3/08.png?featherlight=false&width=90pc)

> Cảnh báo giúp tránh vượt quá ngân sách.

## 5. Review and Create
- Kiểm tra cấu hình.
- Nhấn **Create budget**.
![Create Cost Budget](/images/3/09.png?featherlight=false&width=90pc)