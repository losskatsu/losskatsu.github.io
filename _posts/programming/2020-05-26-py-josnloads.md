---
title: "[python] 파이썬으로 웹페이지 json형식 데이터 가져오기" 
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

# 파이썬으로 웹페이지 json형식 데이터 가져오기

파이썬을 활용해 웹사이트 내용을 가져오는 법을 알아보겠습니다. 
우선 필요한 라이브러리를 불러오겠습니다. 

```python
import json
import urllib.request
```

네이버 메인화면 데이터를 불러와보겠습니다.

```python
>>> url = 'https://www.naver.com'
>>> jsonurl = urllib.request.urlopen(url)
>>> byte_data = jsonurl.read()
>>> text_data = byte_data.decode('utf-8')
<!doctype html>             <html lang="ko"> <head> <meta charset="utf-8"> <title>NAVER</title> <meta http-equiv="X-UA-Compatible" content="IE=edge"> <meta name="viewport" content="width=1190"> <meta name="apple-mobile-web-app-title" content="NAVER"/> <meta name="robots" content="index,nofollow"/> <meta name="description" content="네이버 메인에서 다양한 정보와 유용한 컨텐츠를 만나 보세요"/> <meta property="og:title" content="네이버"> <meta property="og:url" content="https://www.naver.com/"> <meta property="og:image" content="https://s.pstatic.net/static/www/mobile/edit/2016/0705/mobile_212852414260.png"> <meta property="og:description" content="네이버 메인에서 다양한 정보와 유용한 컨텐츠를 만나 보세요"/> <meta name="twitter:card" content="summary"> <meta name="twitter:title" content=""> <meta name="twitter:url" content="https://www.naver.com/"> <meta name="twitter:image" content="https://s.pstatic.net/static/www/mobile/edit/2016/0705/mobile_212852414260.png"> <meta name="twitter:description" content="네이버 메인에서 다양한 정보와 유용한 컨텐츠를 만나 보세요"/> <link rel="stylesheet" href="https://pm.pstatic.net/dist/css/nmain.20200522.css"> <link rel="stylesheet" href="https://ssl.pstatic.net/sstatic/search/pc/css/api_atcmp_200326.css"> <link rel="shortcut icon" type="image/x-icon" href="/favicon.ico?1"/>  <script type="text/javascript" src="https://pm.pstatic.net/dist/lib/nelo.20191018.js" defer="defer"></script> <script>document.domain="naver.com",window.nmain=window.nmain||{},window.nmain.gv=window.nmain.gv||{},window.nmain.supportFlicking=!1;var nsc="navertop.v4",ua=navigator.userAgent;window.nmain.isIE=navigator.appName&&0<navigator.appName.indexOf("Explorer")&&ua.toLocaleLowerCase().indexOf("msie 10.0")<0,document.getElementsByTagName("html")[0].setAttribute("data-useragent",ua)</script> <script>window.nmain.isIE&&(Object.create=function(n){function t(){}return t.prototype=n,new t})</script> <script>
```

이번에는 json 형식의 데이터를 불러와보겠습니다.

```python
>>> url = 'https://python.bakyeono.net/data/movies.json'
>>> text_data = urllib.request.urlopen(url).read().decode('utf-8')
>>> movies = json.loads(text_data)
```
불러온 데이터를 확인하면 아래와 같습니다.

```python
>>> movies
[{'title': 'Interstella',
  'genre': 'SF',
  'year': 2014,
  'starring': ['M. McConaughey', 'A. Hathaway', 'J. Chastain']},
 {'title': 'Braveheart',
  'genre': 'Drama',
  'year': 1995,
  'starring': ['M. Gibson', 'S. Marceau', 'P. McGoohan']},
 {'title': 'Mary Poppins',
  'genre': 'Fantasy',
  'year': 1964,
  'starring': ['J. Andrews', 'D. Van Dyke']}]
```

json의 첫번째 항목을 알아볼까요

```python
>>> movies[0]
{'title': 'Interstella',
 'genre': 'SF',
 'year': 2014,
 'starring': ['M. McConaughey', 'A. Hathaway', 'J. Chastain']}
```

json의 첫번째 항목의 title을 알아봅시다. 

```python
>>> movies[0]['title']
'Interstella'
```
