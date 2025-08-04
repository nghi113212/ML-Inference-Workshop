---
title : "Create Security Group"
date : "2025-07-28"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

1. In **VPC dashboard**
    - Select **Security groups** in the left-hand sidebar
    - Click **Create security group**
    ![](/images/4.VPC/20.png)

2. In **Basic details**
    - For **Security group name:** `lambda-sg`
    - For **Description:** `Security Group for Lambda functions accessing ElasticCache (Valkey) inside VPC`
    - **VPC:** Choose **my-workshop-vpc**
    - For **Tags**
        - Choose **Add new tag**
        - **Key:** Enter `Name`
        - **Value:** Enter `lambda-sg`
    - Then, click **Create security group**
    ![](/images/4.VPC/21.png)

3. Create a second security group for Valkey
    - Do the same steps as above
    - For **Security group name:** `valkey-sg`
    - For **Description:** `Allows inbound access from Lambda functions to ElasticCache (Valkey)`
    - **VPC:** Choose **my-workshop-vpc**
    - For **Inbound rules:**
        - Select **Add rule**
        - **Type:** Select **Custom TCP**
        - **Port range:** Enter `6379`
        - **Source:** Choose **Custom**, select **lambda-sg**
    - For **Tags**
        - Choose **Add new tag**
        - **Key:** Enter `Name`
        - **Value:** Enter `valkey-sg`
    - Then, click **Create security group**
    ![](/images/4.VPC/22.png)
