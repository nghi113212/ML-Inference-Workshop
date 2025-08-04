---
title: "Giới thiệu"
date: "2024-07-27"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

## Tình huống thực tế

Hãy tưởng tượng bạn là data scientist tại một công ty thương mại điện tử. Team của bạn đã xây dựng một **model phát hiện gian lận** cần phân tích mọi giao dịch theo thời gian thực. Yêu cầu kinh doanh rất khắt khe:

- **Hiệu suất**: Phát hiện gian lận trong vòng **50ms** để không làm chậm giao dịch
- **Quy mô**: Xử lý **đợt tăng traffic Black Friday** từ 100 lên 10,000 requests mỗi giây
- **Chi phí**: Kiểm soát chi phí hạ tầng trong thời gian traffic thấp
- **Độ tin cậy**: Yêu cầu **99.9% uptime** cho hệ thống production

Hệ thống triển khai dựa trên server hiện tại không thể đáp ứng những demands này một cách cost-effective.

## Thách thức

Triển khai machine learning models lên production phức tạp và tốn kém. Các phương pháp truyền thống gặp khó khăn với:

- **Độ trễ cao** - Ứng dụng kinh doanh cần thời gian phản hồi dưới 100ms
- **Scaling không dự đoán được** - Đợt tăng traffic khó xử lý hiệu quả
- **Chi phí hạ tầng** - Server được cung cấp quá mức lãng phí tiền
- **Gánh nặng vận hành** - Quản lý server, scaling và monitoring

## Giải pháp của chúng tôi: Kiến trúc Serverless ML

Kiến trúc serverless AWS giải quyết những vấn đề này bằng cách cung cấp:

- **Thanh toán theo request** - Không có chi phí idle
- **Tự động scaling** - Từ không đến hàng nghìn requests
- **Độ trễ dưới 100ms** - Với provisioned concurrency
- **Monitoring tích hợp sẵn** - Tích hợp CloudWatch và X-Ray
- **Bảo mật doanh nghiệp** - Hỗ trợ IAM và VPC

### Kiến trúc giải pháp

![Kiến trúc](/images/AWS-Architecture.png)

**Cách hoạt động:**
1. **API Gateway** nhận và xác thực requests
2. **Lambda** load model và xử lý inference (với cache check)
3. **ElastiCache** lưu trữ predictions thường dùng để truy xuất instant
4. **CloudWatch** monitor hiệu suất và log tất cả activities

## Kết quả học tập

Sau khi hoàn thành workshop này, bạn sẽ:

- Biết cách xây dựng một machine learning model
- Triển khai ML models có khả năng mở rộng trên AWS serverless infrastructure
- Triển khai chiến lược caching hiệu quả cho ML workloads
- Thiết lập production monitoring và alerting
- Đạt được thời gian phản hồi nhất quán dưới 100ms


