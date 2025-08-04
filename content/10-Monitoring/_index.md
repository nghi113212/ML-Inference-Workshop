---
title : "Monitoring and Pricing"
date : "2025-07-28" 
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Monitoring
1. In **your Lambda function dashboard**
    - Click **Configuration** Tab
    - Choose **Monitoring and operations tools** in the left sidebar
    - In **Additional monitoring tools** choose **Edit**
    ![](/images/10.Monitoring-Pricing/1.png)
    - Activate **X-Ray**
    - Click **Save**
    ![](/images/10.Monitoring-Pricing/4.png)

2. Confirm
    - X-Ray is enable
    ![](/images/10.Monitoring-Pricing/5.png)

3. Access **CloudWatch** service (Your invoke lambda function again)
    - Choose **trace**
    ![](/images/10.Monitoring-Pricing/6.png)
    - Select **Trace** you want to see insight
    ![](/images/10.Monitoring-Pricing/7.png)


#### Cost analysis
4. **Monthly Cost Calculation**

   **Service Configuration:**
   - **ECR**: 1 image (358.18MB)
   - **ElastiCache Serverless**: Valkey engine 
   - **Lambda**: 50 Provisioned Concurrency units
   - **CloudWatch**: Log monitoring
   - **X-Ray**: Distributed tracing
   - **API Gateway**: REST API only

5. **Detailed Monthly Cost Breakdown**

   **ECR (Elastic Container Registry)**
   ```
   Storage: 358.18MB = 0.358GB
   Pricing: $0.10 per GB per month
   Monthly Cost: 0.358 × $0.10 = $0.036
   ```

   **ElastiCache Serverless (Valkey)**
   ```
   Based on usage pattern: ~2.9 GB-Hours daily
   Monthly estimate: 2.9 × 30 = 87 GB-Hours
   Pricing: $0.101 per GB-Hour for data storage
   Monthly Cost: 87 × $0.101 = $8.79
   ```

   **Lambda with Provisioned Concurrency** ⚠️ **MAJOR COST**
   ```
   Configuration: 50 concurrent executions
   Memory allocation: 1GB (typical for ML workloads)
   Monthly compute time: 50 × 1GB × 30 days × 24 hours × 3600 seconds
   = 129,600,000 GB-seconds per month
   
   Pricing: $0.0000041667 per GB-second
   Monthly Cost: 129,600,000 × $0.0000041667 = $540.00
   ```

   **API Gateway (REST API)**
   ```
   Estimated monthly requests: ~30,000 (scaled from workshop usage)
   Free Tier: First 1 million requests per month
   Monthly Cost: $0.00 (within free tier)
   ```

   **CloudWatch + X-Ray**
   ```
   CloudWatch Logs: Basic monitoring within free tier
   X-Ray Traces: Estimated 200 traces/month (within 100K free tier)
   Monthly Cost: $0.00 (within free tier)
   ```

6. **Total Monthly Cost Summary**

   | Service | Monthly Cost | Percentage |
   |---------|-------------|------------|
   | Lambda (Provisioned Concurrency) | $540.00 | 98.4% |
   | ElastiCache Serverless | $8.79 | 1.6% |
   | ECR Storage | $0.036 | 0.007% |
   | API Gateway | $0.00 | 0% |
   | CloudWatch/X-Ray | $0.00 | 0% |
   | **TOTAL** | **$548.83** | **100%** |

7. **Cost Optimization Strategies**

   **Critical Recommendation**: The current setup with **50 Provisioned Concurrency** is extremely expensive for production.

   **Alternative Configurations:**

   **Option 1: Reduce Provisioned Concurrency**
   ```
   5 Provisioned Concurrency units instead of 50
   Monthly Cost: $54.00 (90% savings)
   Total Monthly: $62.83
   ```

   **Option 2: Business Hours Only (8AM-8PM)**
   ```
   50 units × 12 hours/day instead of 24/7
   Monthly Cost: $270.00 (50% savings)
   Total Monthly: $278.83
   ```

   **Option 3: No Provisioned Concurrency**
   ```
   Use regular Lambda with cold starts
   Monthly Cost: ~$2-5 for compute + requests
   Total Monthly: $10.83 (98% savings)
   ```

8. **Production Recommendations**

    **For Development/Testing:**
    - Use **Option 3** (No Provisioned Concurrency): **$10.83/month**
    
    **For Production (Low Traffic):**
    - Use **Option 1** (5 Provisioned Concurrency): **$62.83/month**
    
    **For Production (High Performance):**
    - Use **Option 2** (Business Hours Only): **$278.83/month**

{{%notice warning%}}
**Critical Cost Alert**: Your current configuration costs **$548.83/month** - this is primarily due to 50 Provisioned Concurrency units running 24/7. Consider reducing to 5-10 units or implementing time-based scheduling for significant savings.
{{%/notice%}}

{{%notice tip%}}
**Cost Optimization Impact**:
- **Current setup**: $548.83/month
- **Optimized for testing**: $10.83/month (98% savings)
- **Optimized for production**: $62.83/month (89% savings)
{{%/notice%}}