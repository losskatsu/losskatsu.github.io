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
나는 2019년 3월 7일부터 3월 20일까지의 데이터를 tableA라는 테이블에서 삭제하고 싶었다. 

```sql
delete from tableA where dt between '2019-03-07' and '2019-03-20'
```

하지만 아래와 같은 에러가 뜨는데

> Error Code: 1175. You are using safe update mode and you tried to update a table without 
a WHERE that uses a KEY column To disable safe mode. toggle the option in Preferences -> SQL Editor and reconnect

## 1.첫번째 방법

위 에러 메시지 처럼 Edit -> Preferences 로 이동하여 
아래 그림에서 노란 체크박스를 해제하는 것이 첫번째 방법이다. 
(기본적으로는 체크되어 있을 것이다.)

![Figure1](/assets/images/sqldeleterow/sqldeleteoption.PNG)

하지만 이 방법은 옵션을 바꿀때마다 재시작을 해야하니 나는 다른 방법을 썼다. 

## 2.두번째 방법
 
두번째 방법으로 임시적으로만 옵션해제 하는 방법을 사용하자. 
사용법은 쿼리를 날리기 전에 아래와 같은 한 문장을 삽입하는 것이다.

```sql
set sql_safe_updates=0;
delete from tableA where dt between '2019-03-07' and '2019-03-20'
```
이렇게 하면 문제없이 해당 행(row)삭제 가능하다.
