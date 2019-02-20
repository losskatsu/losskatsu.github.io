---
title: "ROC Curve(ROC 커브)란? ROC 커브 해석" 
categories:
  - MachineLearning
tags:
  - Statistics
  - MachineLearning
  - Evaluation
use_math: true
toc: true
toc_label: "My Table of Contents"
toc_icon: "cog"
---

# 1. ROC 커브란 무엇일까요? 

여러분이 머신러닝 모델을 만들었다고 합니다. 
모델을 만들었으면 이 모델이 성능이 좋은지 않좋은지 평가를 해야 하겠죠?
ROC 커브는 머신러닝 모델을 평가할 때 쓰입니다. 
<br />

# 2. 민감도와 특이도

ROC 커브를 이야기 하기전에 민감도(Sensitivity)와 특이도(Specificity)의 개념을 아셔야 합니다. 
흔히 민감도와 특이도를 설명하기 위해 의사의 진단을 예를 듭니다.
의사는 환자를 진단해 병에 걸렸느냐 안 걸렸느냐를 판단합니다. 
이때 발생할 수 있는 경우는 

모수 | 병에 걸림 | 정상인
-----|-----------|----- 
검사결과 양성 | 병에 걸린 사람을 양성이라고 판단했으니 정답(1) | 정상인에게 병에 걸렸다는 양성 판정을 내렸으니 오답(2)
검사결과 음성 | 병에 걸린 사람을 정상인이라 판단했으니 오답(3) | 정상인에게 병에 걸리지 않았다는 음성 판정을 내렸으니 정답(4)

위의 표를 좀 더 간략히 표현하면

![figure0](/assets/images/roc/roc00.JPG)


* **민감도(Sensitivity, True positive rate(TPR), Recall)**: 실제 병에 걸린 사람이 양성 판정을 받는 비율입니다. 
* **특이도(Specificity, True negative rate(TNR) )**: 정상인이 음성 판정을 받는 비율입니다. 
* **False positive rate(FPR)** = 1-specificity


$$ \texttt{민감도(Sensitivity)} = \frac{(1)}{(1)+(3)} $$ 

$$ \texttt{특이도(Specificity)} = \frac{(2)}{(2)+(4)} $$


# 3. ROC 커브

결국 모형이 좋다는 말의 뜻을 생각해보면,
모든 환자에게 양성 판정을 내리고, 모든 정상인에게 음성 판정을 내리면 완벽하다. 
만약 모든 진단에 대해 양성 판정을 내리면 어떻게 될까?
이 경우 병에 걸린 모든 환자를 찾을 수 있다. 왜냐면 모든 사람이 양성 판정을 받기 때문이다. 
하지만 정상인도 환자로 판정 받는 다는 단점이 있다. 
그럼 모든 진단에 대해 음성 판정을 내리면 어떻게 될까?
이 경우에는 모든 정상인에 대해 올바른 판정이 내려진다. 
하지만 병에 걸린 환자 또한 정상인이라고 판정 받으므로 병을 치료할 수 없다.

![figure1](/assets/images/roc/roc01.png){: width="500" height="500"}

ROC 커브는 이러한 다양한 부분을 한눈에 볼 수 있는 판정법이다. 
Figure1에서 보면, 병에 걸린 사람을 양성 판정하고, 정상인을 정상인이라 판정하는 가장 이상적인 판정, 
즉, TPR = 1 이고, FPR = 0 인 경우가 가장 이상적이다.(Perfect Classification)

![figure2](/assets/images/roc/roc02.jpg){: width="400" height="400"}

ROC 커브에서 모델의 평가가 좋다는 것은 커브의 밑면적 즉 AUC의 넓이가 넓을 수록 그 모델의 성능이 좋다는 것이다.

![figure3](/assets/images/roc/roc03.png){: width="500" height="500"}
