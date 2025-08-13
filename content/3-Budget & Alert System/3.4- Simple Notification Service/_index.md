---
title : "Simple Notification Service"

weight : 3
chapter : false
pre : " <b> 3.4 </b> "
---

### 📢 Setting up SNS Topic for AWS Budget Alerts

#### 📝 Objective
In this section, you will:
- Create an **SNS Topic** to send alerts when budgets exceed thresholds.
- Subscribe an email to receive alerts.
- Test sending a notification.
- (Optional) Integrate with AWS Budget.

---

#### Create SNS Topic
1. Log in to **AWS Management Console**.
2. Search for "SNS" → Select **Simple Notification Service**.
![imple Notification Service](/images/3/23.png?featherlight=false&width=90pc)
3. Click **Create topic**.
4. Click **Topic Name**: `MySNS`
![imple Notification Service](/images/3/24.png?featherlight=false&width=90pc)
5. Configure:
   - **Type**: `Standard`
   - **Name**: `MySNS`
   - **Display name**: `Budget Alerts`
   ![imple Notification Service](/images/3/25.png?featherlight=false&width=90pc)
6. Click **Create topic**.
   ![imple Notification Service](/images/3/26.png?featherlight=false&width=90pc)

---

#### Create Subscription for the Topic
1. After the topic is created, click **Create subscription**.
   ![imple Notification Service](/images/3/27.png?featherlight=false&width=90pc)

2. Configure:
   - **Topic ARN**: (auto-filled, e.g., `arn:aws:sns:ap-southeast-1:886149544526:MySNS`)
   - **Protocol**: `Email`
   - **Endpoint**: The recipient email address (e.g., `duypt6123@gmail.com`)
3. Click **Create subscription**.
   ![imple Notification Service](/images/3/28.png?featherlight=false&width=90pc)
   ![imple Notification Service](/images/3/29.png?featherlight=false&width=90pc)



---

#### Confirm Email Subscription
1. Check the email inbox you used for subscription.
2. Find the confirmation email from AWS.
3. Click **Confirm subscription** in the email.
   ![imple Notification Service](/images/3/30.png?featherlight=false&width=90pc)

4. Once confirmed, the status in AWS Console will display **Confirmed**.
   ![imple Notification Service](/images/3/31.png?featherlight=false&width=90pc)
   ![imple Notification Service](/images/3/32.png?featherlight=false&width=90pc)

---

#### Test Sending a Message
1. Open the `MySNS` topic.
2. Click **Publish message**.
   ![imple Notification Service](/images/3/36.png?featherlight=false&width=90pc)
Configure:
   - **Subject**: `test message from sns`
   - **Message body**: `test sns`
   - **Message group ID**: `35bad533-6199-469b-af15-412400fe77a6`
4. Click **Publish message**.
   ![imple Notification Service](/images/3/38.png?featherlight=false&width=90pc)
   ![imple Notification Service](/images/3/37.png?featherlight=false&width=90pc)



---

#### Verify the Result
- The test message is delivered to the subscribed email.
- AWS Console shows successful delivery status.

   ![imple Notification Service](/images/3/39.png?featherlight=false&width=90pc)



---

#### Tích hợp với AWS Budget
1. Go to **Billing and Cost Management** → **Budgets**→ **Usage-Budget**.
      ![imple Notification Service](/images/3/41.png?featherlight=false&width=90pc)

2. Create or edit a budget (e.g., `Usage-Budget`).
      ![imple Notification Service](/images/3/42.png?featherlight=false&width=90pc)
      - Chọn next
      ![imple Notification Service](/images/3/43.png?featherlight=false&width=90pc)

3. In the **SNS Alerts** section, add the **SNS topic ARN** you created.
      ![imple Notification Service](/images/3/44.png?featherlight=false&width=90pc)
      ![imple Notification Service](/images/3/45.png?featherlight=false&width=90pc)

4. Check all configuration again.
      ![imple Notification Service](/images/3/46.png?featherlight=false&width=90pc)
      - Nhấn Save
      ![imple Notification Service](/images/3/47.png?featherlight=false&width=90pc)
      


💡 **Tip**:  
- One SNS topic can be linked to multiple budgets.
- Combine with **Cost Anomaly Detection** for earlier alerts.