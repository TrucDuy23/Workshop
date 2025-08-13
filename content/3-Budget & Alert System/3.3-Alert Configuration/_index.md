---
title : "Multiple Alert"

weight : 3
chapter : false
pre : " <b> 3.3 </b> "
---

### 📊 Add Multiple Alert Levels for AWS Budget

#### 📝 Objective
Configure 2 alert levels:
- **Alert #1**: 80% of budget
- **Alert #2**: 100% of budget

---

#### Access Budget Management
1. Sign in to **AWS Management Console**.  
2. Navigate to: **Billing and Cost Management** → **Budgets**.  
3. Click on the budget you created (e.g., `Cost-budgets`).  
![imple Notification Service](/images/3/48.png?featherlight=false&width=90pc)

---

### Add Alert Configuration
#### Create a New Alert
1. In **Budget details**, go to the **Alerts** tab.  
2. Click **Edit alerts** (top right).  
![imple Notification Service](/images/3/49.png?featherlight=false&width=90pc)  
3. Click **Add alert threshold**.  
![imple Notification Service](/images/3/50.png?featherlight=false&width=90pc)

---

#### Configure Alert #2 (100%)
- Set the following:
   - **Threshold**: `100`
   - **Type**: `% of budgeted amount`
   - **Trigger**: `Actual`
   - **Email recipients**: Example `xxxxxxxx@mail.com`  
![imple Notification Service](/images/3/51.png?featherlight=false&width=90pc)

💡 **Tip**:  
- **Actual** = Based on actual spending.  
- **Forecasted** = Based on predicted spending (useful for early warnings).  
- Separate multiple emails with commas (`,`) to send alerts to multiple recipients.

---

#### Review and Save
1. Verify configuration:
   - **Alert #1**: 80% threshold  
   - **Alert #2**: 100% threshold  
![imple Notification Service](/images/3/52.png?featherlight=false&width=90pc)  
2. Click **Next** → **Save**.  
![imple Notification Service](/images/3/53.png?featherlight=false&width=90pc)

---

#### 📬 Results
- Receive an email when **cost reaches 80%** of the budget (e.g., $40 if the budget is $50).  
- Receive another email when **cost reaches 100%** of the budget.  
- Optionally, add **Budget Actions** to automatically take actions (e.g., stop EC2 instances).  

⚠ **Note**: Alert emails may take a few minutes to arrive after the threshold is exceeded.
