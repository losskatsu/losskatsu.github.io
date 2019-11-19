---
title: "[Java] 자바 롬복(lombok) 라이브러리 정리" 
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

# 자바(Java) 롬복(lombok) 라이브러리 정리

## 롬복(lombok) 라이브러리란

롬복 라이브러리는 자바코드 컴파일 시 자동으로 접근자(get)/설정자(set) 함수를 추가할 수 있는 라이브러리 입니다. 

## 롬복(lombok) 사용 전

아래 코드와 같이 일반적인 자바 프로그래밍을 할때 클래스 변수마다 일일이 get, set 함수를 지정해줘야하는데요. 

```java
public class Student {
    private String name;

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Student [name=" + name + "]";
    }    
}
```

롬복(lombok) 라이브러리를 이용하면 어노테이션 설정으로 get/set 함수를 따로 만들지 않고 바로 사용 가능합니다. 
maven 환경에서는 dependency를 가져오기 위해 아래와 같이 추가 설정을 해 주시구요.

```java
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.16.10</version>
</dependency>
```

## 롬복 사용 후

실제 사용법은 아래와 같이 @Data 어노테이션만 해주면 됩니다.

```java
import lombok.Data;

@Data
public class Student {
    private int id;
}
```

위 코드만 작성만으로 setId(int), getId() 함수가 자동으로 생성 됩니다.  

## 어노테이션 종류

* @Data
* @NoArgsConstructor: 파라미터가 없는 생성자 생성
* @AllArgsConstructor: 모든 필드를 파라미터로 가지는 생성자 생성
* @RequiredArgsConstructor: 기본값이 없고 @NonNull 어노테이션이 붙은 필드를 파라미터로 입력받는 생성자 생성 


