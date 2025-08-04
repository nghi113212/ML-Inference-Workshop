---
title : "Lambda"
date : "2025-07-28" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

1. Truy cập **AWS Management Console**
    - Tìm kiếm dịch vụ **Lambda**
    - Chọn **Lambda** từ kết quả tìm kiếm
    ![](/images/7.Lambda/1.png)

2. Chọn **Create a function**
3. Trong **Create function** chọn **Container image**
    - **Function name:** Nhập `demo-ml-inference`
    - **Container image URI** chọn **Browser images**
    ![](/images/7.Lambda/2.png)
    - **Amazon ECR image repository** chọn **my-workshop-ecr**
    - Chọn image hiện có
    - Sau đó, nhấp **Select image**
    ![](/images/7.Lambda/3.png)


4. Mở **IAM service** trong tab khác
    - Chọn **Role** ở bên trái
    - Nhấp vào role **elasticache-iam-auth-app**
    - Chọn **Add permissions** 
    - Chọn **Attach policy**
    ![](/images/7.Lambda/4.png)
    - Tìm kiếm **AWSLambdaVPCAccessExecutionRole**
    - Chọn **AWSLambdaVPCAccessExecutionRole**
    - Nhấp **Add permissions**
    ![](/images/7.Lambda/5.png)


5. Quay lại tab Lambda, mở rộng **Change default execution role**
    - Chọn **Use an existing role**
    - **Existing role** chọn **elasticache-iam-auth-app**
    ![](/images/7.Lambda/6.png)

6. Mở rộng **Additional configurations**
    - **VCP** tích chọn **Enable**
    - **VPC** chọn **my-workshop-vpc**
    - **Subnet** chọn **Private Subnet 1** và **Private Subnet 2**
    - **Security group** chọn **lambda-sg**
    ![](/images/7.Lambda/7.png)
    - Cuộn xuống, chọn **Create function**
    ![](/images/7.Lambda/8.png)

7. Xác nhận
    - Thành công
    ![](/images/7.Lambda/9.png)

8. Test lambda function
    - Chọn tab **Configuration**
    - Chọn **Edit**
    ![](/images/7.Lambda/10.png)
    - Với **Time out** thay đổi thành **1 min**
    - Sau đó, chọn **Save**
    ![](/images/7.Lambda/11.png)

    - Chọn tab **Test** trong function của bạn
    ![](/images/7.Lambda/12.png)
    - Với **Event JSON**, gõ:
    ```
    {
        "text": "I love this movie"
    }
    ```
    - Sau đó chọn **Test**
    ![](/images/7.Lambda/13.png)

    - Lambda function chạy thành công
    ![](/images/7.Lambda/14.png)
    Như bạn có thể thấy Duration này là **580.20 ms**, đây được gọi là **Cold start**. Điều này xảy ra khi chúng ta chạy function lần đầu tiên hoặc chạy lại sau một khoảng thời gian dài.

    - Để giảm thiểu vấn đề này, chúng ta sẽ cấu hình Lambda chạy liên tục bằng cách sử dụng **Provisioned concurrency**

#### Provisioned concurrency
9. Chọn tab **Configuration**
    - Ở bên trái, nhấp **Concurrency and recursion detection**
    - Nếu **Unreserved account concurrency** của bạn trông như thế này
    ![](/images/7.Lambda/15.png)
    Điều đó có nghĩa là:     
        1. Bạn có các lambda function khác trong tài khoản đang sử dụng concurrency
        2. Tài khoản của bạn mới (điều này không phải trường hợp của bạn vì đã 4 tháng tuổi) hoặc tài khoản của bạn không có nhiều usage, và AWS đã đặt giới hạn thấp hơn cho cả hai trường hợp.

    - Đây là các bước ngắn để giải quyết vấn đề này:
        ![](/images/7.Lambda/16.png)
        ![](/images/7.Lambda/17.png)
        ![](/images/7.Lambda/18.png)
        ![](/images/7.Lambda/19.png)
        ![](/images/7.Lambda/20.png)
        ![](/images/7.Lambda/21.png)
        ![](/images/7.Lambda/22.png)
        ![](/images/7.Lambda/23.png)

10. Nhấp tab **Versions** 
    - Chọn **Publish new version**
    ![](/images/7.Lambda/24.png)
    - Với **Version description** nhập `v1`
    - Nhấp **Publish**
    ![](/images/7.Lambda/25.png)
    - Sau khi publish version mới, bạn sẽ đã ở trong tab **Configuration** với **Provisioned concurrency**
    - Chọn **Edit**
    ![](/images/7.Lambda/26.png)
    - Nhập số lượng **Provisioned concurrency** mà bạn muốn cho lambda function của mình
    - Nhấp **Save**
    ![](/images/7.Lambda/27.png)


{{%notice warning%}}
Khi bạn sử dụng **Provisioned concurrency** có nghĩa là function của bạn chạy liên tục và luôn sẵn sàng để sử dụng. **Tuy nhiên**, **càng sử dụng nhiều provisioned concurrency** thì **càng phải trả nhiều tiền**
{{%/notice%}}
- Đợi status chuyển thành **Ready** 
    ![](/images/7.Lambda/28.png)