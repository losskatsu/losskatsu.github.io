---
title: "[자바스크립트] map, reduce, filter" 
categories:
  - frontend
tags:
  - frontend
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---


# nodejs와 자바스크립트(javascript) 차이

## 1. 서론

보통 배열이 주어졌을때 각 원소를 순회하며 방문할때는 for문을 사용합니다.
그러나 for문 말고도 map, reduce, filter와 같은 메소드를 사용하면 
배열을 이용한 작업을 간단히 할 수 있습니다. 
오늘은 map, reduce, filter에 대해 알아보겠습니다. 

## 2. map

## 2.1. map 간단히 사용하기

map은 인풋으로 배열을 받고 아웃풋으로 배열을 내놓습니다. 
즉, map을 이용하면 기존 배열을 이용해 새로운 배열을 만드는 것이 가능합니다. 

```javascript
>> const numbers1 = [1,2,3,4,5];
>> const numbers2 = numbers1.map(val => val*2);
>> console.log(numbers2) 
Array(5) [ 2, 4, 6, 8, 10 ]
```

위 코드는 map 메소드를 이용해 기존 배열인 numbers1의 각 원소에 2를 곱해 
새로운 배열 numbers2를 만드는 코드입니다. 
map 메소드 내부를 보면 val이라는 것이 있는데, 
이는 map 메소드 안에서 사용되는 매개변수이고 이는 다른 이름으로 설정가능합니다. 
map 메소드 안에서 만들어진 val는 배열의 원소 순서대로 방문합니다. 
즉, val는 차례로 1, 2, 3, 4, 5를 방문하고 각 값에 2를 곱한 후 새로운 val이 되는 것입니다. 

## 2.2. map 풀버전

사실 map 메소드의 매개변수는 value하나만 들어가는게 아니라 다음과 같이 
value, index, array가 들어갑니다. 
value는 배열의 원소를 의미하며, index는 해당 원소의 인덱스를 의미합니다. 
그리고 array는 이름처럼 배열을 의미합니다. 
map 메소드의 풀버전을 사용하면 다음과 같습니다. 

```javascript
>> const numbers1 = [1,2,3,4,5];
>> const numbers3 = numbers1.map((value, index, array) => 
      {console.log(value, index, array); 
      return value*2;})      
```
```javascript
1 0 Array(5) [ 1, 2, 3, 4, 5 ]
2 1 Array(5) [ 1, 2, 3, 4, 5 ]
3 2 Array(5) [ 1, 2, 3, 4, 5 ]
4 3 Array(5) [ 1, 2, 3, 4, 5 ]
5 4 Array(5) [ 1, 2, 3, 4, 5 ]
4 3 Array(5) [ 1, 2, 3, 4, 5 ]
```
```javascript
>> console.log(numbers3)
Array(5) [ 2, 4, 6, 8, 10 ]
```



## 3. reduce
