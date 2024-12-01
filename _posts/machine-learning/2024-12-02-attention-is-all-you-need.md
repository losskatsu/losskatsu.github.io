---
title: "[딥러닝] Attention is all you need 논문 번역" 
categories:
  - machine-learning
tags:
  - machine-learning
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
sidebar:
  title: "AI Machine Learning"
  nav: sidebar-contents
---


# Attention is all you need 논문 번역

## 0. Abstract

대부분의 시퀀스 변환 모델들은 복잡한 순환신경망(RNN)이나 합성곱신경망(CNN)을 기반으로 하는 경우가 많았고, 
이러한 신경망들은 인코더(encoder)와 디코더(decoder)를 포함한다. 
또한 성능이 가장 뛰어난 모델들은 어텐션 메커니즘을 통해 인코더와 디코더를 연결한다. 
우리는 이 논문에서 트랜스포머(Transformer)라는 아주 단순한 신경망 구조를 제안한다. 
이 트랜스포머라는 구조는 RNN이나 CNN은 제거하고 단순히 어텐션 메커니즘을 기반으로 하는 아주 간단한 구조이다. 
우리는 번역 업무를 수행하는 두 종류의 인공지능으로 실험을 했는데, 
트랜스포머 기반의 모델이 품질이 더 우수했으며 병렬처리 하기 좋고, 학습하는 시간도 적게들었다. 
우리 모델은 WMT 2014 영어-독일어 번역 업무에서 28.4 BLEU를 기록했는데, 
이는 기존 기록보다 2 BLEU 이상 좋은 성능을 보여주면서 기존 베스트 기록을 갈아치웠다. 
그리고 WMT 2014 영어-프랑스 번역 업무에서는 단일 모델 기준, 
41.8 BLEU라는 초대 신기록을 달성했는데, 
이는 3.5일 동안 8개의 GPU로 학습한 결과이고 흔히 말하는 베스트 모델에 비해 현저히 적은 리소스로 학습한 것을 의미한다. 
트랜스포머 구조는 대규모 학습 데이터냐 제한된 학습 데이터냐에 상관없이 
영어 구문 분석에서 성공적으로 적용할 수 있음을 보여주었다. 

<br/>

<a href="http://www.yes24.com/Product/Goods/97032765" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00001_ml.png" width="800" align="middle">

<br/>



## 1. Introduction

RNN, LSTM, GRU와 같은 모델들은 언어 모델이나 기계번역과 같은 시퀀스 모델링이나 변환 문제에서 대세로 자리잡았습니다. 
그리고 인코더-디코더 아키텍트를 발전시키기 위한 수많은 사람들의 노력이 있었다. 

순환 모델들은 일바적으로 인풋이나 아웃풋 시퀀스의 기호 위치를 따라 팩터를 계산한다. 
시퀀스의 기호 위치는 계산 과정에서 특정 스텝에 할당딘 후, 
은닉 상태 $h_t$를 생성합니다. 
이때 은닉 상태 $h_t$는 이전 은닉상태 $h_{t-1}$과 현재 시점 $t$에서의 인풋값의 함수이다. 
그러나 이러한 방식으로는 학습과정에서 데이터의 병렬 처리를 어렵게 만들고 시퀀스 길이가 길어질수록 더 큰 문제가 된다.  
왜냐하면 메모리 제약조건이 데이터간 배치를 제한하기 때문이다. 
최근 연구에서는 팩토라이제이션 트릭과 조건부 계산을 활용해 계산 효율성을 높이고, 
조건부 계산의 경우에는 모델 성능도 끌어올렸다. 
그러나 순차적으로 계산된다는 근본적인 제약조건은 여전히 남아있는 상태였다.  

어텐션은 인풋/아웃풋 시퀀스 내의 거리에 상관없이 의존성을 모델링 가능하게 만들어, 
다양한 작업에서 강력한 시퀀스 모델링 통합이나 변환 모델의 필수 요소가 되었다. 
그러나 일부 예외케이스를 제외하면 이러한 어텐션 메커니즘은 대부분 RNN과 함께 사용된다. 

이 연구에서는 RNN을 배제하고, 대신 어텐션 메커니즘만을 사용해 
인풋과 아웃풋 간의 의존성을 모델링하는 Transformer라는 모델 아키텍처를 제안한다. 
Transformer는 병렬 처리를 대폭 향상 시키며, 
8개의 P100 GPU에서 단 12시간의 훈련만으로 번역에서 최고의 성능을 보여준다. 

