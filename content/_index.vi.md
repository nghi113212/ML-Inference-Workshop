---
title : "First Cloud Journey"
date : "2025-07-26" 
weight : 1 
chapter : false
---

# Hệ thống ML Inference thời gian thực với AWS Lambda & API Gateway

## Tổng quan Workshop

Workshop này cung cấp trải nghiệm thực hành trong việc xây dựng và triển khai hệ thống machine learning inference sẵn sàng cho production sử dụng các công nghệ serverless của AWS. Bạn sẽ học cách tạo một ML API có khả năng mở rộng với thời gian phản hồi dưới 100ms trong khi duy trì hiệu quả chi phí và bảo mật cấp doanh nghiệp.

---

## Những gì bạn sẽ xây dựng

Một giải pháp ML inference serverless hoàn chỉnh bao gồm:

- **Phản hồi API siêu nhanh** (< 100ms) sử dụng AWS Lambda và API Gateway
- **Caching thông minh** với ElastiCache Valkey để tối ưu hiệu suất  
- **Monitoring production** sử dụng CloudWatch và AWS X-Ray
- **Bảo mật doanh nghiệp** với IAM roles và tích hợp VPC
- **Khả năng auto-scaling** xử lý các đợt tăng traffic một cách liền mạch


## Công nghệ chính

- **AWS Lambda** - Serverless compute để hosting ML model
- **API Gateway** - Quản lý và định tuyến RESTful API
- **ElastiCache Valkey** - Lớp caching hiệu suất cao
- **Python 3.12** - Môi trường runtime với Scikit-learn
- **CloudWatch & X-Ray** - Monitoring và tracing toàn diện


## Mục tiêu học tập

Sau khi hoàn thành workshop này, bạn sẽ:

- Biết cách xây dựng một machine learning model
- Triển khai ML models sẵn sàng cho production trên AWS serverless infrastructure
- Triển khai các chiến lược caching hiệu quả cho ML workloads
- Thiết lập hệ thống monitoring và alerting toàn diện
- Áp dụng các best practices bảo mật AWS cho ứng dụng doanh nghiệp
- Tối ưu hiệu suất hệ thống cho yêu cầu inference thời gian thực



## Yêu cầu tiên quyết

- Làm quen cơ bản với AWS console
- Hiểu biết về REST APIs và các khái niệm HTTP
- Kiến thức lập trình Python (mức trung cấp)
- Tài khoản AWS với quyền phù hợp


## Nội dung
- [1. Giới thiệu](/1-Introduce/)
- [2. Các bước chuẩn bị](/2-Prerequiste/)
- [3. Xây dựng model](/3-Build-model)
- [4. VPC](/4-VPC)
- [5. ElastiCache](/5-Elastic-Cache)
- [6. ECR](/6-ECR)
- [7. Lambda](/7-Lambda)
- [8. API Gateway](/8-API-Gateway)
- [9. Kiểm thử](/9-Testing)
- [10. Giám sát và chi phí](/10-Monitoring)
- [11. Dọn dẹp tài nguyên](/11-Clean-up)
