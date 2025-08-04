---
title: "Install AWS CLI"
date : "2025-07-27"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

## Overview

AWS CLI (Command Line Interface) is the official command-line tool for managing AWS resources directly from the terminal. In this workshop, it will be used to connect to Elastic Container Registry to push model image from docker.

---

## Installation

### Step 1: Download and Install

Visit the official AWS CLI installation page:
👉 **https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html**

**For Windows:**
- Download the `.msi` installer and run it

**For macOS:**
```bash
brew install awscli
```

**For Linux (Ubuntu/Debian):**
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### Step 2: Verify Installation

```bash
aws --version
```

Expected output: `aws-cli/2.x.x Python/3.x.x`

---

## Configuration

### Create IAM User (Recommended)

{{% notice warning %}}
**Security:** Don't use your root AWS account credentials. Create an IAM user instead.
{{% /notice %}}

### Configure CLI

```bash
aws configure
```

Enter your credentials:
```
AWS Access Key ID: [Your Access Key]
AWS Secret Access Key: [Your Secret Key]
Default region name: us-east-1
Default output format:
```