## 2. Background

순차적 계산을 줄이기 위한 목표는 Extended Neural GPU, ByteNet, ConvS2S와 같은 
모델들의 기반을 형성한다. 
이러한 모델들은 기본적으로 CNN을 사용하며 
모든 인풋/아웃풋 위치에 대해 은닉 표현(hidden representation)을 병렬처리로 계산한다. 
그리고 이러한 모델들은 엄청난 양의 연산을 요구한다. 
왜냐하면 임의의 두 인풋 또는 아웃풋 위치 간의 신호를 연결하는데 필요한 연산 횟수가 
위치간 거리에 따라 증가하기 때문이다. 
ConvS2S는 선형적으로, ByteNet의 경우 로그 함수 형태로 증가한다. 
이는 먼 위치간의 의존성을 학습하는 것을 더 어렵게 만든다. 
반면, 트랜스포머에서는 연산 횟수가 상수형태로 일정하다는 장점이 있지만, 
이를 위해 어텐션 가장치가 적용된 위치를 평균화하기 때문에 
모델이 정보를 구분하고 세밀하게 표현하는 능력이 감소한다는 단점이 있다. 
이러한 효과는 3.2절에서 설명한 Multi-Head Attention을 통해 보완한다. 

Self-attention은 때로 intra-attention이라고도 불리는데, 
이는 하나의 시퀀스 내의 서로 다른 위치들을 연관지어 
그 시퀀스의 표현(representation)을 계산하는 어텐션 메커니즘이다. 
Self-attention은 다양한 역할을 수행하는데, 
예를 들어, 독해, 요약, 텍스트 함의 분석 등과 같은 문장 표현 학습을 포함한 
다양한 역할을 수행한다. 

End-to-end 메모리 네트워크는 시퀀스 정렬된 순환 대신 
순환 어텐션 메커니즘을 기반으로 하며, 
간단한 언어 질문 답변 및 언어 모델링 관련해서는 좋은 성능을 보이는 것으로 알려져있다. 
여기서 시퀀스 정렬(sequence alignment)라는 말은 
입력 시퀀스의 각 위치가 시간 순서대로 단계별로 처리되는 것을 의미한다. 

우리가 아는 한 트랜스포머는 시퀀스 정렬된 RNN이나 합성곱 없이도 
인풋/아웃풋 표현을 계산하기 위해 self-attention만 사용하는 최초의 변환 모델이다. 
다음 섹션에서는 트랜스포머를 설명하고, self-attention을 사용하는 이유를 알아보며, 
다른 모델에 비해 가지는 장점에 대해 논의해보자. 

## 3. Model Architecture

대부분의 뛰어난 신경망 기반 시퀀스 변환 모델들은 인코더-디코더 구조로 구성되어 있다. 
이 구조에서 인코더는 인풋 시퀀스 $x=(x_1, ... , x_n)$를 $z=(z_1, ..., z_n)$로 매핑한다. 
이때 $x$는 ("I","love","you")와 같은 기호 표현을 의미하고, 
$z$는 ((0.2, 0.3, -0.1),(0.5, -0.4, 0.2),(-0.1, 0.8, 0.3))과 같은 연속형 숫자 표현을 의미한다. 
그 후에 디코더는 $z$를 기반으로 출력 시퀀스 $(y_1, ..., y_m)$을 한번에 하나씩 생성한다. 
이때 디코더는 자기회귀(auto-regressive) 방식으로 작동하며, 
이전에 생성된 기호들을 다음 기호를 생성할 때 추가적인 입력으로 사용한다. 

(Figure 1. The Transformer - model architecture)

트랜스포머는 위 그림과 같은 전체적은 구조를 따른다. 
이 트랜스포머는 self-attention을 쌓은 형태와 
각각의 단어가 별도로 처리되는(point-wise) 완전 연결(full connected) 레이어를 
활용해 인코더와 디코더를 구성한다. 

이 구조는 figure1의 왼쪽과 오른쪽 그림에서 각각 볼 수 있다. 
왼쪽 그림은 인코더 구조, 오른쪽 그림은 디코더 구조를 보여준다. 
인코더와 디코더는 각각 self-attention 메커니즘을 통해 입력 시퀀스 간의 관계를 계산하고, 
이어지는 full connected layer를 통해 최종 출력을 생성한다. 

