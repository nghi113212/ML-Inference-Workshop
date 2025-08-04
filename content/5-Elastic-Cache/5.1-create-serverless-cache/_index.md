---
title : "Create serverless cache"
date : "2025-07-28" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

1. Access the **AWS Management Console**
    - Search for the **ElastiCache** service
    - Select **ElastiCache** from the search results
    ![](/images/5.ElastiCache/1.png)

2. In **Amazon ElastiCache**
    - Select **Valkey caches** in the left-hand side
    - Click **Create cache** 
    ![](/images/5.ElastiCache/2.png)

3. In **Configuration**
    - **Engine:** select **Valkey**
    - **Deployment option:** choose **Serverless**
    - **Creation method:** choose **New cache**
    ![](/images/5.ElastiCache/3.png)

4. In **Settings**
    - For **Name:** enter `my-workshop-cache`
    - **Engine version:** select **8**
    ![](/images/5.ElastiCache/4.png)

5. Expand **Default settings**
    - Select **Customize default settings**
    ![](/images/5.ElastiCache/5.png)

6. In **Connectivity**
    - **VPC ID:** Select **my-workshop-vpc**
    - **Availability Zones:** Select **ap-southeast-1a** and **ap-southeast-1b**
    ![](/images/5.ElastiCache/6.png)

7. For **Security**
    - Choose **Customize your security settings**
    - In **Selected security groups**, choose **Manage**
    ![](/images/5.ElastiCache/7.1.png)

    - In **Manage security groups**
        - Select **valkey-sg**
        - Then, click **Choose**
        ![](/images/5.ElastiCache/7.2.png)

8. Scroll down, then click **Create**
    ![](/images/5.ElastiCache/8.png)

9. Wait for the **Status** turns into **Available**
    - Copy the **Endpoint** and **ARN**, we will use this later
    ![](/images/5.ElastiCache/9.png)