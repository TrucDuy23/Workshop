---
title : "Clean Up Resources"

weight : 6
chapter : false
pre : " <b> 6. </b> "
---

### AWS Budgets Cleanup 
---

### AWS Budgets Cleanup**

### 1. Purpose
Remove lab-created AWS Budgets to:
- Keep account tidy  
- Stop unwanted alerts  
- Avoid confusion

---

### 2. Steps
1. **Open Budgets**  
   AWS Console → Search **Billing and Cost Management** → **Budgets**
2. **Select Budget**  
   Tick checkbox → Click **Delete**
![Clean Up Resources ](/images/6/01.png?featherlight=false&width=90pc)

3. **Confirm Deletion**  
   Review name → **Confirm**

4. **Repeat** for all lab budgets
![Clean Up Resources ](/images/6/02.png?featherlight=false&width=90pc)

---

### 3. Tips & Warnings
💡 Export data before deleting production budgets.  
⚠️ Deletion is permanent – check before confirming.

---

### 4. Verify
Refresh **Budgets** page → No lab budgets remain.


## Simple Notification Service

#### Step 2: Delete Topics

1. Go to **SNS** → **Topics**
2. Select the topic to delete
3. Click **Delete** button
![Clean Up Resources](/images/6/03.png?featherlight=false&width=90pc)

4. Type exactly `delete me` in the confirmation field
5. Click **Delete** to complete
![Clean Up Resources](/images/6/04.png?featherlight=false&width=90pc)

#### Step 1: Delete Subscriptions

1. Go to **AWS Console** → **SNS** → **Subscriptions**
2. Select the subscription to delete
3. Click **Delete** button
4. Confirm deletion in the dialog box
![Clean Up Resources](/images/6/05.png?featherlight=false&width=90pc)


### ** Delete CloudWatch Alarms**
1. Go to **CloudWatch → Alarms**
2. Select alarms related to your Auto Scaling Group
3. **Actions → Delete** → Confirm deletion
![Clean Up Resources](/images/6/10.png?featherlight=false&width=90pc)

---

### ** Delete Auto Scaling Groups**
1. Go to **EC2 → Auto Scaling Groups**
2. Select target group → **Actions → Delete**
![Clean Up Resources](/images/6/08.png?featherlight=false&width=90pc)

3. ⚠️ **Warning**: All running instances will be terminated  
4. Type `delete` to confirm
![Clean Up Resources](/images/6/09.png?featherlight=false&width=90pc)


---

### ** Delete Launch Templates**
1. Go to **EC2 → Launch Templates**
2. Select template → **Actions → Delete template**
3. Confirm deletion
![Clean Up Resources](/images/6/07.png?featherlight=false&width=90pc)

---

💡 **Tip**: Always verify that no production resources are linked before deletion.