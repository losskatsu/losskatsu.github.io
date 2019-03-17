---
title: "행렬식(determinant)의 의미" 
categories:
  - LinearAlgebra
tags:
  - Statistics
  - MachineLearning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---

## 행렬식(determinant)의 의미

행렬식의 의미를 알기 위해 위키백과를 검색하면 아래와 같은 결과가 나옵니다.
<br />

선형대수학에서, 행렬식(determinant)은 정사각행렬에 수를 대응시키는 함수의 하나이다. 
대략, 정사각행렬이 나타내는 선형변환이 부피를 확대시키는 정도를 나타낸다. 
<br />

### 1. determinant

행렬식은 영어로 determinant라고 합니다. 
영어사전에서 determinant를 찾아보면, '결정요인' 이라는 뜻이 나옵니다. 
잘은 모르겠지만 뭔가 '결정적인 역할을 하는' 느낌이 듭니다. 

### 2. 2 by 2

먼저 간단하게 $2 \times 2$ 행렬을 살펴봅시다. 

### 3. 3 by 3
위 섹션의 개념을 한 차원 확장시키면 바로 $3 \times 3$ 행렬식의 의미를 파악하실 수 있습니다. 
네, $3 \times 3$ 행렬식의 의미는 3차원 공간에서 해당 행렬 속 벡터들로 구성된 3차원 도형의 부피를 의미합니다. 

### 4. n by n
따라서 $n \times n$ 행렬의 행렬식은 n차원 공간의 벡터들로 구성된 도형의 부피라는 것을 알 수 있습니다. 

### 5. 행렬식(determinant)의 의미
앞서 말한 내용을 정리하면 행렬식은 '부피'라고 생각할 수 있습니다. 
그런데, 이 사실로부터 개념을 조금 확장시켜봅시다. 
그렇다면 행렬식이 0이라는 것은 어떤 의미일까요?


