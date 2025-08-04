---
title : "Clean up"
date : "2025-07-28" 
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

### Delete Lambda function
1. In **Lambda function** dashboard
    - Choose **demo-ml-inference** 
    - Click **Action** select **Delete**
    ![](/images/11.Clean-up/1.png)
    - Type **confirm**
    - Click **Delete**
    ![](/images/11.Clean-up/2.png)

### Delete ElastiCache
2. In **ElastiCache** dashboard
    - Choose your Cache
    - Click **Action** choose **Delete**
    ![](/images/11.Clean-up/3.png)
    - For **Create backup** choose **No**
    - Type your cache's name
    - Click **Delete**
    ![](/images/11.Clean-up/4.png)
    - In **User management** delete **iam-user-01**
    ![](/images/11.Clean-up/5.png)
    - Click **Delete**
    ![](/images/11.Clean-up/6.png)
    - In **User group management** delete **iam-user-group-01**
    ![](/images/11.Clean-up/7.png)

### Delete Elastic Container Registry
3. In **Elastic Container Registry** dashboard
    - Choose your repository
    - Click **Delete**
    ![](/images/11.Clean-up/8.png)

### Delete API Gateway
4. In **API Gateway** dashboard
    - Choose your api
    - Click **Delete**
    ![](/images/11.Clean-up/9.png)

### Delete Policy and Role
5. In **Policies** dashboard
    - Delete `elasticache-allow-all` and `AWSLambdaTracerAccessExecutionRole-...`
    ![](/images/11.Clean-up/10.png)
    - In **Role** dashboard delete **elasticache-iam-auth-app**
    ![](/images/11.Clean-up/11.png)

