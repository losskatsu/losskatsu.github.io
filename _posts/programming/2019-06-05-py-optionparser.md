---
title: "[Python] 명령행 옵션 추가(OptionParser), add_option " 
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

## 1. OptionParser 

* 사용법

```python
from optparse import OptionParser
```

## 2. add_option

parameter | option & meaning
----------|-----------------
dest | argument가 저장될 변수이름
help | option에 대한 help messege(ex: %default, %prog)
metavar | help message에서 argument를 표현할때 쓰임
metavar | dest의 default 값 표현
action | default는 store <br /> store : argument 저장 <br /> store_true : option 설정되면 true로 저장 <br /> store_false : option 설정되면 false로 저장
type | int, float, string, complex, choice

## 3. parse_args()

```python
(options, args) = parser.parse_args()
```

parsing한 옵션값을 변수로 불러오기 위해 options에 넣어줌.

### Example

```python
if __name__ == '__main__':
  parser = OptionParser()
  parser.add_option("-c", "--targetdate", dest="targetdate", action="store")
  (options, args) = parser.parse_args()
```
