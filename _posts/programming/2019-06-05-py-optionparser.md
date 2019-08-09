---
title: "[Python] 파이썬 명령행 옵션 추가 argparse, optparse  " 
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

# 파이썬 명령행 옵션 추가 argparse, optparse


## 1. argparse

* 사용법

```python
from argparse import ArgumentParser

parser = ArgumentParser()
parser.add_argument('-a', '--application', type = str, required = True, help = 'application name')
parser.add_argument('-t', '--datetime', type=str, help = 'format: YYYY-mm-ddTHH:MM:SS')
parser.add_argument('-d', '--destination', type=str, help = 'alpha or real')

```



## 2. OptionParser 

* 사용법

```python
from optparse import OptionParser
```

### 2-1. add_option

parameter | option & meaning
----------|-----------------
dest | argument가 저장될 변수이름
help | option에 대한 help messege(ex: %default, %prog)
metavar | help message에서 argument를 표현할때 쓰임
metavar | dest의 default 값 표현
action | default는 store <br /> store : argument 저장 <br /> store_true : option 설정되면 true로 저장 <br /> store_false : option 설정되면 false로 저장
type | int, float, string, complex, choice

## 2-2. parse_args()

```python
(options, args) = parser.parse_args()
```

parsing한 옵션값을 변수로 불러오기 위해 options에 넣어줌.

## 2-3. Example

```python
from optparse import OptionParser

if __name__ == '__main__':
  parser = OptionParser()
  parser.add_option("-c", "--targetdate", dest="targetdate", action="store")
  (options, args) = parser.parse_args()
```

## 3. argparse vs optparse

그렇다면 둘 중 어느 방식을 선호할까? 
대체적으로 argparse를 더 많이 사용한다. 
왜냐면 호환성 측면에서 optparse는 파이썬2 버전에서 호환되지 않는다고 알고있다. 
