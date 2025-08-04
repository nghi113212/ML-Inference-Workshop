---
title : "Các bước chuẩn bị"
date : "2024-07-27" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

## Tổng quan

Trước khi bắt đầu **Workshop ML Inference** này, bạn cần cài đặt và cấu hình các công cụ sau đây. Workshop này tập trung vào việc triển khai các mô hình machine learning dưới dạng **serverless containers** sử dụng **AWS Lambda** và **API Gateway** để thực hiện inference hiệu suất cao.

---

## Công cụ cần thiết

### 🛠️ Môi trường phát triển
- **[Visual Studio Code](2.1-dowload-vs-code)** - IDE để phát triển code với các extensions cho ML và Docker
- **[Python](2.5-dowload-python)** - Ngôn ngữ lập trình cho việc phát triển ML model và tích hợp AWS

### 🐳 Containerization
- **[Docker Desktop](2.3-dowload-docker)** - Đóng gói ML models thành containers tối ưu cho AWS Lambda deployment

### ☁️ Tích hợp AWS  
- **[AWS CLI](2.4-dowload-aws-cli)** - Công cụ dòng lệnh để push Docker images lên Elastic Container Registry (ECR)

### 🧪 Kiểm thử API
- **[Postman](2.2-dowload-postman)** - Test ML inference endpoints, verify thời gian phản hồi dưới 100ms, và validate API behavior

---

## Quy trình workshop

Với các công cụ này, bạn sẽ có thể:

1. **Phát triển** ML models locally sử dụng Python
2. **Containerize** models với Docker cho Lambda deployment  
3. **Push** container images lên AWS ECR sử dụng AWS CLI
4. **Deploy** serverless inference APIs trên AWS Lambda
5. **Test** hiệu suất API và chức năng với Postman

{{% notice info %}}
**Thời gian cài đặt ước tính**: 30-45 phút cho việc cài đặt và cấu hình tất cả công cụ
{{% /notice %}}