### 3.1. Encoder and Decoder Stacks

#### Encoder

인코더는 $N=6$개의 동일한 레이어로 구성된 스택 구조이다. 
그리고 각 레이어는 두개의 서브 레이어를 포함한다. 
첫 번째 서브 레이어는 Multi-head self attention 메커니즘으로, 
인풋 시퀀스 내의 위치 간 의존성을 계산한다. 
두 번째 서브 레이어는 각각의 단어가 별도로 처리되는(position-wise) 
완전 연결(full connected) 피드포워드 네트워크로, 
인풋 데이터를 개별적으로 처리하며 비선형 변환을 수행한다. 
이렇게 두개의 서브레이어 주변에는 잔차 연결(residual connection) 후에 
레이어 normalizaiton을 사용한다.  
즉, 각 서브 레이어의 아웃풋은 다음과 같다. 
인풋 $x$와 인풋 $x$가 서브레이어를 통과한 아웃풋인 $sublayer(x)$를 더한 다음 
normalizaiton을 수행한다. 이를 수식으로 나타내면 다음과 같다. 

$LayerNorm(x + sublayer(x))$  

이러한 잔차연결을 용이하게 하기 위해서, 
모델 내부의 임베딩 레이어를 포함한 모든 서브 레이어에 
아웃풋 차원 $d_{model}=512$로 설정한다. 

#### Decoder 

디코더는 $N=6$개의 동일한 레이어로 구성된 스택 구조를 가진다. 
각각의 레이어에는 두개의 서브 레이어가 존재하는것 까지는 인코더 레이어와 유사하지만 
디코더에는 세번째 서브 레이어가 추가되는데, 
세번째 서브레이어는 인코더 스택의 아웃풋에 대해 multi-head attention을 수행한다. 
인코더와 유사하게, 서브 레이어 주변에 잔차 연결을 하고 normalization을 수행한다. 
반면, 디코더 내부에 있는 self-attention 서브 레이어를 수정하여 
특정 위치가 현재 이후에 나오는 위치를 참조하지 못하도록 한다. 
즉, 미래 정보를 참조하지 못하도록 막는다는 뜻이다. 
이러한 마스킹은 출력 임베딩이 오프셋만큼 이동된다는 사실과 결합되어 
$i$번째 위치의 예측이 $i$ 이전 위치에서 알려진 아웃풋에만 의존할수있도록 보장한다. 


<br/>

<a href="http://www.yes24.com/Product/Goods/106175772" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00003_crawling.png" width="800" align="middle">

<br/>


### 3.2 Attention

어텐션 함수는 쿼리와 키-값 쌍의 집합을 아웃풋으로 매핑하는 방식으로 설명할 수 있다. 
이때 쿼리(query), 키(key), 값(value), 아웃풋(output) 모두 벡터로 표현된다. 
아웃풋은 값(value)의 가중합으로 계산되며, 
각 값에 할당된 가중치는 해당 쿼리와 대응되는 키(key) 사이의 호환성 함수에 의해 계산된다. 
예를들어 "I love apples"라는 문장을 번역하는 모델을 처리중이라고 했을때, 
디코더가 "사과"라는 단어를 생성하려고 하는 상황이라고 가정하자. 
이때 쿼리(query)는 디코더의 현재상태이며, 
현재상태는 사과와 관련된 정보를 찾아야하는 상태를 의미이다. 
쿼리를 예로 들면 (0.25, 0.35, 0.45)와 같은 벡터 형태를 띈다.  
키(key)와 값(value)는 인코더가 입력 문장의 각 단어를 벡터로 변환한 단서다. 

* "I" -> key: (0.1, 0.2, 0.3), value: (0.5, 0.6, 0.7)  
* "love" -> key: (0.2, 0.3, 0.4), value: (0.6, 0.7, 0.8)
* "apples" -> key: (0.3, 0.4, 0.5), value: (0.7, 0.8, 0.9)  

아웃풋은 쿼리와 키 간의 유사도를 계산해 가장 관련성 높은 값들을 가중합한 값이다. 


(figure2)

#### 3.2.1 Scaled Dot-Product Attention  

