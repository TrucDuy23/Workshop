---
title : "Auto Scaling – Quản lý chi phí động"

weight : 5
chapter : false
pre : " <b> 5.1 </b> "
---


---

#### Access Auto Scaling Groups

**From AWS Console:**
1. Go to **Services → EC2**
2. In the EC2 dashboard, scroll the left-hand menu
3. Find the **AUTO SCALING** section
4. Click **Auto Scaling Groups**
![Auto Scaling ](/images/5/13.png?featherlight=false&width=90pc)

---

### Setup Auto Scaling Group (If Not Already Created)
![Auto Scaling ](/images/5/14.png?featherlight=false&width=90pc)

#### Create Launch Template
1. In the EC2 console, click **Launch Templates** (left menu)
2. Click **Create launch template**
![Auto Scaling ](/images/5/15.png?featherlight=false&width=90pc)

3. Configure:
   - **Name:** `web-app-template`
![Auto Scaling ](/images/5/16.png?featherlight=false&width=90pc)

   - **AMI:** Amazon Linux 2 (or an existing AMI)
![Auto Scaling ](/images/5/17.png?featherlight=false&width=90pc)

   - **Instance type:** `t2.micro`
![Auto Scaling ](/images/5/18.png?featherlight=false&width=90pc)

   - **Key pair:** your-key-pair
![Auto Scaling ](/images/5/19.png?featherlight=false&width=90pc)

4. Click **Create launch template**
![Auto Scaling ](/images/5/22.png?featherlight=false&width=90pc)


---

#### Create Auto Scaling Group
1. Go back to **Auto Scaling Groups**
2. Click **Create Auto Scaling group**
3. **Step 1 – Choose launch template:**
   - Name: `web-app-asg`
![Auto Scaling ](/images/5/23.png?featherlight=false&width=90pc)

      - Launch template: `web-app-template`
![Auto Scaling ](/images/5/24.png?featherlight=false&width=90pc)

4. **Network:**
   - VPC: Default (or custom)
   - Subnets: Select **2+ subnets** in different AZs
![Auto Scaling ](/images/5/25.png?featherlight=false&width=90pc)

5. **Step 3 – Load balancing** (optional):
   - Attach to existing ALB (if available)
![Auto Scaling ](/images/5/26.png?featherlight=false&width=90pc)

6. **Step 4 – Group size:**
   - Desired: `2`
   - Minimum: `1`
   - Maximum: `5`
![Auto Scaling ](/images/5/27.png?featherlight=false&width=90pc)
![Auto Scaling ](/images/5/28.png?featherlight=false&width=90pc)
    - SNS Topic: select the created sns topic
![Auto Scaling ](/images/5/29.png?featherlight=false&width=90pc)

7. **Review** và click **Create**
![Auto Scaling ](/images/5/30.png?featherlight=false&width=90pc)


---
### Configure Dynamic Scaling

####  Access Scaling Policies
1. From **Auto Scaling Groups** list, click the ASG name
2. ASG detail page opens with tabs:  
   **Details | Activity | Instance management | Monitoring | Automatic scaling**
3. Click **Automatic scaling** tab
![Auto Scaling ](/images/5/33.png?featherlight=false&width=90pc)



---

#### Create Target Tracking Policy
1. In **Automatic scaling** tab → **Dynamic scaling policies** section
2. Click **Create dynamic scaling policy**
![Auto Scaling ](/images/5/32.png?featherlight=false&width=90pc)
![Auto Scaling ](/images/5/34.png?featherlight=false&width=90pc)
![Auto Scaling ](/images/5/35.png?featherlight=false&width=90pc)

**Advanced Target Tracking Tips:**
- Disable scale-in if you only want to **scale out**
- Adjust **instance warmup** based on workload:
  - 300s (5 min): Standard web apps
  - 600s (10 min): Apps with long initialization
  - 120s (2 min): Lightweight apps
- Target values:
  - Web servers: **70% CPU**
  - Database: **60% CPU**
  - Background workers: **80% CPU**

---

### Advanced Scaling (Step Scaling)

**When to use Step Scaling:**
✅ Fine-grained control  
✅ Multiple scaling thresholds  
✅ Complex scaling logic  
✅ Integration with custom metrics  

❌ Avoid if:
- You only need simple scaling
- First time setting up Auto Scaling
- You prefer hands-off scaling

---

####  Create CloudWatch Alarm
1. Go to **Services → CloudWatch**  
![Auto Scaling ](/images/5/36.png?featherlight=false&width=90pc)

2. Click **Alarms** (left menu) → **Create alarm**
![Auto Scaling ](/images/5/37.png?featherlight=false&width=90pc)

3. **Select metric**:
![Auto Scaling ](/images/5/38.png?featherlight=false&width=90pc)
- Select EC2
![Auto Scaling ](/images/5/39.png?featherlight=false&width=90pc)

- Select By Auto Scaling Group
![Auto Scaling ](/images/5/40.png?featherlight=false&width=90pc)
- Select Web-app-asg
   ![Auto Scaling ](/images/5/41.png?featherlight=false&width=90pc)


4. **Set conditions**:
   - Statistic: Average  
   - Period: 5 minutes
   ![Auto Scaling ](/images/5/42.png?featherlight=false&width=90pc)

   - Threshold type: Static  
    - Condition: `CPUUtilization > 80`
   ![Auto Scaling ](/images/5/43.png?featherlight=false&width=90pc)
5. **Actions** (optional):
   - Alarm state: In alarm  
   - Send notification to SNS topic (optional)
   ![Auto Scaling ](/images/5/44.png?featherlight=false&width=90pc)

   - Click Next
   ![Auto Scaling ](/images/5/45.png?featherlight=false&width=90pc)

6. **Name**: `High-CPU-Alarm-ASG`  
   **Description**: Alarm when CPU > 80% for ASG  
   ![Auto Scaling ](/images/5/46.png?featherlight=false&width=90pc)

7. Review → **Create alarm**
   ![Auto Scaling ](/images/5/47.png?featherlight=false&width=90pc)
   ![Auto Scaling ](/images/5/48.png?featherlight=false&width=90pc)
   ![Auto Scaling ](/images/5/49.png?featherlight=false&width=90pc)


---

#### Create Step Scaling Policy
1. Go to **Auto Scaling Groups** → select your ASG
2. Click **Automatic scaling** tab
3. **Create dynamic scaling policy**:
   ![Auto Scaling ](/images/5/50.png?featherlight=false&width=90pc)

   - Policy type: **Step scaling**
   - Policy name: `Scale-Out-Step-Policy`
   - CloudWatch alarm: `High-CPU-Alarm-ASG`
4. **Scaling adjustment**:
   - Action: Add
   - Capacity units: Instances
5. **Step adjustments**:
   - **Step 1:**  
     Lower bound: 0 → Upper bound: 10  
     Scaling: +1 instance
   - **Step 2:**  
     Lower bound: 10 → Upper bound: ∞  
     Scaling: +2 instances
6. **Instance warmup:** 300 seconds
7. **Create policy**
   ![Auto Scaling ](/images/5/51.png?featherlight=false&width=90pc)


---

## ✅ Verification
- In ASG **Automatic scaling** tab → see policies  
   ![Auto Scaling ](/images/5/52.png?featherlight=false&width=90pc)

- In **Activity** tab → track scaling events  
- In **CloudWatch → Alarms** → check alarm status

---

## 💡 Notes:
- Instance warmup ensures the new instance is ready before receiving traffic
- Step scaling gives more granular control than target tracking
- You can test by **artificially increasing CPU load**