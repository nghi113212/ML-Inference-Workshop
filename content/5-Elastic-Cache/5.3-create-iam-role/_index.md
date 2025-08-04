---
title : "Create IAM role"
date : "2025-07-28" 
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---


1. Access the **AWS Management Console**
    - Search for the **IAM** service
    - Select **IAM** from the search results
    ![](/images/5.ElastiCache/10.png)

2. In **Identity and Access Management (IAM)**
    - Select **Policies**
    - Click **Create policy**
    ![](/images/5.ElastiCache/14.png)

3. In **Policy editor**
    - Select **JSON**
    - Replace cache ARN with your own ARN
    ```
    {
    "Version": "2012-10-17",
    "Statement": [
        {
    "Effect" : "Allow",
        "Action" : [
            "elasticache:Connect"
        ],
        "Resource" : [
            "arn:aws:elasticache:ap-southeast-1:878585013121:serverlesscache:my-workshop-cache",
            "arn:aws:elasticache:ap-southeast-1:878585013121:user:iam-user-01"
        ]
        }
    ]
    }
    ```
    ![](/images/5.ElastiCache/34.png)

    - Scroll down, click **Next** 

4. In **Policy Details**
    - For **Policy name:** Enter `elasticache-allow-all`
    - Scroll down, click **Create policy**
    ![](/images/5.ElastiCache/16.png)

5. Confirm
    - Successful
    ![](/images/5.ElastiCache/17.png)

6. In **Identity and Access Management (IAM)**
    - Select **Roles**
    - Click **Create role**
    ![](/images/5.ElastiCache/11.png)

7. For **Trusted entity type**
    - Choose **Custom trust policy**
    ```
        {
    "Version": "2012-10-17",
        "Statement": [
        {
        "Effect": "Allow",
        "Principal": {
            "Service": "lambda.amazonaws.com"
        },
        "Action": "sts:AssumeRole"
        }]
    }

    ```


    - Click **Next**
<!-- ![](/images/5.ElastiCache/13.png) -->

8. In **Permissions policies**
    - **Filter by Type** Choose **Customer managed**
    - Then click **Next**
    ![](/images/5.ElastiCache/18.png)

9. In **Role details**
    - **Role name:** Enter `elasticache-iam-auth-app`
    - Scroll down, click **Create role**
    ![](/images/5.ElastiCache/35.png)

10. Confirm
    - Successfull
    ![](/images/5.ElastiCache/20.png)