우리는 이 특정한 어텐션 방식을 "Scaled Dot-Product Attention"이라고 부르겠다. 
(figure2 참고) 
인풋 데이터는 $d_k$ 차원의 쿼리와 키(key)와 $d_v$ 차원의 값(value)으로 구성되어 있다. 
우리는 쿼리와 키 간의 내적을 계산한 뒤, 각 결과를 $\sqrt{d_k}$로 나누고 
소프트맥스 함수를 적용해 값(value)에 대한 가중치를 얻는다. 

실제로는 동시에 여러 쿼리들에 어텐션 함수를 적용하고, 행렬 Q에 함께 모아서 처리한다. 
키와 값들 역시 행렬 k와 v에 함께 모아처리한다. 
우리는 아웃풋 해열을 다음과 같이 계산할 수 있다. 

$Attention(Q, K, V) = softmax(\frac{QK^{T}}{\sqrt{d_k}})V$ 

가장 흔하게 사용되는 어텐션 함수는 additive(가산) attention과 dot-product(내적) 어텐션이다. 
내적 어텐션은 $1/\sqrt{d_k}$ 스케일링 요소만 추가된 것을 제외하면 
우리 알고리즘(Scaled Dot-Product Attention)과 동일하다. 
가산 어텐션은 호환성 함수를 계산할 때, 
단일 은닉층을 가진 피드포워드 네트워크를 사용한다. 
이러한 두 방식은 이론적인 복잡도가 비슷하지만, 
내적 어텐션은 매우 최적화된 행렬 곱셈 코드로 구현할 수 있으므로 
실제로 훨씬 빠르고 메모리 효율적이다. 
즉, 가산 어텐션은 은닉층을 활용해 호환성을 계산하고, 내적 어텐션은 단순히 내적을 사용하는데, 
내적 어텐션이 더 빠르고 효율적이라고 할 수 있다. 

$d_k$가 작을 때는 두 방법의 성능이 비슷하지만 
$d_k$가 클 경우에는 스케일링이 없는 내적 어텐션은 가산 어텐션보다 성능이 떨어진다. 
$d_k$ 값이 클 경우, 내적 결과값이 매우 커지면서 소프트맥스 함수의 
그래디언트가 매우 작은 영역(region)으로 밀려서 그런것이 아닐까 추측한다. 
따라서 이러한 일을 예방하고 안정성을 확보하기 위해 
내적 값에 $1/\sqrt{d_k}$을 곱하는 스케일링을 적용한다. 


#### 3.2.2 Multi-Head Attention 

우리는 $d_{model}$ 차원의 키, 값, 쿼리를 사용해 단일 어텐션 함수를 수행하는 대신, 
쿼리 키, 값을 각각 서로 다르게 학습된 프로젝션(linear projections)을 사용해 
$d_k$, $d_k$, $d_v$ 차원으로 프로젝션(linear projections)하고 
이를 h번 반복하는 것이 유리하다는 것을 발견했다. 
이렇게 선형 변환된 쿼리, 키, 값에 대해 각각 병렬로 어텐션 함수를 수행하여 
$d_v$차원의 아웃풋을 얻는다. 
이 아웃풋들을 이어 붙여 서로 연결(concatenate)하고 다시 한번 선형 변환 한 뒤,  
figure2에 묘사된 것과 같은 최종 값을 구할 수 있다. 

멀티-헤드 어텐션은 모델이 다양한 표현 공간(Representation Subspace)에서 
서로 다른 위치의 정보를 동시에 주목할 수 있게 한다. 
단일 어텐션 헤드에서는 평균화로 인해 여러 정보가 하나로 합쳐지면서
구체적인 특징들이 희석될 수 있다. 
그러나 멀티-헤드 방식은 각 헤드가 독립적으로 특정 특징을 학습할 수 있게 함으로써 
모델의 표현력을 강화시킨다. 

$MultiHead(Q, K, V) = Concat(head_1, ..., head_h)W^{O}$  
$where head_i = Attentino(QW_{i}^{Q}, KW_{i}^{K}, VW_{i}^{V})$  

이때 프로젝션(projection, 선형 변환)에 사용되는 행렬들은 
다음과 같은 매게변수 행렬로 정의 된다. 

