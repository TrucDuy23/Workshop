---
title : "Enable Detailed Billing Reports (CUR)"

weight : 2
chapter : false
pre : " <b> 2.3 </b> "
---

**Goal:** Enable legacy Detailed Billing Reports and configure an S3 bucket to receive them.

###  Open Billing Preferences
- Console → **Billing and Cost Management** → **Billing Preferences**.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/010.png?featherlight=false&width=90pc)
   
###  Enable legacy delivery
- Click **Edit** under Detailed billing reports (legacy).  
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/011.png?featherlight=false&width=90pc)
- Check **Legacy report delivery to S3** → click **Configure an S3 bucket to activate**.
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/012.png?featherlight=false&width=90pc)
![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/013.png?featherlight=false&width=90pc)

###  Configure S3 bucket (Step 1)
- Choose **Create a new S3 bucket** or **Use an existing S3 bucket**.  
- If creating, enter a globally-unique **S3 bucket name**, choose **Region** → **Next**.

![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/014.png?featherlight=false&width=90pc)
**Note:** bucket names must be unique across AWS. Do not make buckets public; leave “Block public access” as default.
   
###  Verify policy (Step 2)
- Review the default bucket policy (allows `billingreports.amazonaws.com` write).  
- Check **I have confirmed that this policy is correct** → **Save**.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/016.png?featherlight=false&width=90pc)

###  Save & Update
- Back in Billing Preferences confirm **Valid bucket** → click **Update**.  
- You should see success banner.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/017.png?featherlight=false&width=90pc)
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/018.png?featherlight=false&width=90pc)

   
###  Activate reports
- Under **Report activation**, tick desired reports (Monthly, Cost allocation) → **Activate**.  
- Report delivery will show **Activated**; files delivered into S3.
   ![Enable Detailed Billing Reports](/WORKSHOP-PHAN-TRUC-DUY/images/1/020.png?featherlight=false&width=90pc)

   ### Quick tips
- Use lifecycle rules to expire old reports.  
- Keep bucket private and enable encryption.  
- For Organizations, configure from the payer/management account and allow cross-account writes if needed.  
- If problems, use **Reverify** or inspect S3 bucket policy.
