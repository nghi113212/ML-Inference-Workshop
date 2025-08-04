---
title : "Install Docker Desktop"
date : "2025-07-27"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

## Overview

**Docker Desktop** is essential for this ML Inference workshop because AWS Lambda supports **container-based deployments**. You'll use Docker to:

- **Package ML models** with their dependencies into containers
- **Test locally** before deploying to AWS Lambda
- **Build optimized images** for faster cold starts
- **Manage Python dependencies** and ML libraries efficiently
- **Ensure consistent environments** between development and production

### Why Containers for ML Inference?

- **Larger Package Sizes**: ML libraries like scikit-learn, numpy exceed Lambda's 250MB limit
- **Dependency Management**: Complex ML dependencies are easier to manage in containers
- **Performance Optimization**: Pre-built images reduce cold start times
- **Reproducible Deployments**: Same environment across dev, staging, and production

---

## Installation Instructions

### 1. Download Docker Desktop

Visit the official Docker website:  
👉 https://www.docker.com/products/docker-desktop/

![Docker](/images/2.Prerequiste/2.3-docker.png)

Choose your operating system:
- **Windows**: Docker Desktop for Windows (requires WSL2)
- **macOS**: Docker Desktop for Mac (Intel or Apple Silicon)
- **Linux**: Docker Desktop for Linux

### 2. System Requirements

**Windows:**
- Windows 10/11 64-bit (Pro, Enterprise, Education)
- WSL2 feature enabled
- 4GB RAM minimum

**macOS:**
- macOS 10.15 or newer
- 4GB RAM minimum

**Linux:**
- 64-bit kernel and CPU virtualization support
- 4GB RAM minimum

### 3. Installation Process

1. **Download** the installer from the official website
2. **Run** the installer with administrator privileges
3. **Restart** your computer when prompted
4. **Launch** Docker Desktop and complete initial setup

### 4. Verify Installation

Open terminal/command prompt and run:

```bash
docker --version
docker run hello-world
```

You should see Docker version information and a successful test run.
