---
title : "Giám sát và chi phí"
date : "2025-07-28" 
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Giám sát
1. Trong **dashboard Lambda function của bạn**
    - Nhấp tab **Configuration**
    - Chọn **Monitoring and operations tools** trong thanh bên trái
    - Trong **Additional monitoring tools** chọn **Edit**
    ![](/images/10.Monitoring-Pricing/1.png)
    - Kích hoạt **X-Ray**
    - Nhấp **Save**
    ![](/images/10.Monitoring-Pricing/4.png)

2. Xác nhận
    - X-Ray đã được bật
    ![](/images/10.Monitoring-Pricing/5.png)

3. Truy cập dịch vụ **CloudWatch** (Gọi lại lambda function của bạn)
    - Chọn **trace**
    ![](/images/10.Monitoring-Pricing/6.png)
    - Chọn **Trace** mà bạn muốn xem chi tiết
    ![](/images/10.Monitoring-Pricing/7.png)


#### Phân tích chi phí
4. **Tính toán chi phí hàng tháng**

   **Cấu hình dịch vụ:**
   - **ECR**: 1 image (358.18MB)
   - **ElastiCache Serverless**: Valkey engine 
   - **Lambda**: 50 Provisioned Concurrency units
   - **CloudWatch**: Log monitoring
   - **X-Ray**: Distributed tracing
   - **API Gateway**: REST API only

5. **Chi tiết phân tích chi phí hàng tháng**

   **ECR (Elastic Container Registry)**
   ```
   Storage: 358.18MB = 0.358GB
   Pricing: $0.10 per GB per month
   Monthly Cost: 0.358 × $0.10 = $0.036
   ```

   **ElastiCache Serverless (Valkey)**
   ```
   Dựa trên usage pattern: ~2.9 GB-Hours hàng ngày
   Ước tính hàng tháng: 2.9 × 30 = 87 GB-Hours
   Pricing: $0.101 per GB-Hour for data storage
   Monthly Cost: 87 × $0.101 = $8.79
   ```

   **Lambda với Provisioned Concurrency** ⚠️ **CHI PHÍ CHÍNH**
   ```
   Configuration: 50 concurrent executions
   Memory allocation: 1GB (thông thường cho ML workloads)
   Monthly compute time: 50 × 1GB × 30 days × 24 hours × 3600 seconds
   = 129,600,000 GB-seconds per month
   
   Pricing: $0.0000041667 per GB-second
   Monthly Cost: 129,600,000 × $0.0000041667 = $540.00
   ```

   **API Gateway (REST API)**
   ```
   Ước tính monthly requests: ~30,000 (scale từ workshop usage)
   Free Tier: 1 triệu requests đầu tiên mỗi tháng
   Monthly Cost: $0.00 (trong free tier)
   ```

   **CloudWatch + X-Ray**
   ```
   CloudWatch Logs: Basic monitoring trong free tier
   X-Ray Traces: Ước tính 200 traces/tháng (trong 100K free tier)
   Monthly Cost: $0.00 (trong free tier)
   ```

6. **Tổng hợp chi phí hàng tháng**

   | Dịch vụ | Chi phí hàng tháng | Tỷ lệ phần trăm |
   |---------|-------------|------------|
   | Lambda (Provisioned Concurrency) | $540.00 | 98.4% |
   | ElastiCache Serverless | $8.79 | 1.6% |
   | ECR Storage | $0.036 | 0.007% |
   | API Gateway | $0.00 | 0% |
   | CloudWatch/X-Ray | $0.00 | 0% |
   | **TỔNG CỘNG** | **$548.83** | **100%** |

7. **Chiến lược tối ưu hóa chi phí**

   **Khuyến nghị quan trọng**: Cấu hình hiện tại với **50 Provisioned Concurrency** cực kỳ đắt đỏ cho production.

   **Các cấu hình thay thế:**

   **Lựa chọn 1: Giảm Provisioned Concurrency**
   ```
   5 Provisioned Concurrency units thay vì 50
   Monthly Cost: $54.00 (tiết kiệm 90%)
   Total Monthly: $62.83
   ```

   **Lựa chọn 2: Chỉ giờ hành chính (8AM-8PM)**
   ```
   50 units × 12 giờ/ngày thay vì 24/7
   Monthly Cost: $270.00 (tiết kiệm 50%)
   Total Monthly: $278.83
   ```

   **Lựa chọn 3: Không có Provisioned Concurrency**
   ```
   Sử dụng Lambda thông thường với cold starts
   Monthly Cost: ~$2-5 cho compute + requests
   Total Monthly: $10.83 (tiết kiệm 98%)
   ```

8. **Khuyến nghị cho Production**

    **Cho Development/Testing:**
    - Sử dụng **Lựa chọn 3** (Không có Provisioned Concurrency): **$10.83/tháng**
    
    **Cho Production (Low Traffic):**
    - Sử dụng **Lựa chọn 1** (5 Provisioned Concurrency): **$62.83/tháng**
    
    **Cho Production (High Performance):**
    - Sử dụng **Lựa chọn 2** (Chỉ giờ hành chính): **$278.83/tháng**

{{%notice warning%}}
**Cảnh báo chi phí quan trọng**: Cấu hình hiện tại của bạn có chi phí **$548.83/tháng** - điều này chủ yếu do 50 Provisioned Concurrency units chạy 24/7. Hãy xem xét giảm xuống 5-10 units hoặc thực hiện lập lịch theo thời gian để tiết kiệm đáng kể.
{{%/notice%}}

{{%notice tip%}}
**Tác động tối ưu hóa chi phí**:
- **Cấu hình hiện tại**: $548.83/tháng
- **Tối ưu hóa cho testing**: $10.83/tháng (tiết kiệm 98%)
- **Tối ưu hóa cho production**: $62.83/tháng (tiết kiệm 89%)
{{%/notice%}}