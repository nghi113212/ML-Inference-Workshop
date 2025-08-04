---
title : "Create ElastiCache user"
date : "2025-07-28" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---


1. Access the **AWS Management Console**
    - Search for the **ElastiCache** service
    - Select **ElastiCache** from the search results
    ![](/images/5.ElastiCache/1.png)

2. In **Amazon ElastiCache**
    - Select **User management** in the left-hand side
    - Click **Create user** 
    ![](/images/5.ElastiCache/21.png)

3. In **User settings**
    - For **User ID** and **User name:** Enter `iam-user-01`
    - **Engine:** Select **Valkey**
    ![](/images/5.ElastiCache/22.png)

4. In **User authentication settings**
    - Choose **IAM authentication**
5. In **Access string**
    - Enter: `on ~* +@all`
    - Then, click **Create**
    ![](/images/5.ElastiCache/23.png)
    - After created, copy ARN value of **iam-user-01** we will use this later
    ![](/images/5.ElastiCache/33.png)

6. In **Amazon ElastiCache**
    - Choose **User group management**
    - Click **Create user group**
    ![](/images/5.ElastiCache/24.png)

7. In **User group settings**
    - **User group ID:** Enter `iam-user-group-01`
    - For **Selected users**, click **Manage**
    - Select **iam-user-01**, then click **Choose**
    ![](/images/5.ElastiCache/25.png)
    - Scroll down, click **Create**
    ![](/images/5.ElastiCache/26.png)

8. Back to **Valkey cache**
    - Select **my-workshop-cache**
    ![](/images/5.ElastiCache/27.png)

9. In **my-workshop-cache**
    - Click **Modify**
    ![](/images/5.ElastiCache/28.png)

10. Scroll down to **Security**
    - **Access control:** Select **User group access control list**
    - **User group:**  Select **iam-user-group-01**
    ![](/images/5.ElastiCache/29.png)
    - Scroll down and click **Preview changes**
    ![](/images/5.ElastiCache/30.png)
    - Click **Save changes**
    ![](/images/5.ElastiCache/31.png)

11. Confirm
    - Successfull
    ![](/images/5.ElastiCache/32.png)