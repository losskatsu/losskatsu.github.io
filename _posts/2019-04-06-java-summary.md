---
title: "[Java] 자바 기초 간단 정리" 
categories:
  - Programming
tags:
  - Programming
  - Java
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 자바(Java) 기초 간단 정리

참고자료 : 윤성우의 열혈 자바 프로그래밍

* 자바에서 정한 규칙: 프로그램의 시작은 main함수부터 시작됨.
* 값을 반환하는 메소드와 반환하지 않는 메소드(void) 존재
* 프로그램의 구성
  * 데이터 : 프로그램상에서 유지하고 관리해야 할 데이터
  * 기능 : 데이터를 처리하고 조작하는 기능.
* 클래스 = 데이터 + 기능(메소드)

## 접근 수준 
* 클래스
  * public: 어디서든 인스턴스 생성 가능
  * default: 동일 패키지로 묶인 클래스 내에서만 인스턴스 생성 허용
* 인스턴스 멤버 대상
  * public > protected > default > private
 
지시자 | 클래스내부 | 동일패키지 | 상속 받은 클래스 | 이외의영역
------|----------|-----------|---------------|----------
private | O | X | X | X 
default | O | O | O | O
protected | O | O | O | X
public | O | O | O | O

* 클래스 변수에 static 선언 - 선언된 클래스의 인스턴스가 공유

## 메소드 오버로딩 

호출된 메소드를 찾알 때 참고하는 두 가지 정보는 메소드의 이름, 메소드의 매개변수 정보이다. 
따라서 이 둘 중 하나의 형태가 다른 메소드를 정의하는 것이 가능하다. 
즉, 메소드 이름은 동일하지만 매개변수 정보가 다른 메소드 정의 가능.

```java
class MyHome{
  void mySimpleRoom(int n){...}
  void mySimpleRoom(int n1, int n2){...}
  void mySimpleRoom(double d1, double d2){...}
}
```

* this를 이용한 인스턴스 변수 접근

```java
class SimpleBox{
  private int data;
  SimpleBox(int data){
    this.data = data; // this.data는 어느 위치에서 건 인스턴스 변수 data를 의미함
    // this.data에서 data는 private int data에서의 data를 의미하고,
    // = data에서 data는 SimpleBox(int data)에서의 data를 의미한다.
  }
}
```

## 상속
* 연관된 일련의 클래스들에 대해 공통적인 규악을 정의할 수 있음.

## 인터페이스
* 메소드의 몸체를 가지지 않는다.

