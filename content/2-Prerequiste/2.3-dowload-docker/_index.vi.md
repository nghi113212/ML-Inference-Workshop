---
title : "Cài đặt Docker Desktop"
date : "2025-07-27"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

## Tổng quan

**Docker Desktop** là công cụ thiết yếu cho workshop ML Inference này vì AWS Lambda hỗ trợ **container-based deployments**. Bạn sẽ sử dụng Docker để:

- **Đóng gói ML models** cùng với dependencies vào containers
- **Test locally** trước khi deploy lên AWS Lambda
- **Build optimized images** để cold starts nhanh hơn
- **Quản lý Python dependencies** và ML libraries hiệu quả
- **Đảm bảo consistent environments** giữa development và production

### Tại sao dùng Containers cho ML Inference?

- **Larger Package Sizes**: ML libraries như scikit-learn, numpy vượt quá giới hạn 250MB của Lambda
- **Dependency Management**: Complex ML dependencies dễ quản lý hơn trong containers
- **Performance Optimization**: Pre-built images giảm cold start times
- **Reproducible Deployments**: Cùng environment trên dev, staging, và production

---

## Hướng dẫn cài đặt

### 1. Download Docker Desktop

Truy cập trang web chính thức của Docker:  
👉 https://www.docker.com/products/docker-desktop/

![Docker](/images/2.Prerequiste/2.3-docker.png)

Chọn hệ điều hành của bạn:
- **Windows**: Docker Desktop for Windows (yêu cầu WSL2)
- **macOS**: Docker Desktop for Mac (Intel hoặc Apple Silicon)
- **Linux**: Docker Desktop for Linux

### 2. Yêu cầu hệ thống

**Windows:**
- Windows 10/11 64-bit (Pro, Enterprise, Education)
- WSL2 feature được enabled
- Tối thiểu 4GB RAM

**macOS:**
- macOS 10.15 hoặc mới hơn
- Tối thiểu 4GB RAM

**Linux:**
- 64-bit kernel và CPU virtualization support
- Tối thiểu 4GB RAM

### 3. Quá trình cài đặt

1. **Download** installer từ trang web chính thức
2. **Chạy** installer với administrator privileges
3. **Restart** máy tính khi được yêu cầu
4. **Khởi chạy** Docker Desktop và hoàn thành initial setup

### 4. Xác minh cài đặt

Mở terminal/command prompt và chạy:

```bash
docker --version
docker run hello-world
```

Bạn sẽ thấy thông tin version Docker và một test run thành công.
