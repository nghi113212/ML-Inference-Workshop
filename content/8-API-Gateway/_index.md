---
title : "API Gateway"
date : "2025-07-28" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

1. Access the **AWS Management Console**
    - Search for the **API Gateway** service
    - Select **API Gateway** from the search results
    ![](/images/8.API-Gateway/1.png)

2. In **API Gateway** dashboard
    - Click **APIs** in the left-hand side
    - Next, choose **Create API** in the right-hand side
    ![](/images/8.API-Gateway/2.png)

3. Scroll down to **REST API**
    - Click **Build**
    ![](/images/8.API-Gateway/3.png)

4. In **API details**
    - Choose **New API**
    - For **API Name** enter `my-workshop-api`
    - Then, click **Create API**
    ![](/images/8.API-Gateway/4.png)

5. After created
    - Click **Create resource**
    ![](/images/8.API-Gateway/5.png)

6. In **Resource details**
    - For **Resource name** enter `predict`
    - Click **Create resource**
    ![](/images/8.API-Gateway/6.png)

7. After created
    - Click **Create method**
    ![](/images/8.API-Gateway/7.png)

8. In **Method details**
    - For **Method type** select **POST**
    - For **Integration type** choose **Lambda function**
    - For **Lambda function** select **Your lambda function**
    ![](/images/8.API-Gateway/8.png)

    - Scroll down and click **Create method**
    ![](/images/8.API-Gateway/8.1.png)

9. After created
    - Click **Deploy API**
    ![](/images/8.API-Gateway/9.png)
    - In **Deploy API**, for **Stage** select **New stage**
    ![](/images/8.API-Gateway/9.1.png)
    - For **Stage name** enter `prod`
    - Then click **Deploy**
    ![](/images/8.API-Gateway/9.2.png)

10. Confirm
    - Successful
    ![](/images/8.API-Gateway/10.png)

{{%notice note%}}
We will use the **Invoke URL** to invoke our Lambda function
{{%/notice%}}