$W_{i}^{Q}\in \mathbb{R}^{d_{model} \times d_k}$  
$W_{i}^{K}\in \mathbb{R}^{d_{model} \times d_k}$  
$W_{i}^{V}\in \mathbb{R}^{d_{model} \times d_v}$  
$W_{i}^{O}\in \mathbb{R}^{hd_{v} \times d_{model}}$  


<br/>

<a href="http://www.yes24.com/Product/Goods/105772247" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00002_la.png" width="800" align="middle">

<br/>



#### 3.2.3 Applications of Attention in our Model  

트랜스포머는 다음과 같은 3가지 방법으로 멀티-헤드 어텐션을 사용한다. 

* '인코더-디코더 어텐션' 레이어에서는 쿼리가 이전 디코더 레이어에서 생성되고,
메모리 키와 값은 인코더 출력에서 가져온다.
이러한 방법은 디코더의 모든 위치가 입력 시퀀스의 모든 위치에 주목할 수 있도록 한다. 
이러한 방식은 [38, 2, 9]와 같은 시퀀스-투-시퀀스 모델에서 사용되는
일반적인 '인코더-디코더 어텐션' 메커니즘을 사용한다.
즉, 인코더 디코더 어텐션은 디코더가
입력 전체 시퀀스 정보에 접근할 수 있게 해주는 메커니즘이다. 

* 인코더는 셀프 어텐션(self-attention) 레이어을 포함하고 있다.
셀프 어텐션 레이어에서는 키, 값, 쿼리 모두 동일한 출처(place)로부터 생성되며,
여기서는 인코더의 이전 계층 아웃풋에서 나옵니다.
여기서 동일한 출처라는 말에 대해 알아보자. 
일반적인 어텐션 메커니즘에서는 쿼리, 키, 값이 서로 다른 데이터 소스에서 올수 있다.
예를 들어 인코더-디코더 어텐션에서 쿼리는 디코더 아웃풋에서 생성되며
키와 값은 인코더 아웃풋에서 생성된다.
반면 셀프 어텐션에서는 쿼리, 키, 값이
모두 동일한 소스(ex. 이전 레이어 아웃풋, 인풋 데이터)에서 생성된다.

* 유사하게, 디코더의 셀프 어텐션 레이어는 디코더의 각 위치가 해당 위치까지의
모든 위치에 주목(attend)할 수 있도록 한다.
auto-regressive 특성을 유지하기 위해 디코더에서
왼쪽 방향으로 정보가 흐르는 것(leftward information flow)을
방지해야한다.
이때, 왼쪽 방향으로 흐르는 것은
현재 위치 이후의 미래 단어가 과거로 정보를 제공하는 것을 의미한다. 
이를 구현하기 위해 스케일 조정된 내적 어텐션(scaled dot-product attention)내에서
소프트맥스 인풋 중 불법적인 연결에 해당하는 모든 값을 마스킹 처리해 $-\infty$로 설정한다.
Figure2를 참고하자.

### 3.3 Position-wise Feed Forward Networks 

어텐션 서브 레이어 외에도 추가적으로, 인코더와 디코더의 각 레이어는 
완전 연결(fully connected) 네트워크를 포함하며, 
이는 각 위치에 개별적이고 동일하게 적용된다. 
이 네트워크는 두 개의 선형 변환과 그 사이의 ReLU 활성화 함수로 구성된다. 

$FFN(x)=max(0, xW_1 + b_1)W_2 + b_2$

선형 변환(linear transformation)은 다른 위치에도 전반적으로 걸쳐서 동일하지만, 
레이어마다 서로 다른 파라미터를 사용한다. 
이를 다르게 표현하면, 커널 크기가 1인 두개의 합성곱(convolution)으로 설명할 수 있다. 
입력과 출력의 차원은 $d_{model}$, 내부 레이어의 차원은 $d_{ff}=2048$이다. 

### 3.4 Embeddings and Softmax 

다른 시퀀스 변환 모델과 유사하게, 
우리는 학습된 임베딩을 사용하여 인풋 토큰과 아웃풋 토큰을 $d_{model}$ 차원의 
벡터로 변환한다. 
우리는 또한 디코더의 아웃풋을 다음 토큰의 예측 확률로 변환하기 위해, 
학습된 선형 변환(linear transformation)과 소프트맥스 함수를 사용한다. 
여기서 학습된 선형 변환이란 우리가 흔히 알고 있는 $wx + b$를 의미한다. 
우리 모델에서는, 두개의 임베딩 레이어(인풋, 아웃풋)와 
소프트맥스 이전 선형 변환 간 동일한 가중치 행렬을 공유한다. 
이는 (30)에서 사용된 방법과 유사하다. 
임베딩 레이어에서, 우리는 가중치 행렬에 $\sqrt{d_{model}}$을 곱한다. 

