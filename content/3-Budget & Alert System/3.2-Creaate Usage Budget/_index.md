---
title : "Create Usage Budget"

weight : 3
chapter : false
pre : " <b> 3.2 </b> "
---

### 📝 Overview
In this section, you will practice creating a **Usage Budget** – a tool to monitor and control AWS resource usage.  
 

ℹ️ **Note:** If you have created a **Cost Budget**, the process is very similar.  
- **Cost Budget** → monitors based on **spending**.  
- **Usage Budget** → monitors based on **resource usage** (e.g., EC2 hours, S3 storage GB).  

---

#### Access Budget Creation
1. Sign in to **AWS Management Console**.  
2. In the search bar, type **Billing** and select **Billing and Cost Management**.  
3. From the left menu, click **Budgets**.  
4. Click **Create budget**.   
![Create Cost Budget](/images/3/12.png?featherlight=false&width=90pc)
---


#### Choose Budget Type
1. Under **Budget setup**, choose **Customize**.  
2. In **Budget types**, select **Usage budget**.  
3. Click **Next**.  
![Create Cost Budget](/images/3/13.png?featherlight=false&width=90pc)


---

#### Set Budget Details
1. In **Set your budget**:  
   - **Budget name** → enter a descriptive name (e.g., `Usage-budget`).  
2. Under **Usage type**:  
   - Select **Usage type groups**.  
   - Choose **EC2:Running Hours** to track EC2 instance running hours. 
![Create Cost Budget](/images/3/14.png?featherlight=false&width=90pc)
3. Under **Set budget amount**:  
   - **Period** → Daily, Monthly, Quarterly, or Annually.  
   - **Budget renewal type** → Recurring or Expiring.  
   - **Budgeting method** → Fixed or Planned.  
   - Enter the **maximum usage hours** you want to allow.  
![Create Cost Budget](/images/3/15.png?featherlight=false&width=90pc)

4. Leave **Budget scope** as default and click **Next**.  
![Create Cost Budget](/images/3/16.png?featherlight=false&width=90pc)

---
#### Configure Alerts
1. In **Configure alerts**, click **Add an alert threshold**.  
![Create Cost Budget](/images/3/17.png?featherlight=false&width=90pc)
2. Set **alert threshold** (e.g., 80% of the budget).  
3. Add one or more **email addresses** to receive notifications.  
4. Click **Next**.    
![Create Cost Budget](/images/3/18.png?featherlight=false&width=90pc)


---
#### Review & Create Budget
1. Review all settings.  
![Create Cost Budget](/images/3/19.png?featherlight=false&width=90pc)
2. Click **Create budget**.  
![Create Cost Budget](/images/3/20.png?featherlight=false&width=90pc)

---

#### Monitor & Manage
- After creation, the budget will appear in the list.  
![Create Cost Budget](/images/3/21.png?featherlight=false&width=90pc)


---

💡 **Pro Tip:**  
- Use Usage Budgets for services billed per usage unit (e.g., EC2 hours, S3 GB-month) to prevent unexpected overuse.  

🔒 **Security Note:**  
- Only authorized cost managers should receive budget alerts to avoid exposing sensitive financial data.