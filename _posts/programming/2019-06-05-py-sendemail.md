---
title: "[Python] 파이썬으로 이메일(email) 보내기 " 
categories:
  - programming
tags:
  - python
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 파이썬으로 이메일 보내기

```python
import smtplib
from email import utils
from email.mime.text import MIMEText
```

* SMTP : Simple Mail Transfer Protocal 
