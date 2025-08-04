---
title : "VPC"
date : "2025-07-28"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

In this workshop, creating a Virtual Private Cloud (VPC) is an essential step to simulate a real-world network environment on AWS. Instead of relying on the default VPC, building a custom VPC allows you to fully control how services like Lambda, ElastiCache communicate with each other while enhancing the overall security and isolation of your resources. This also helps you gain hands-on experience with network segmentation, internal service connectivity, and security best practices that are commonly used in production systems.

Specifically, creating a VPC provides the following benefits:

- Network isolation: Separates public and private subnets to protect sensitive resources from unauthorized internet access.

- Improved security: Enables precise traffic control through security groups and route tables, keeping services like databases and caches private.

- Real-world networking practice: Allows Lambda functions inside private subnets to securely connect to internal services like ElastiCache without public exposure.

- Production-like architecture: Mirrors how systems are deployed in real-world scenarios, making the workshop more relevant and practical.

- Foundation for more complex setups: Prepares you to implement advanced architectures using NAT Gateways, Load Balancers, and Service Mesh.