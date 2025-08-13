---
title : "Create Cost Budget"

weight : 3
chapter : false
pre : " <b> 3.1 </b> "
---

## 1. Sign in to AWS Console
- Go to **https://console.aws.amazon.com**.
- Search for **Budgets** in the search bar and select it.
![Create Cost Budget](/images/3/01.png?featherlight=false&width=90pc)

## 2. Create a New Budget
- Click **Create budget**.
![Create Cost Budget](/images/3/02.png?featherlight=false&width=90pc)
- Select **Customize(advanced)** → Click **Cost budget - recommended**→ Click **Next**.
![Create Cost Budget](/images/3/04.png?featherlight=false&width=90pc)
> Cost budgets are the most common type for controlling AWS spending.

## 3. Set Budget Details
- **Budget name**:  `Cost-budgets`
- **Period**: Choose Monthly, Quarterly, or Annually.
![Create Cost Budget](/images/3/05.png?featherlight=false&width=90pc)
- **Budgeted amount**: e.g., `50 USD`
- Click **Next**.  
![Create Cost Budget](/images/3/06.png?featherlight=false&width=90pc)
> The period determines how often the budget resets.

## 4. Configure Notifications
- Add **Notification**.
![Create Cost Budget](/images/3/07.png?featherlight=false&width=90pc)
- Set **Threshold** (e.g., 80% of budget).
- Enter **Email** to receive alerts.
- Click **Next**.
![Create Cost Budget](/images/3/08.png?featherlight=false&width=90pc)

> Notifications help you avoid overspending.

## 5. Review and Create
- Review your settings.
- Click **Create budget**.
![Create Cost Budget](/images/3/09.png?featherlight=false&width=90pc)