---
title : "API Gateway"
date : "2025-07-28" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

1. Truy cập **AWS Management Console**
    - Tìm kiếm dịch vụ **API Gateway**
    - Chọn **API Gateway** từ kết quả tìm kiếm
    ![](/images/8.API-Gateway/1.png)

2. Trong **API Gateway** dashboard
    - Nhấp **APIs** ở bên trái
    - Tiếp theo, chọn **Create API** ở bên phải
    ![](/images/8.API-Gateway/2.png)

3. Cuộn xuống **REST API**
    - Nhấp **Build**
    ![](/images/8.API-Gateway/3.png)

4. Trong **API details**
    - Chọn **New API**
    - Với **API Name** nhập `my-workshop-api`
    - Sau đó, nhấp **Create API**
    ![](/images/8.API-Gateway/4.png)

5. Sau khi tạo
    - Nhấp **Create resource**
    ![](/images/8.API-Gateway/5.png)

6. Trong **Resource details**
    - Với **Resource name** nhập `predict`
    - Nhấp **Create resource**
    ![](/images/8.API-Gateway/6.png)

7. Sau khi tạo
    - Nhấp **Create method**
    ![](/images/8.API-Gateway/7.png)

8. Trong **Method details**
    - Với **Method type** chọn **POST**
    - Với **Integration type** chọn **Lambda function**
    - Với **Lambda function** chọn **Lambda function của bạn**
    ![](/images/8.API-Gateway/8.png)

    - Cuộn xuống và nhấp **Create method**
    ![](/images/8.API-Gateway/8.1.png)

9. Sau khi tạo
    - Nhấp **Deploy API**
    ![](/images/8.API-Gateway/9.png)
    - Trong **Deploy API**, với **Stage** chọn **New stage**
    ![](/images/8.API-Gateway/9.1.png)
    - Với **Stage name** nhập `prod`
    - Sau đó nhấp **Deploy**
    ![](/images/8.API-Gateway/9.2.png)

10. Xác nhận
    - Thành công
    ![](/images/8.API-Gateway/10.png)

{{%notice note%}}
Chúng ta sẽ sử dụng **Invoke URL** để gọi Lambda function của mình
{{%/notice%}}