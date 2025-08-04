---
title : "Tạo serverless cache"
date : "2025-07-28" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

1. Truy cập **AWS Management Console**
    - Tìm kiếm dịch vụ **ElastiCache**
    - Chọn **ElastiCache** từ kết quả tìm kiếm
    ![](/images/5.ElastiCache/1.png)

2. Trong **Amazon ElastiCache**
    - Chọn **Valkey caches** ở bên trái
    - Nhấp **Create cache** 
    ![](/images/5.ElastiCache/2.png)

3. Trong **Configuration**
    - **Engine:** chọn **Valkey**
    - **Deployment option:** chọn **Serverless**
    - **Creation method:** chọn **New cache**
    ![](/images/5.ElastiCache/3.png)

4. Trong **Settings**
    - Với **Name:** nhập `my-workshop-cache`
    - **Engine version:** chọn **8**
    ![](/images/5.ElastiCache/4.png)

5. Mở rộng **Default settings**
    - Chọn **Customize default settings**
    ![](/images/5.ElastiCache/5.png)

6. Trong **Connectivity**
    - **VPC ID:** Chọn **my-workshop-vpc**
    - **Availability Zones:** Chọn **ap-southeast-1a** và **ap-southeast-1b**
    ![](/images/5.ElastiCache/6.png)

7. Với **Security**
    - Chọn **Customize your security settings**
    - Trong **Selected security groups**, chọn **Manage**
    ![](/images/5.ElastiCache/7.1.png)

    - Trong **Manage security groups**
        - Chọn **valkey-sg**
        - Sau đó, nhấp **Choose**
        ![](/images/5.ElastiCache/7.2.png)

8. Cuộn xuống, sau đó nhấp **Create**
    ![](/images/5.ElastiCache/8.png)

9. Đợi **Status** chuyển thành **Available**
    - Sao chép **Endpoint** và **ARN**, chúng ta sẽ sử dụng sau này
    ![](/images/5.ElastiCache/9.png)