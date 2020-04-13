---
title: "뉴턴-랩슨(Newton-Raphson) 개념 정리" 
categories:
  - statistics
tags:
  - statistics
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

# 뉴턴-랩슨(Newton-Raphson) 개념 정리

## 뉴턴-랩슨 정의

> 수치해석학에서, 뉴턴-랩슨 방법은 실수값 함수의 영점을 근사하는 방법의 하나이다. 

쉽게 말해, 뉴턴 랩슨 방법은 컴퓨터계산을 이용해 함수해를 구하는데, 정확하기 구하기는 힘드니 근사값을 구하는 방법입니다. 
이 방법은 흔히 손으로 구하기 힘든 방정식의 해를 구할때 컴퓨팅계산을 이용해 근사적인 해를 구합니다. 

$$ x^{n+1} = x^{n} - \frac{f(x^{n})}{f\prime(x^{n})} $$

