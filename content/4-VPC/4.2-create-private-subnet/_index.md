---
title : "Create Private Subnet"
date : "2025-07-28"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

1. In **VPC dashboard**
    - Select **Subnets** from the left-hand menu
    - Click **Create subnet**
    ![](/images/4.VPC/5.png)

2. Select a VPC
    - In the Create subnet
    - Choose the **my-workshop-vpc** created earlier
    ![](/images/4.VPC/6.png)

3. Create the first private subnet
    - **Subnet name:** Enter `Private Subnet 1`
    - **Availability Zone:** Choose ap-southeast-1a
    - **IPv4 subnet CIDR block:** Enter `10.0.0.0/24`
    - Click **Create subnet**
    ![](/images/4.VPC/7.png)

4. Confirm 
    - Successful
    ![](/images/4.VPC/8.png)

5. Create the second private subnet
    - Choose the **my-workshop-vpc** created earlier
    - **Subnet name:** Enter `Private Subnet 2`
    - **Availability Zone:** Choose ap-southeast-1b
    - **IPv4 subnet CIDR block:** Enter `10.0.1.0/24`
    - Click **Create subnet**
    ![](/images/4.VPC/9.png)
6. Confirm
    - Successful
    ![](/images/4.VPC/10.png)