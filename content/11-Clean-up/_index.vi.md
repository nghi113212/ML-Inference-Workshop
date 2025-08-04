---
title : "Dọn dẹp tài nguyên"
date : "2025-07-28" 
weight : 11
chapter : false
pre : " <b> 11. </b> "
---

### Xóa Lambda function
1. Trong **Lambda function** dashboard
    - Chọn **demo-ml-inference** 
    - Nhấp **Action** chọn **Delete**
    ![](/images/11.Clean-up/1.png)
    - Gõ **confirm**
    - Nhấp **Delete**
    ![](/images/11.Clean-up/2.png)

### Xóa ElastiCache
2. Trong **ElastiCache** dashboard
    - Chọn Cache của bạn
    - Nhấp **Action** chọn **Delete**
    ![](/images/11.Clean-up/3.png)
    - Với **Create backup** chọn **No**
    - Gõ tên cache của bạn
    - Nhấp **Delete**
    ![](/images/11.Clean-up/4.png)
    - Trong **User management** xóa **iam-user-01**
    ![](/images/11.Clean-up/5.png)
    - Nhấp **Delete**
    ![](/images/11.Clean-up/6.png)
    - Trong **User group management** xóa **iam-user-group-01**
    ![](/images/11.Clean-up/7.png)

### Xóa Elastic Container Registry
3. Trong **Elastic Container Registry** dashboard
    - Chọn repository của bạn
    - Nhấp **Delete**
    ![](/images/11.Clean-up/8.png)

### Xóa API Gateway
4. Trong **API Gateway** dashboard
    - Chọn api của bạn
    - Nhấp **Delete**
    ![](/images/11.Clean-up/9.png)

### Xóa Policy và Role
5. Trong **Policies** dashboard
    - Xóa `elasticache-allow-all` và `AWSLambdaTracerAccessExecutionRole-...`
    ![](/images/11.Clean-up/10.png)
    - Trong **Role** dashboard xóa **elasticache-iam-auth-app**
    ![](/images/11.Clean-up/11.png)