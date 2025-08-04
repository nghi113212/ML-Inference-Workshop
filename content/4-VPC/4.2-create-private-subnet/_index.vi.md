---
title : "Tạo Private Subnet"
date : "2025-07-28" 
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---

1. Trong **VPC dashboard**
    - Chọn **Subnets** từ menu bên trái
    - Nhấp **Create subnet**
    ![](/images/4.VPC/5.png)

2. Chọn VPC
    - Trong Create subnet
    - Chọn **my-workshop-vpc** đã tạo trước đó
    ![](/images/4.VPC/6.png)

3. Tạo private subnet đầu tiên
    - **Subnet name:** Nhập `Private Subnet 1`
    - **Availability Zone:** Chọn ap-southeast-1a
    - **IPv4 subnet CIDR block:** Nhập `10.0.0.0/24`
    - Nhấp **Create subnet**
    ![](/images/4.VPC/7.png)

4. Xác nhận
    - Thành công
    ![](/images/4.VPC/8.png)

5. Tạo private subnet thứ hai
    - Chọn **my-workshop-vpc** đã tạo trước đó
    - **Subnet name:** Nhập `Private Subnet 2`
    - **Availability Zone:** Chọn ap-southeast-1b
    - **IPv4 subnet CIDR block:** Nhập `10.0.1.0/24`
    - Nhấp **Create subnet**
    ![](/images/4.VPC/9.png)
6. Xác nhận
    - Thành công
    ![](/images/4.VPC/10.png)