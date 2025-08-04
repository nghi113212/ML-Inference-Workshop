---
title : "Install Postman"
date : "2025-07-27"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

## Overview

**Postman** is an essential tool for testing and developing APIs. In this ML Inference workshop, you'll use Postman to:

- **Test ML API endpoints** deployed on AWS API Gateway
- **Send inference requests** with sample data to your serverless ML model
- **Verify response times** to ensure sub-100ms latency requirements
- **Test authentication** and security configurations
- **Monitor API behavior** under different load conditions

### Why Postman for ML APIs?

- **Quick Testing**: Send POST requests with JSON payloads containing features for prediction
- **Response Analysis**: View model predictions and response metadata
- **Performance Monitoring**: Check response times and debug latency issues
- **Collection Management**: Save ML inference requests for different use cases
- **Environment Variables**: Switch between development, staging, and production endpoints

---

## Instructions

1. Visit the official Postman download page:  
   👉 https://www.postman.com/downloads/

2. Choose the correct version for your operating system:

   - **Windows**: `.exe` installer
   - **macOS**: `.zip` or `.dmg` file  
   - **Linux**: `.tar.gz` or AppImage

3. Install and launch Postman. You can sign in or click "Skip and take me to the app".

4. **Key Features for ML API Testing**:

   - **Request URL**: Enter your API Gateway endpoint
   - **Method**: Use POST for ML inference requests
   - **Headers**: Set Content-Type: application/json
   - **Body**: Include JSON with features for model prediction
   - **Tests**: Add scripts to validate response format and latency

5. **Create Collections for ML Testing**:
   
   - ML Inference - Fraud Detection
   - Performance Tests
   - Error Handling Tests
   - Cache Validation Tests

