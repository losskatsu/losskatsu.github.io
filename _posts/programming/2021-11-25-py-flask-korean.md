---
title: "[python] Flask 한글 POST 요청 받기" 
categories:
  - programming
tags:
  - programming
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# Flask 한글 POST 요청 받기

참고링크
* [아나콘다로 가상환경 설치하기(윈도우)](https://losskatsu.github.io/programming/py-conda/)
* [파이썬 가상환경 설치하기(우분투)](https://losskatsu.github.io/programming/pyenv/)
* [파이썬 가상환경 설치하기(centOS6)](https://losskatsu.github.io/it-infra/pyenv-centos6/)
* [mysql 설치하기](https://losskatsu.github.io/it-infra/mysql-index/)
* [파이썬과 DB 연동하기](https://losskatsu.github.io/programming/py-db-conn/)
* [Flask를 이용한 api 서버 구축(1)](https://losskatsu.github.io/programming/py-flask01/) 
* [Flask를 이용한 api 서버 구축(2)](https://losskatsu.github.io/programming/py-flask02/)


## 1. 개요

flask로 API 서버를 만들었을때 한글을 받아야하는 경우가 있는데요. 
flask는 요청 데이터를 기본적으로 아스키코드로 받기 때문에 한글을 받을 수 없습니다. 
따라서 flask로 한글을 받기 위해서는 보내는 쪽에서 인코딩한 다음에 
인코딩한 바이트 코드를 문자열로 처리한 후 해당 문자열을 받아 디코딩 해야합니다.
그렇다면 바이트 코드 문자열은 어떻게 디코딩할 수 있을까요? 
이것은 urllib 라이브러리를 활용하면 가능합니다. 


## 2. (서버) Flask 한글 POST 요청 받기

플라스크로 한글을 받기 위해 다음과 같이 서버를 올립니다. 

```python
from flask import Flask, request, jsonify
from urllib import parse

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

@app.route("/test", methods=['POST'])
def test():
    args = request.json
    string = args['review']
    string = parse.unquote(string, 'utf8')
    return string

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5001)
```
```
* Serving Flask app '__main__' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off

 * Running on all addresses.
   WARNING: This is a development server. Do not use it in a production deployment.
 * Running on http://10.1.55.81:5001/ (Press CTRL+C to quit)
10.1.55.81 - - [25/Nov/2021 14:58:36] "POST /test HTTP/1.1" 200 -
```

## 3. (클라이언트) 한글 보내기 

클라이언트에서는 한글을 보냅니다. 
이때 한글 원문을 그대로 보내면 안되고 인코딩 한 후에 보냅니다. 

```bash
C:\Users> curl -d "{""review"":""%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94""}" 
-H "Content-Type: application/json" -X POST http://10.1.55.81:5001/test

안녕하세요
```

한글이 잘 보내지는 것을 알 수 있습니다. 

## 4. 인코딩, 디코딩 

이번에는 인코딩과 디코딩에 대해 알아보겠습니다. 

```python
s1 = '안녕하세요'
print(s1)
```
```
안녕하세요
```

위와 같은 문자열을 인코딩해보겠습니다.

```python
from urllib import parse
s2 = parse.quote(s1)
print(s2)
```
```
%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94
```

인코딩 함수는 quote와 quote_plus가 있습니다. 
두 함수의 차이는 quote는 띄어쓰기를 '%20'으로 처리하는 반면 
quote_plus는 띄어쓰기를 '+'기호로 처리합니다.  
 
먼저 quote 방식을 이용해 인코딩해봅니다.

```python
s3 = '제 이름은 홍길동 입니다.'
s4 = parse.quote(s3)
print(s4)
```
```
%EC%A0%9C%20%EC%9D%B4%EB%A6%84%EC%9D%80%20%ED%99
%8D%EA%B8%B8%EB%8F%99%20%EC%9E%85%EB%8B%88%EB%8B%A4.
```

다음은 quote_plus 방법을 써보겠습니다.

```python
s5 = parse.quote_plus(s3)
print(s5)
```
```
%EC%A0%9C+%EC%9D%B4%EB%A6%84%EC%9D%80+%ED%99%8D
%EA%B8%B8%EB%8F%99+%EC%9E%85%EB%8B%88%EB%8B%A4.
```
quote_plus를 사용하면 띄어쓰기가 '+'기호인 것을 볼 수 있습니다.

```python
parse.unquote(s4)
```
```
'제 이름은 홍길동 입니다.'
```


```python
parse.unquote_plus(s4)
```
```
'제 이름은 홍길동 입니다.'
```


```python
parse.unquote(s5)
```
```
'제+이름은+홍길동+입니다.'
```



```python
parse.unquote_plus(s5)
```
```
'제 이름은 홍길동 입니다.'
```
