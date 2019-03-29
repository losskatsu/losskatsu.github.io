---
title: "내적(inner product), 정사영(projection)의 의미" 
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

## 내적(inner product)의 의미

작성 중인 문서입니다. 

내적은 기본적으로 연산이라고 생각하시면 쉽습니다. 
흔히 생각할 수 있는 연산이라고 하면 더하기, 빼기, 곱하기, 나누기 정도가 있는데, 
내적도 이러한 연산 중 하나라고 생각하시면 편합니다. 
특이한 점은 내적은 벡터와 벡터의 연산인데 결과가 스칼라라는 점입니다. 

### 내적의 정의 

앞서 내적은 연산이라고 말씀드렸습니다.
그럼 간단히 내적이 어떤 연산인지 확인해 봅시다.

$$ \langle \mathbf{u}, \mathbf{v} \rangle = \mathbf{u} \cdot \mathbf{v} =  u_{1}v_{1} + u_{2}v_{2} + \dots + u_{n}v_{n} $$

이 내적이라는 연산을 사용하면, 
우리가 흔히 알고있는 한 벡터의 norm을 구한다던가, 두 벡터 사이의 거리를 측정하는데 이용할 수 있습니다.  

벡터 $\mathbf{v}$의 norm 
<br />
$$ \parallel \mathbf{v} \parallel = \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}  $$

벡터 $\mathbf{u}$, $\mathbf{v}$ 사이의 거리 
<br />
$$ d(\mathbf{u}, \mathbf{v}) = \parallel \mathbf{\mathbf{u} - \mathbf{v}} \parallel = \sqrt{\langle \mathbf{u} - \mathbf{v}, \mathbf{u} - \mathbf{v} \rangle}  $$


물리 법칙에서의 내적

수직

정사영