Table 1: 다양한 레이어 유형에 대한 최대 경로 길이(Maximum path length), 
레이어별 연산 복잡도(Per-layer complexity), 
최소 순차 연산 수 (Minimum number of sequential operations)

Layer Type | Complexity per Layer | Sequential Operations | Maximum Path Length
-----------|----------------------|-----------------------|--------------------
Self-Attention | $O(n^2 \cdot d)$ | $O(1)$ | $O(1)$
Recurrent | $O(n \cdot d^2)$ | $O(n)$ | $O(n)$ 
Convolutional | $O(k \cdot n \cdot d^2)$ | $O(1)$ | $O(log_k (n))$
Self-Attention(restricted) | $O(r \cdot n \cdot d)$ | $O(1)$ | $O(n/r)$


### 3.5 Positional Encoding 

우리 모델은 순환(recurrence)이나 합성곱(convolution)을 사용하지 않으므로, 
시퀀스의 순서 정보를 활용하려면 토큰의 상대적 또는 절대적 위치 정보를 추가해야 한다. 
이를 위해 포지셔널 인코딩(positional encoding)을 인풋 인베딩에 추가한다. 
이는 인코더와 디코더 스택의 가장 바닥(bottom)에서 적용된다. 
포지셔널 인코딩은 임베딩과 동일한 차원($d_{model})$을 가지며, 
두 값을 합산 할 수 있도록 설계된다. 
포지셔널 인코딩 방식에는 여러가지 선택지가 있는데, 
학습 기반 방식과 고정(fixed) 방식이 있다. 

포지셔널 인코딩은 시퀀스 내 각 토큰의 위치 정보를 벡터로 표현하여, 
모델이 순서를 이해할 수 있게 한다. 
이때 위에서 말한 고정 방식이란 주로 수학에서 말하는 사인이나 코사인 함수를 말한다. 

* "I love you"  
* "I" -> (0.5, 0.6, 0.7, 0.8)  
* "love" -> (0.6, 0.7, 0.8, 0.9)  
* "you" -> (0.7, 0.8, 0.9, 1.0)  

예를 들어, 위와 같이 시퀀스 길이가 3이라고 하고, 임베딩 차원 $d_{model}=4$라고 하면 
포지셔널 인코딩은 다음과 같다. 

* 짝수 인덱스($2i$) : $sin(\frac{pos}{10000^{2i / d_{model}}})$
* 홀수 인덱스($2i+1$) : $cos(\frac{pos}{10000^{2i / d_{model}}})$

위 식은 짝수 차원은 사인 함수로 계산하고 홀수 차원은 코사인 함수로 계산하라는 뜻이다. 
위와 같은 함수를 선택한 이유는, 해당 함수들을 사용했을 때 모델이 
상대적인 위치를 쉽게 학습할 수 있을 것이라고 가정했기 때문이다. 
왜냐하면 
고정된 오프셋 k에 대해 $PE_{pos+k}$는 $PE_{pos}$의 선형함수로 표현될수 있기 때문이다. 
이 말은 특정 위치에서 고정된 간격만큼 떨어진 다른 위치의 인코딩 값은 
원래 위치의 인코딩 값과 선형적으로 연관되도록 설계된다는 뜻이다. 
예를 들어 위 예제에서 I는 love 바로 앞에 있다라는 관계를 모델이 쉽게 이해할 수 있다. 

예를 들어, 위 예제에서 "love"에 해당하는 단어는 포지션 1에 해당한다. 
참고로 I는 포지션 0, you는 포지션 2에 해당함. 
이를 POS=1이라고 하고 POS=1에 대해 포지셔널 인코딩을 진행하면 다음과 같다.

