---
title : "VPC"
date : "2025-07-28" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

Trong workshop này, việc tạo một Virtual Private Cloud (VPC) là bước quan trọng nhằm mô phỏng môi trường mạng riêng trong thực tế khi triển khai hệ thống trên AWS. Thay vì sử dụng VPC mặc định, việc tự thiết lập VPC giúp bạn kiểm soát hoàn toàn cách các dịch vụ như Lambda, ElastiCache giao tiếp với nhau, đồng thời đảm bảo an toàn và bảo mật cao hơn cho tài nguyên. Ngoài ra, nó còn giúp bạn hiểu rõ cách phân chia mạng, thiết lập kết nối nội bộ, và áp dụng các nguyên tắc bảo mật theo chuẩn kiến trúc của AWS.

Cụ thể, việc tạo VPC mang lại các lợi ích sau:

- Cách ly mạng: Chia subnet công khai và riêng tư để cô lập tài nguyên quan trọng, tránh truy cập trái phép từ Internet.

- Tăng cường bảo mật: Dễ dàng kiểm soát truy cập bằng security group và routing table, tránh lộ tài nguyên như cache hay database.

- Thực hành networking thực tế: Học cách kết nối Lambda trong private subnet với dịch vụ nội bộ như ElastiCache mà không cần public IP.

- Mô phỏng hệ thống production: Thiết kế gần giống môi trường triển khai thật, phục vụ học tập và ứng dụng thực tiễn.

- Chuẩn bị cho các kiến trúc phức tạp hơn: Là nền tảng để mở rộng với các dịch vụ như NAT Gateway, Load Balancer hoặc Service Mesh.

