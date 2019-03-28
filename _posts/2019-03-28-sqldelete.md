---
title: "[SQL] DB 테이블의 행 삭제가 안될 때" 
categories:
  - ITinfra
tags:
  - ITinfra
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# [SQL] DB 테이블의 행 삭제가 안될 때

DB 테이블에서 특정 행을 삭제하고 싶어 아래와 같은 명령어를 입력했다. 

```
delete from tableA where dt between '2019-03-07' and '2019-03-20'
```

하지만 아래와 같은 에러가 뜨는데

> Error Code: 1175. You are using safe update mode and you tried to update a table without 
a WHERE that uses a KEY column To disable safe mode. toggle the option in Preferences -> SQL Editor and reconnect

위 에러 메시지 처럼 Edit -> Preferences 로 이동하여 
아래 그림에서 노란 체크박스를 해제하는 것이 첫번째 방법이다. 

