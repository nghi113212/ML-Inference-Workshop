---
title: "Cài đặt AWS CLI"
date : "2025-07-27"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

## Tổng quan

AWS CLI (Command Line Interface) là công cụ dòng lệnh chính thức để quản lý tài nguyên AWS trực tiếp từ terminal. Trong workshop này, nó sẽ được sử dụng để kết nối đến Elastic Container Registry để push image của model từ docker.

---

## Cài đặt

### Bước 1: Tải và cài đặt

Truy cập trang cài đặt chính thức:
👉 **https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html**

**Dành cho Windows:**
- Tải file `.msi` installer và chạy

**Dành cho macOS:**
```bash
brew install awscli
```

**Dành cho Linux (Ubuntu/Debian):**
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### Bước 2: Kiểm tra cài đặt

```bash
aws --version
```

Kết quả mong đợi: `aws-cli/2.x.x Python/3.x.x`

---

## Cấu hình

### Tạo IAM User (Khuyến nghị)

{{% notice warning %}}
**Bảo mật:** Không sử dụng thông tin tài khoản root AWS. Hãy tạo IAM user thay thế.
{{% /notice %}}

### Cấu hình CLI

```bash
aws configure
```

Nhập thông tin xác thực:
```
AWS Access Key ID: [Access Key của bạn]
AWS Secret Access Key: [Secret Key của bạn]
Default region name: us-east-1
Default output format:
```
