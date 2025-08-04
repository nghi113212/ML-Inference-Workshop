---
title : "Tạo Security Group"
date : "2025-07-28"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

1. Trong **VPC dashboard**
    - Chọn **Security groups** trong thanh bên trái
    - Nhấp **Create security group**
    ![](/images/4.VPC/20.png)

2. Trong **Basic details**
    - Với **Security group name:** `lambda-sg`
    - Với **Description:** `Security Group for Lambda functions accessing ElasticCache (Valkey) inside VPC`
    - **VPC:** Chọn **my-workshop-vpc**
    - Với **Tags**
        - Chọn **Add new tag**
        - **Key:** Nhập `Name`
        - **Value:** Nhập `lambda-sg`
    - Sau đó, nhấp **Create security group**
    ![](/images/4.VPC/21.png)

3. Tạo security group thứ hai cho Valkey
    - Làm các bước tương tự như trên
    - Với **Security group name:** `valkey-sg`
    - Với **Description:** `Allows inbound access from Lambda functions to ElasticCache (Valkey)`
    - **VPC:** Chọn **my-workshop-vpc**
    - Với **Inbound rules:**
        - Chọn **Add rule**
        - **Type:** Chọn **Custom TCP**
        - **Port range:** Nhập `6379`
        - **Source:** Chọn **Custom**, chọn **lambda-sg**
    - Với **Tags**
        - Chọn **Add new tag**
        - **Key:** Nhập `Name`
        - **Value:** Nhập `valkey-sg`
    - Sau đó, nhấp **Create security group**
    ![](/images/4.VPC/22.png)