---
title : "ECR"
date : "2025-07-28" 
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---

Amazon Elastic Container Registry (ECR) là một dịch vụ Docker container registry được quản lý hoàn toàn, giúp dễ dàng lưu trữ, quản lý và triển khai các Docker container images. Trong workshop này, ECR đóng vai trò là kho lưu trữ trung tâm cho container chứa machine learning model của chúng ta, bao gồm sentiment analysis model cùng tất cả các dependencies. ECR tích hợp liền mạch với AWS Lambda, cho phép chúng ta triển khai các ML model được đóng gói trong container - điều này phù hợp với những model quá lớn hoặc phức tạp so với traditional Lambda deployment packages. Cách tiếp cận này mang lại khả năng quản lý dependencies tốt hơn, thời gian cold start nhanh hơn cho ML workloads, và dễ dàng quản lý phiên bản cho các lần triển khai model.