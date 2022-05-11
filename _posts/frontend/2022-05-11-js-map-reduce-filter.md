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


# 자바스크립트 - map, reduce, filter

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

마지막으로 기억해주세요. 
map의 인풋은 배열이고, 아웃풋도 배열이라는 사실을! 

## 3. reduce

### 3.1. reduce 간단히 사용하기 

reduce 메소드는 앞서 배운 map과는 달리 
인풋으로 배열을 받고 아웃풋으로 배열이 아닌 하나의 값을 내놓습니다. 
reduce는 배열 원소의 덧셈을 할때 많이들 사용하는데
한번 예를 들어 보겠습니다. 

```javascript
>> const numbers1 = [1,2,3,4,5];
>> const sumArray = numbers1.reduce((acc, current)=>{
      console.log(acc, current, acc+current); 
      return acc+current;
      });
```
```javascript
1 2 3
3 3 6
6 4 10
10 5 15
```
```javascript
>> console.log(sumArray)
15
```

위 코드를 보면 acc는 accumulator라고 해서 누적된 값을 저장하는 매개변수입니다. 
결과를보면 첫번째 acc값은 1이 되는데 이는 배열의 첫번째 값에 해당합니다. 
누적된 것이 없으므로 배열의 첫번쨰 값을 지정하는 것입니다. 
그리고 current는 현재값을 의미하는데 첫번째 값이 acc값으로 들어갔으므로 
current값은 첫번째 원소가 아닌 두번쨰 원소부터 차례로 방문합니다. 
그래서 acc값과 current값을 더한 값이 다시 acc값으로 저장됩니다. 

### 3.2. reduce 초기값 사용하기

앞서 사용한 reduce에서는 acc의 초기값을 따로 설정하지 않았습니다. 
이번에는 acc의 초기값을 1000으로 설정해 보겠습니다. 

```javascript
>> const numbers1 = [1,2,3,4,5];
>> const sumArray2 = numbers1.reduce((acc,current)=>{
      console.log(acc,current,acc+current); 
      return acc+current;},1000);
```
```javascript
1000 1 1001
1001 2 1003
1003 3 1006
1006 4 1010
1010 5 1015
```
```javascript
>> console.log(sumArray2)
1015
```

위 코드를 보면  acc의 초기값이 1000으로 시작되는 것을 알 수 있습니다. 
그리고 acc의 초기값이 따로 설정되는 경우 current값은 두번째 원소부터 시작하는 것이 아닌
첫번째 원소부터 시작되는 점이 다르다는 것을 알 수 있습니다.

## 4. filter

### 4.1. filter 간단히 사용하기

filter 메소드는 인풋으로 배열을 받고 아웃풋으로 배열을 내놓는 메소드 입니다. 
filter 메소드는 이름 그대로 배열을 받아서 특정 조건으로 각 원소를 검사한 후 
조건에 맞는 원소들만 출력해줍니다. 

```javascript
>> const numberArray = ['one', 'two','three','four','five'] 
>> const numberFilter = numberArray.filter(val => val.length > 3);
>> console.log(numberFilter)
Array(3) [ "three", "four", "five" ]
```

위 예제는 배열의 원소 중 길이가 3보다 큰 원소들만 골라서 출력해주는 코드입니다. 

### 4.2. filter 풀버전 

filter 메소드도 map 메소드와 같이 풀버전이 존재합니다. 
매개변수는 value, index, array를 사용하는데, 
value는 배열의 원소를 의미하며 index는 해당 원소의 인덱스, 그리고 array는 배열을 의미합니다. 

```javascript
>> const numberArray = ['one', 'two','three','four','five']
>> const numberFilter3 = numberArray.filter((val, idx, array) =>{
        console.log(val,idx,array); 
        return val.length > 4;});
```
```javascript
one 0 Array(5) [ "one", "two", "three", "four", "five" ]
two 1 Array(5) [ "one", "two", "three", "four", "five" ]
three 2 Array(5) [ "one", "two", "three", "four", "five" ]
four 3 Array(5) [ "one", "two", "three", "four", "five" ]
five 4 Array(5) [ "one", "two", "three", "four", "five" ]
```
```javascript
>> console.log(numberFilter3)
Array [ "three" ]
```


