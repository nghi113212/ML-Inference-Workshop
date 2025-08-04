---
title : "Tạo IAM role"
date : "2025-07-28" 
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---

1. Truy cập **AWS Management Console**
    - Tìm kiếm dịch vụ **IAM**
    - Chọn **IAM** từ kết quả tìm kiếm
    ![](/images/5.ElastiCache/10.png)

2. Trong **Identity and Access Management (IAM)**
    - Chọn **Policies**
    - Nhấp **Create policy**
    ![](/images/5.ElastiCache/14.png)

3. Trong **Policy editor**
    - Chọn **JSON**
    - Thay thế cache ARN bằng ARN của riêng bạn
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

    - Cuộn xuống, nhấp **Next** 

4. Trong **Policy Details**
    - Với **Policy name:** Nhập `elasticache-allow-all`
    - Cuộn xuống, nhấp **Create policy**
    ![](/images/5.ElastiCache/16.png)

5. Xác nhận
    - Thành công
    ![](/images/5.ElastiCache/17.png)

6. Trong **Identity and Access Management (IAM)**
    - Chọn **Roles**
    - Nhấp **Create role**
    ![](/images/5.ElastiCache/11.png)

7. Với **Trusted entity type**
    - Chọn **Custom trust policy**
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

    - Nhấp **Next**

8. Trong **Permissions policies**
    - **Filter by Type** Chọn **Customer managed**
    - Sau đó nhấp **Next**
    ![](/images/5.ElastiCache/18.png)

9. Trong **Role details**
    - **Role name:** Nhập `elasticache-iam-auth-app`
    - Cuộn xuống, nhấp **Create role**
    ![](/images/5.ElastiCache/35.png)

10. Xác nhận
    - Thành công
    ![](/images/5.ElastiCache/20.png)