---
title : "ECR"
date : "2025-07-28" 
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---

Amazon Elastic Container Registry (ECR) is a fully managed Docker container registry that makes it easy to store, manage, and deploy Docker container images. In this workshop, ECR serves as the central repository for our machine learning model container, which packages our sentiment analysis model with all its dependencies. ECR integrates seamlessly with AWS Lambda, allowing us to deploy containerized ML models that are too large or complex for traditional Lambda deployment packages. This approach provides better dependency management, faster cold start times for ML workloads, and easier versioning of our model deployments.