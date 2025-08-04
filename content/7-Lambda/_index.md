---
title : "Lambda"
date : "2025-07-28" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

1. Access the **AWS Management Console**
    - Search for the **Lambda** service
    - Select **Lambda** from the search results
    ![](/images/7.Lambda/1.png)

2. Choose **Create a function**
3. In **Create function** select **Container image**
    - **Function name:** Enter `demo-ml-inference`
    - **Container image URI** choose **Browser images**
    ![](/images/7.Lambda/2.png)
    - **Amazon ECR image repository** select **my-workshop-ecr**
    - Choose the existing image
    - Then, click **Select image**
    ![](/images/7.Lambda/3.png)


4. Open **IAM service** in different tab
    - Choose **Role** in the left-hand side
    - Click into **elasticache-iam-auth-app** role
    - Choose **Add permissions** 
    - Choose **Attach policy**
    ![](/images/7.Lambda/4.png)
    - Search **AWSLambdaVPCAccessExecutionRole**
    - Choose **AWSLambdaVPCAccessExecutionRole**
    - Click **Add permissions**
    ![](/images/7.Lambda/5.png)


5. Back to Lambda Tab, Expand **Change default execution role**
    - Choose **Use an existing role**
    - **Existing role** choose **elasticache-iam-auth-app**
    ![](/images/7.Lambda/6.png)

6. Expand **Additional configurations**
    - **VCP** tick to **Enable**
    - **VPC** select **my-workshop-vpc**
    - **Subnet** select **Private Subnet 1** and **Private Subnet 2**
    - **Security group** choose **lambda-sg**
    ![](/images/7.Lambda/7.png)
    - Scroll down, choose **Create function**
    ![](/images/7.Lambda/8.png)

7. Confirm
    - Successful
    ![](/images/7.Lambda/9.png)

8. Test the lambda function
    - Choose the **Configuration** Tab
    - Choose **Edit**
    ![](/images/7.Lambda/10.png)
    - For **Time out** change into **1 min**
    - Then, choose **Save**
    ![](/images/7.Lambda/11.png)

    - Choose the **Test** Tab in your function
    ![](/images/7.Lambda/12.png)
    - For **Event JSON**, type:
    ```
    {
        "text": "I love this movie"
    }
    ```
    - Then choose **Test**
    ![](/images/7.Lambda/13.png)

    - Lambda function runs probably
    ![](/images/7.Lambda/14.png)
    As you can see this Duration is **580.20 ms**, this is call the **Cold start**. This happends when we first run the function or run it again after a long break. 

    - To minimize this problem, we will configure our Lambda to run constantly by using **Provisioned concurrency**

#### Provisioned concurrency
9. Choose **Configuration** Tab
    - In the left-hand side, click **Concurrency and recursion detection**
    - If your **Unreserved account concurrency** looks like this
    ![](/images/7.Lambda/15.png)
    That means:     
        1. You have other lambda functions in the account that is using  the concurrency
        2. Your account is new (which is not your case as it is 4 month old) or your account is not having much usage, and aws has set lower limits for both cases.

    - Here is short steps to solve this:
        ![](/images/7.Lambda/16.png)
        ![](/images/7.Lambda/17.png)
        ![](/images/7.Lambda/18.png)
        ![](/images/7.Lambda/19.png)
        ![](/images/7.Lambda/20.png)
        ![](/images/7.Lambda/21.png)
        ![](/images/7.Lambda/22.png)
        ![](/images/7.Lambda/23.png)

10. Click **Versions** Tab 
    - Choose **Publish new version**
    ![](/images/7.Lambda/24.png)
    - For **Version description** enter `v1`
    - Click **Publish**
    ![](/images/7.Lambda/25.png)
    - After publish new version you will be already in **Configuration** Tab with **Provisioned concurrency**
    - Choose **Edit**
    ![](/images/7.Lambda/26.png)
    - Enter the number of **Provisioned concurrency** that you want for your lambda function
    - Click **Save**
    ![](/images/7.Lambda/27.png)


{{%notice warning%}}
When you use **Provisioned concurrency** that means your function runs constantly and is always ready to use. **However**, the **more provisioned concurrency** you use the **more money you pay**
{{%/notice%}}
- Wait for the status turn in to **Ready** 
    ![](/images/7.Lambda/28.png)
