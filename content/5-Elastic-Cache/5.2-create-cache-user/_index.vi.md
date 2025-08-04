---
title : "Tạo ElastiCache user"
date : "2025-07-28" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

1. Truy cập **AWS Management Console**
    - Tìm kiếm dịch vụ **ElastiCache**
    - Chọn **ElastiCache** từ kết quả tìm kiếm
    ![](/images/5.ElastiCache/1.png)

2. Trong **Amazon ElastiCache**
    - Chọn **User management** ở bên trái
    - Nhấp **Create user** 
    ![](/images/5.ElastiCache/21.png)

3. Trong **User settings**
    - Với **User ID** và **User name:** Nhập `iam-user-01`
    - **Engine:** Chọn **Valkey**
    ![](/images/5.ElastiCache/22.png)

4. Trong **User authentication settings**
    - Chọn **IAM authentication**
5. Trong **Access string**
    - Nhập: `on ~* +@all`
    - Sau đó, nhấp **Create**
    ![](/images/5.ElastiCache/23.png)
    - Sau khi tạo, sao chép giá trị ARN của **iam-user-01**, chúng ta sẽ sử dụng sau này
    ![](/images/5.ElastiCache/33.png)

6. Trong **Amazon ElastiCache**
    - Chọn **User group management**
    - Nhấp **Create user group**
    ![](/images/5.ElastiCache/24.png)

7. Trong **User group settings**
    - **User group ID:** Nhập `iam-user-group-01`
    - Với **Selected users**, nhấp **Manage**
    - Chọn **iam-user-01**, sau đó nhấp **Choose**
    ![](/images/5.ElastiCache/25.png)
    - Cuộn xuống, nhấp **Create**
    ![](/images/5.ElastiCache/26.png)

8. Quay lại **Valkey cache**
    - Chọn **my-workshop-cache**
    ![](/images/5.ElastiCache/27.png)

9. Trong **my-workshop-cache**
    - Nhấp **Modify**
    ![](/images/5.ElastiCache/28.png)

10. Cuộn xuống **Security**
    - **Access control:** Chọn **User group access control list**
    - **User group:** Chọn **iam-user-group-01**
    ![](/images/5.ElastiCache/29.png)
    - Cuộn xuống và nhấp **Preview changes**
    ![](/images/5.ElastiCache/30.png)
    - Nhấp **Save changes**
    ![](/images/5.ElastiCache/31.png)

11. Xác nhận
    - Thành công
    ![](/images/5.ElastiCache/32.png)