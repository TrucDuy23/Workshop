---
title : "Resource Tagging Strategy"

weight : 5
chapter : false
pre : " <b> 5.2 </b> "
---

---

### 1. Open Tag Editor (Resource Groups & Tag Editor)
1. In AWS Console search **Resource Groups & Tag Editor** (or Resource Groups → Tag Editor).  
2. Open **Tag Editor**.
![Enable Detailed Billing Reports](/images/5/01.png?featherlight=false&width=90pc)

---

### 2. Select Regions & Resource Types
1. Under **Regions**: choose **All regions** (or select specific regions).  
![Enable Detailed Billing Reports](/images/5/02.png?featherlight=false&width=90pc)

![Enable Detailed Billing Reports](/images/5/03.png?featherlight=false&width=90pc)

2. Under **Resource types**: select **All supported resource types** or specific types (e.g., `AWS::EC2::Instance`).   
![Enable Detailed Billing Reports](/images/5/04.png?featherlight=false&width=90pc)

   - Tip: use All regions + All resource types to scan the whole account.

---

### 3. (Optional) Filter by existing tags
- To target specific resources, enter **Tag key** and optional **Tag value**, then click **Add**.



---
### 4. Search and select resources
1. Click **Search resources**.  
![Enable Detailed Billing Reports](/images/5/05.png?featherlight=false&width=90pc)

2. The results list appears (up to 500 resources returned).  
3. Select resources you want to tag (tick boxes).  
4. Click **Manage tags of selected resources**.
![Enable Detailed Billing Reports](/images/5/08.png?featherlight=false&width=90pc)


---

### 5. Add / Edit tags on resources
1. In the Manage tags dialog, enter **Tag key** and **Tag value** (e.g., `Project = ClothingWeb`, `Environment = Prod`).  
2. Click **Add** for each pair.  
3. Review tags to apply → click **Save** (or **Apply**).  
4. Confirm tags appear in the resource list under the **Tags** column.

**Note:** This updates resource metadata directly — be careful when changing tags used by automation.

---

### 6. Activate Cost Allocation Tags (Billing)
1. Go to **AWS Console** → **Billing** → **Cost Allocation Tags**.  
2. There are two tabs:
   - **User-defined cost allocation tags**
   - **AWS generated cost allocation tags**
![Enable Detailed Billing Reports](/images/5/09.png?featherlight=false&width=90pc)

3. Check/select the tag keys you want to use for cost allocation (e.g., `Project`, `Environment`, or `aws:*` tags).  

![Enable Detailed Billing Reports](/images/5/10.png?featherlight=false&width=90pc)
4. Click **Activate** and confirm in the popup.
![Enable Detailed Billing Reports](/images/5/11.png?featherlight=false&width=90pc)



---

### 7. After Activation
- Tags will turn **Active**. It can take several hours (sometimes up to ~24 hours) for tag data to appear in Cost Explorer / CUR.  
- Use **Backfill tags** if you want to apply tag data to historical records (optional).  
- You can **Download CSV** of tag keys for auditing.
![Enable Detailed Billing Reports](/images/5/12.png?featherlight=false&width=90pc)

---

### 8. Verify in Cost Explorer / Reports
1. Open **Cost Explorer** and group/filter by the tag key (e.g., `Project`) to see cost breakdown by tags.  
2. If not immediately visible, wait a few hours and re-check.

---

### Best practices
- Define a clear tagging convention: e.g., `Project`, `Owner`, `Environment`, `CostCenter`.  
- Enforce tagging via **Tag Policies** (AWS Organizations) where possible.  
- Avoid sensitive data in tags.  
- Remember Tag Editor returns up to 500 resources per search—plan accordingly.  
- Validate IAM permissions before mass-tagging.

