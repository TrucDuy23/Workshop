---
title : "Set Time Ranges and Grouping"

weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

1. **Select Time Range:**  
![time ranges và grouping](/images/1/006.png?featherlight=false&width=90pc)
   - **Last 3 months / 6 months:** Useful for spotting recent spending trends.  
   - **Custom:** Choose a specific period to analyze deployment phases, campaigns, or troubleshooting windows.  
   ![time ranges và grouping](/images/1/007.png?featherlight=false&width=90pc)

2. **Granularity:**  
   - **Daily:** See day-by-day spending – great for spotting short-term cost spikes.  
   - **Monthly:** Best for long-term trend analysis and budget planning.  
   - **Hourly:** Ideal for hourly-billed services (like EC2) and investigating sudden cost surges.  
   ![time ranges và grouping](/images/1/008.png?featherlight=false&width=90pc)

3. **Group By:**  
   - **Service:** Break down costs by AWS services (EC2, S3, RDS…).  
   - **Region:** View costs by AWS region (us-east-1, ap-southeast-1…), useful for workload placement optimization.  
   - **Tag:** Use when **Cost Allocation Tags** are enabled to categorize spending by project, environment (dev, staging, prod), or team.  
   ![time ranges và grouping](/images/1/009.png?featherlight=false&width=90pc)

**💡 Tips:**  
- Combine **long Time Range + Monthly granularity** for big-picture trend forecasting.  
- Combine **short Time Range + Daily/Hourly granularity** to investigate sudden cost increases.  
- When using **Group by Tag**, ensure consistent tagging rules for accurate analysis (e.g., `Project=ClothingWeb`, `Environment=Prod`).  
- Always check **Region** for unexpected deployments in more expensive areas.