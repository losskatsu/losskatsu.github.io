---
title: "텐서플로 튜토리얼(1)-기본 이미지 분류" 
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

# 텐서플로 튜토리얼(1)-기본 이미지 분류

본 포스팅은 [텐서플로 튜토리얼](https://www.tensorflow.org/tutorials/keras/classification?hl=ko)과 동일한 내용입니다. 

## import 라이브러리

```python
from __future__ import absolute_import, division, print_function, unicode_literals, unicode_literals

# tensorflow와 tf.keras를 임포트합니다
import tensorflow as tf
from tensorflow import keras

import numpy as np
import matplotlib.pyplot as plt

print(tf.__version__)
```
```python
2.0.0
```

