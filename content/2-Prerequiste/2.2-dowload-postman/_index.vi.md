---
title : "Cài đặt Postman"
date : "2025-07-27"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

## Tổng quan

**Postman** là công cụ thiết yếu để test và phát triển APIs. Trong workshop ML Inference này, bạn sẽ sử dụng Postman để:

- **Test ML API endpoints** được triển khai trên AWS API Gateway
- **Gửi inference requests** với sample data đến serverless ML model
- **Xác minh response times** để đảm bảo yêu cầu độ trễ dưới 100ms
- **Test authentication** và cấu hình bảo mật
- **Monitor API behavior** dưới các điều kiện load khác nhau

### Tại sao dùng Postman cho ML APIs?

- **Quick Testing**: Gửi POST requests với JSON payloads chứa features để prediction
- **Response Analysis**: Xem model predictions và response metadata
- **Performance Monitoring**: Kiểm tra response times và debug latency issues
- **Collection Management**: Lưu ML inference requests cho các use cases khác nhau
- **Environment Variables**: Chuyển đổi giữa development, staging và production endpoints

---

## Hướng dẫn

1. Truy cập trang download chính thức của Postman:  
   👉 https://www.postman.com/downloads/

2. Chọn phiên bản phù hợp với hệ điều hành của bạn:

   - **Windows**: `.exe` installer
   - **macOS**: `.zip` hoặc `.dmg` file  
   - **Linux**: `.tar.gz` hoặc AppImage

3. Cài đặt và khởi chạy Postman. Bạn có thể đăng nhập hoặc click "Skip and take me to the app".

4. **Tính năng chính cho ML API Testing**:

   - **Request URL**: Nhập API Gateway endpoint của bạn
   - **Method**: Sử dụng POST cho ML inference requests
   - **Headers**: Set Content-Type: application/json
   - **Body**: Bao gồm JSON với features cho model prediction
   - **Tests**: Thêm scripts để validate response format và latency

5. **Tạo Collections cho ML Testing**:
   
   - ML Inference - Fraud Detection
   - Performance Tests
   - Error Handling Tests
   - Cache Validation Tests

