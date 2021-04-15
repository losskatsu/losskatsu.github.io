---
title: "[python] 파이썬 함수, 모듈, 패키지의 차이점" 
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

# 파이썬 함수, 모듈, 패키지의 차이점 

**참고링크**

* [윈도우에 아나콘다를 사용해 파이썬 가상환경 설치하기](https://losskatsu.github.io/programming/py-conda/)
* [맥북에 파이썬 가상환경(pyenv) 설치하기](https://losskatsu.github.io/it-infra/pyenv-osx/)
* [우분투에 파이썬 가상환경(pyenv) 설치하기](https://losskatsu.github.io/programming/pyenv/)
* [CentOS에 파이썬 가상환경(pyenv) 설치하기](https://losskatsu.github.io/it-infra/pyenv-centos6/)
* [함수, 모듈, 패키지의 차이점](https://losskatsu.github.io/programming/function-module-package/)
* [클래스, 객체 개념](https://losskatsu.github.io/programming/class-object/)

## 1. 함수

함수는 미리 정한 동작을 수행하는 코드를 묶은 것을 의미합니다. 
함수를 사용하면 같은 코드를 여러 번 작성할 필요가 없다는 장점이 있습니다.


<center><img src="/assets/images/programming/function-module-package/01.JPG" width="500"></center>

위 그림은 입력변수의 덧셈 결과를 출력하는 sum이라는 함수입니다. 

```python
def sum(a,b):
    c = a + b
    return c
```

<center><img src="/assets/images/programming/function-module-package/02.JPG" width="500"></center>

함수는 위 그림과 같이 어렸을 때 수학 시간에 배운 함수의 개념과 동일하다고 생각할 수 있습니다.

```python
>>> sum(2,5)
7
```

위 코드와 같이 sum 함수를 이용해  2와 5의 합을 구하면 7인 것을 알 수 있습니다. 



## 2. 모듈 

모듈(module)은 전역변수, 함수, 클래스 등을 모아놓은 .py 확장자를 가진 파일입니다. 

<center><img src="/assets/images/programming/function-module-package/03.JPG" width="800"></center>

모듈의 개념은 위와 같습니다. 위 그림에서 모듈 module01.py는 변수 2개 클래스 1개, 함수 2개를 모아 놓은 .py 파일입니다. 
그리고 main.py라는 다른 파이썬 파일에서 모듈 module01를 import 명령어를 이용해 불러올 수 있습니다. 

<center><img src="/assets/images/programming/function-module-package/04.JPG" width="800"></center>

모듈을 실습하기 위해 위와 같은 파일을 만든다고 해보겠습니다. 
임의의 실습 폴더를 만들고 module01.py와 main.py를 만듭니다. 

```python
# module01.py
A= 1
B = 2

def sum(c, d):
    e = c + d
    return e
```
위 코드는 module01.py의 코드입니다.

```python
# main.py
import module01

new_a = module01.A
print("new_a = ", new_a)

new_b = module01.B
print("new_b = ", new_b)

sol = module01.sum(new_a, new_b)
print("new_a + new_b = ", sol)

```
위 코드는 main.py파일의 코드입니다.

<center><img src="/assets/images/programming/function-module-package/05.JPG" width="800"></center>

파일을 생성했다면 Anaconda prompt를 실행합니다. 그리고 생성된 프롬프트 창에서 다음과 같이 입력합니다. 

```bash
(base) > cd ‘실습폴더’
(base) > python main.py
new_a = 1
new_b = 2
new_a + new_b = 3
```


## 3. 패키지/라이브러리

<center><img src="/assets/images/programming/function-module-package/07.JPG" width="800"></center>

앞서 모듈이 함수의 집합이라면 패키지(package)는 모듈을 모아놓은 폴더라고 할 수 있습니다. 
패키지는 종종 라이브러리(library)라고도 부릅니다. 엄말하게 말하면 라이브러리는 패키지의 집합으로 패키지 보다 포괄적인 개념이지만, 
혼용해서 사용하기도 합니다. 
예를 들어, 넘파이 라이브러리라고도 부르고, 넘파이 패키지라고도 부릅니다.

<center><img src="/assets/images/programming/function-module-package/08.JPG" width="500"></center>

패키지 실습 폴더 구성은 위 그림과 같습니다. 파일의 코드는 앞선 모듈 코드와 동일합니다. 
모듈 실습과의 차이점은 모듈이 package01이라는 폴더 안에 존재한다는 것입니다. 

```python
# main.py
import package01.module01

new_a = package01.module01.A
print("new_a = ", new_a)

new_b = package01.module01.B
print("new_b = ", new_b)

sol = package01.module01.sum(new_a, new_b)
print("new_a + new_b = ", sol)
```
main.py 파일의 코드 내용은 위와 같습니다. 

```python
(base) > cd ‘실습폴더’
(base) > python main.py
new_a = 1
new_b = 2
new_a + new_b = 3
```
그리고 anaconda prompt에서 위 코드를 실행하면 결과를 확인할 수 있습니다. 
