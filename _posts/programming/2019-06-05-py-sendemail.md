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
* smtplib.SMTP() : SMTP 서버가 TLS를 사용하는 경우
* smtplib.SMTP_SSL() : SMTP 서버가 SSL을 사용하는 경우

## SSL, TLS 란 

SSL, TLS는 네트워크를 통해 작동하는 서버에 인증 및 데이터 암호화를 제공하는 암호화 프로토콜. 
SSL 의 취약점을 보완한 TLS 등장. TLS만 사용하도록 권장되지만, 
사람들은 SSL을 오랜기간 사용해왔으므로 SSL이라는 단어를 더 자주 사용함. 
