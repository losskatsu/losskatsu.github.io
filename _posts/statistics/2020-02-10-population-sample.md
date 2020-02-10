---
title: "[기초통계] 모집단과 표본의 의미" 
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

# 모집단과 표본의 의미

## 1. 모집단(population)과 모수(population parameter)

### 1-1. 모집단(population)

모집단의 뜻은 아래와 같습니다.

> 모집단(population)이란 정보를 얻고자 하는 관심 대상의 전체집합을 말한다. 

쉽게 말해, 모집단은 집단 전체를 말한다고 할 수 있습니다. 
예를 들어, 어떤 게임 유저들의 하루 평균 플레이 타임을 분석하고 싶을 경우, 모집단은 해당 게임을 플레이하는 유저 전체의 플레이 타임이 됩니다. 

### 1-2. 모수(population parameter)

> 모수(population parameter)란 모집단 분포 특성을 규정 짓는 척도. 관심의 대상이 되는 모집단의 대표값을 말한다.

위의 예에서 전체 유저의 하루 평균 플레이 타임이 60분 일 경우 모수는 60분이 됩니다.

## 2. 표본(sample)과 표본통계량(sample statistic)

### 2-1. 표본(sample)

표본의 뜻은 아래와 같습니다.

> 표본(sample)은 모집단(population)의 부분집합이다.

즉, 표본은 모집단의 일부분이라고 할 수 있습니다. 

### 2-2. 표본통계량(sample statistic)

> 표본통계량(sample statistic)이란 표본의 몇몇 특징을 수치화한 값이다.

## 3. 모집단과 표본의 관계

## 4. 용어의 잘못된 사용

흔히 실무에서 '모수'라는 용어를 잘못 사용하는 경우가 있는데요. 
모수를 샘플 수라는 뜻으로 사용하는 경우를 종종 봅니다. 
예를 들어 쿼리를 날려 데이터베이스에 존재하는 데이터를 조회했을 때 1,000 건이 조회되었다고 합시다. 
이 경우, "모수가 1,000 이다."라는 표현을 사용하곤 하는데요. 
이는 틀린 표현입니다. 위에서 설명드렸듯, 모수는 모집단의 대표값을 의미하는 것이지 샘플 수를 의미하는 것이 아닙니다. 
다른 틀린 표현으로는 "모수가 작다", "모수가 크다" 등이 있습니다. 
