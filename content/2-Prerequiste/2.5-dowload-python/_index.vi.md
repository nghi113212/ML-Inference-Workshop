---
title: "Cài đặt Python"
date : "2025-07-27"
weight: 5
chapter: false
pre: " <b> 2.5 </b> "
---

## Tổng quan

Python là ngôn ngữ lập trình cần thiết để phát triển và triển khai các mô hình machine learning. Trong workshop này, Python sẽ được sử dụng để xây dựng ML models, tạo Docker containers, và tích hợp với các dịch vụ AWS.

Trong workshop này, tác giả sử dụng Python phiên bản 3.12.4.

---

## Cài đặt

### Bước 1: Tải và cài đặt Python

Truy cập trang web chính thức của Python:
👉 **https://www.python.org/downloads/**

**Dành cho Windows:**
- Tải Python 3.8+ installer (.exe)
- Tick chọn **"Add Python to PATH"** trong quá trình cài đặt
- Chọn **"Install for all users"**

**Dành cho macOS:**
```bash
# Sử dụng Homebrew (khuyến nghị)
brew install python

# Hoặc tải từ python.org
```

**Dành cho Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

### Bước 2: Kiểm tra cài đặt

```bash
python --version
# hoặc
python3 --version
```

Kết quả mong đợi: `Python 3.8.x` hoặc cao hơn

```bash
pip --version
# hoặc
pip3 --version
```
