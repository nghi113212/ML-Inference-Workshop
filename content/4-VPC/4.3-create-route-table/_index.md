---
title : "Create Route Table"
date : "2025-07-28"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Create route table
1. In **VPC dashboard**
    - Choose **Route tables** frpm the left-hand sidebar
    - Click on **Create route table**
    ![](/images/4.VPC/11.png)
2. In **Route table settings**
    - **Name:** `Route table-Private-1`
    - **VPC:** Choose **my-workshop-vpc**
    - Click **Create route table**
    ![](/images/4.VPC/12.png)

3. Confirm creation
    - Successful
    ![](/images/4.VPC/13.png)

4. Repeat the same step for private route table 2
    - **Name:** `Route table-Private-2`
    - **VPC:** Choose **my-workshop-vpc**
    - Click **Create route table**
    ![](/images/4.VPC/14.png)

5. Confirm creation
    - Successful
    ![](/images/4.VPC/15.png)

#### Associate with subnet

6. In **Route tables** dashboard
    - Select **Route table-Private-1**
    - Next, choose **Subnet associations** tab
    - In Explicit subnet associations, click **Edit subnet associations**
    ![](/images/4.VPC/16.png)

7. In **Edit subnet associations**
    - Select **Private Subnet 1**
    - Then, click **Save associations**
    ![](/images/4.VPC/17.png)

8. Do the same for Route table-Private-2
    - Select **Route table-Private-2**
    ![](/images/4.VPC/18.png)
    ![](/images/4.VPC/19.png)