* $i=0$, PE(1, 0) = $sin(\frac{1}{10000^{0/4}}) = sin(1) = 0.0001$
* $i=1$, PE(1, 1) = $cos(\frac{1}{10000^{0/4}}) = cos(1) = 0.0001$
* $i=2$, PE(1, 2) = $sin(\frac{1}{10000^{2/4}}) = sin(1/100) = 0.9999$
* $i=3$, PE(1, 3) = $cos(\frac{1}{10000^{0/4}}) = cos(1/1000) = 0.9999$

위와 같이 정리하면 "love"에 대한 포지셔널 인코딩은 다음과 같다. 

$PE(1) = [0.0001, 0.9999, 0.0001, 0.9999]$

그리고나서 기존 인풋 인베딩에 포지셔널 인코딩을 추가하면 다음과 같다. 

* "I" -> (0.5, 0.6, 0.7, 0.8) -> (0.5, 1.6, 0.7, 0.8)  
* "love" -> (0.6, 0.7, 0.8, 0.9) ->  (0.6001, 1.6999, 0.8001, 1.8999)  
* "you" -> (0.7, 0.8, 0.9, 1.0)  ->  (0.7002, 1.7998, 0.9002, 1.9998)  

위와 같은 고정 방식 말고도, 우리는 학습된 포지셔널 임베딩을 사용하는 실험도 진행했다. 
사인, 코사인 기반 인코딩과 학습된 임베딩과 같은 두 방식이 
거의 동일한 결과를 산출한다는 것을 발견했다. (표 3의 E행 참고) 
우리는 사인파 기반 버전을 선택했는데, 이는 이 방식이 모델이 학습 중에 만나는 
시퀀스 길이보다 더 긴 시퀀스에 대해 외삽(extrapolate)을 가능하게 하기 때문이다. 
이때, 외삽은 학습 데이터 범위 밖에 있는 값을 추정하거나 예측하는 것을 의미한다. 
예를 들어 학습 데이터에서 길이 10까지의 문장만 학습했다면, 
길이 15의 문장을 처리하려는 시도가 외삽이다. 
예를 들어, 내가 학습할 때 사용한 데이터는 

* "I love deep learning because it is fun."

와 같이 단어 9개로 구성된 문장이었다면 실제 테스트 상황에서는 다음과 같이 
17개 단어로 구성된 문장이 들어올 수 있다. 

* "The Transformer model is very powerful and works well for long sequences in natural language processing."

위와 같은 경우, 학습된 포지셔널 임베딩을 사용할 경우, 
학습 데이터에 등장했던 문장 길이에만 최적화되므로 학습 중에는 본적없는 길이 17의 문장에 
대해서는 제대로 동작하지 않을수도 있다. 
반면 사인파 기반 포지셔널 인코딩을 사용하는 경우, 
문장의 길이가 길어지더라도 그대로 적용 가능하다.  

<br/>

<a href="http://www.yes24.com/Product/Goods/117709828" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00004_probability.png" width="800" align="middle">

<br/>

## 4. Why Self-Attention

이번 섹션에서는 시퀀스 $(x_1, ... ,x_n)$을 동일한 길이의 
다른 시퀀스 $(z_1, ... ,z_n)$로 매핑하는 데 일반적으로 사용되는 
순환 레이어와 합성곱 레이어를 셀프 어텐션과 다양한 측면으로 비교한다. 
이때 $x_i, z_i \in R^d$를 만족하는데 $x_i, z_i$는 스칼라가 아니라 벡터이며, 
이들은 시퀀스 변환하는 인코더나 디코더에 있는 은닉 상태(hidden state) 벡터을 의미한다. 
셀프 어텐션을 사용하기 위해서는 우리는 세가지 필요조건을 고여한다. 

첫번째 필요조건은 레이어 당 총 계산 복잡도이다. 
예를 들어 연산에 필요한 곱셈과 덧셈의 수 등을 합산하여 계산한다. 
두번째 조건은 병렬화 할 수 있는 계산의 양인데, 이는 필요한 최소 순차 연산의 수로 측정된다. 
이때, 병렬화 가능한 정도를 평가하기 위해 순차적으로만 수행해야하는 최소 작업수를 
기준으로 삼는다는 점이다. 순차 작업이 적을 수록 병렬 처리가 더 효과적일 수 있다. 

<br/>

<a href="http://www.yes24.com/Product/Goods/126115324" target="_blank"><img src="/assets/images/advertisement/ad-book/ad00005_dockernk8s.png" width="800" align="middle">

<br/>
