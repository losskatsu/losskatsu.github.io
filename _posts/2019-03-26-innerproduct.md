---
title: "내적(inner product) 의미" 
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

위와 같은 연산을 벡터의 element들끼리 연산한다라고 생각할 수도 있지만, 
벡터곱으로 생각할 수 있습니다. 

$$ \mathbf{u} = 
\begin{pmatrix}
u_{1} \\
u_{2} \\
\vdots \\
u_{n}
\end{pmatrix}
, \mathbf{v} =
\begin{pmatrix}
v_{1} \\
v_{2} \\
\vdots \\
v_{n}
\end{pmatrix} $$

예를 들어, 위와 같이 두 개의 열벡터가 존재한다고 했을 때, 
두 열벡터의 내적은 아래와 같이 표현할 수 있습니다. 

$$ \mathbf{u} \cdot \mathbf{v} = \mathbf{u}^{T}\mathbf{v} $$

이 내적이라는 연산을 사용하면, 
우리가 흔히 알고있는 한 벡터의 norm을 구한다던가, 두 벡터 사이의 거리를 측정하는데 이용할 수 있습니다.  

벡터 $\mathbf{v}$의 norm, norm은 벡터의 길이(length)라고도 표현합니다. 그리고 norm이 1인 벡터는 unit vector라고 부릅니다.  
<br />

$$ \parallel \mathbf{v} \parallel = \sqrt{\langle \mathbf{v}, \mathbf{v} \rangle}  $$

벡터 $\mathbf{u}$, $\mathbf{v}$ 사이의 거리 
<br />

$$ d(\mathbf{u}, \mathbf{v}) = \parallel \mathbf{\mathbf{u} - \mathbf{v}} \parallel = \sqrt{\langle \mathbf{u} - \mathbf{v}, \mathbf{u} - \mathbf{v} \rangle}  $$


### 내적의 성질

![figure02](/assets/images/innerproduct/innerproduct02.JPG)

위와 같은 성질을 이용하면 아래와 같은 성질을 생각할 수 있습니다. 

$$ \parallel \mathbf{u} + \mathbf{v} \parallel \leq \parallel \mathbf{v} \parallel + \parallel \mathbf{v} \parallel $$


### 물리학 관점으로 보는 내적

원점으로부터 시작되는 두 벡터를 표현하면 두 벡터 사이에는 반드시 각도 $\theta$ 가 존재 할 것입니다. 

![figure01](/assets/images/innerproduct/innerproduct01.JPG)

그리고 위에서 정의했던 내적을 아래와 같은 식으로 표현할 수 있습니다. 

$$ \mathbf{u} \cdot \mathbf{v} = \parallel \mathbf{u} \parallel \parallel \mathbf{v} \parallel cos\theta  $$

위 식을 이용하면 내적과 각도 $\theta$와의 관계를 알 수 있습니다. 

* 내적 > 0 이면, $ \theta < 90 $
* 내적 < 0 이면, $ \theta > 90 $
* 내적 = 0 이면, $ \theta = 90 $

특히 마지막 세번째관계에 주목할 필요가 있습니다. 
내적은 두 벡터간의 수직 여부를 판단하는데 유용하게 쓰일 수 있습니다. 

![figure03](/assets/images/innerproduct/innerproduct03.JPG)

어떤 물체를 각도 $\theta$인 상태의 줄을 잡아당긴다고 하면, 
위 관계가 조금 더 쉽게 이해 될 수 있습니다. 
각도 $\theta$가 90도 보다 작다면 낭비되는 힘이 적으므로, 
더 쉽게 물체를 움직일 수 있고, 
각도가 90도 보다 크다면 원래 움직이고자 하는 방향과 반대방향으로 움직이므로 내적은 음수가 됩니다. 
그리고 90도 방향으로 줄을 잡아 당긴다면 물체는 움직이지 않겠죠. 

이로 부터 우리는 아래와 같은 성질을 추가적으로 알 수 있습니다. 

Cauchy-Schwarz Inequality
<br />

$$ | \mathbf{u} \cdot \mathbf{v} | \leq \parallel \mathbf{u} \parallel \parallel \mathbf{v} \parallel $$

### 정사영

위 개념은 정사영과 연관지을 수도 있습니다. 
다시 한번 내적을 구하는 식을 보시죠. 

$$ \mathbf{u} \cdot \mathbf{v} = \parallel \mathbf{u} \parallel \parallel \mathbf{v} \parallel cos\theta  $$

위 식을 조금 변형하면 

$$ \parallel \mathbf{u} \parallel \parallel \mathbf{v} \parallel cos\theta = 
\parallel \mathbf{u} \parallel ( \parallel \mathbf{v} \parallel cos\theta ) $$

혹은

$$ \parallel \mathbf{u} \parallel \parallel \mathbf{v} \parallel cos\theta = 
( \parallel \mathbf{u} \parallel cos\theta ) \parallel \mathbf{v} \parallel   $$





