---
title: "Install Python"
date : "2025-07-27"
weight: 5
chapter: false
pre: " <b> 2.5 </b> "
---

## Overview

Python is a programming language essential for machine learning model development and deployment. In this workshop, Python will be used to build ML models, create Docker containers, and integrate with AWS services.

In this workshop, authur uses Python version 3.12.4.

---

## Installation

### Step 1: Download and Install Python

Visit the official Python website:
👉 **https://www.python.org/downloads/**

**For Windows:**
- Download Python 3.8+ installer (.exe)
- Check **"Add Python to PATH"** during installation
- Choose **"Install for all users"**

**For macOS:**
```bash
# Using Homebrew (recommended)
brew install python

# Or download from python.org
```

**For Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

### Step 2: Verify Installation

```bash
python --version
# or
python3 --version
```

Expected output: `Python 3.8.x` or higher

```bash
pip --version
# or  
pip3 --version
```
