---
title : "Tạo Route Table"
date : "2025-07-28" 
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Tạo route table
1. Trong **VPC dashboard**
    - Chọn **Route tables** từ thanh bên trái
    - Nhấp **Create route table**
    ![](/images/4.VPC/11.png)
2. Trong **Route table settings**
    - **Name:** `Route table-Private-1`
    - **VPC:** Chọn **my-workshop-vpc**
    - Nhấp **Create route table**
    ![](/images/4.VPC/12.png)

3. Xác nhận tạo
    - Thành công
    ![](/images/4.VPC/13.png)

4. Lặp lại bước tương tự cho private route table 2
    - **Name:** `Route table-Private-2`
    - **VPC:** Chọn **my-workshop-vpc**
    - Nhấp **Create route table**
    ![](/images/4.VPC/14.png)

5. Xác nhận tạo
    - Thành công
    ![](/images/4.VPC/15.png)

#### Liên kết với subnet

6. Trong **Route tables** dashboard
    - Chọn **Route table-Private-1**
    - Tiếp theo, chọn tab **Subnet associations**
    - Trong Explicit subnet associations, nhấp **Edit subnet associations**
    ![](/images/4.VPC/16.png)

7. Trong **Edit subnet associations**
    - Chọn **Private Subnet 1**
    - Sau đó, nhấp **Save associations**
    ![](/images/4.VPC/17.png)

8. Làm tương tự cho Route table-Private-2
    - Chọn **Route table-Private-2**
    ![](/images/4.VPC/18.png)
    ![](/images/4.VPC/19.png)
