---
title: Tensorflow - 텐서플로를 사용해 MNIST를 학습
type: blog-archive
status: active
created: '2026-06-13'
updated: '2026-08-16'
published: '2026-06-13T20:56:20+09:00'
source: https://agapeuni.tistory.com/838
source_blog: agapeuni.tistory.com
post_id: 838
category: ✨ 딥러닝·머신러닝
tags:
- MNIST데이터정규화
- MNIST손글씨분류
- tensorflow예제
- 딥러닝모델구현
- 딥러닝모델학습방법
- 손글씨숫자인식예제
- 케라스MNIST실습
- 텐서플로MNIST
- 텐서플로모델평가
- 파이썬딥러닝코드
body_hash: eefd7fe00a7cc5a9606d13935a88a3011b4b5335bca457b66813ea65bff37654
visibility: private
rag: exclude
---

# Tensorflow - 텐서플로를 사용해 MNIST를 학습

- 원문: https://agapeuni.tistory.com/838
- 게시일: 2026-06-13T20:56:20+09:00
- 분류: ✨ 딥러닝·머신러닝

## 본문

![[03 Attachments/티스토리 Vento AI Lab/838/838-001-파이썬-001_(5).png]]

## 1. 딥러닝 단계

딥러닝(Deep Learning)은 다양한 분야에서 활용되는 머신 러닝 알고리즘이다. 일반적으로 딥러닝은 다음과 같은 단계를 따른다. 이번에는 딥러닝의 단계를 알아보고 텐서플로를 사용해 단계를 따라 딥러닝 모델을 구현해 보자. 텐서플로는 구글에서 제공하는 머신러닝 플랫폼이다. 데이터로 MNIST 손글씨 이미지를 사용한다.

![[03 Attachments/티스토리 Vento AI Lab/838/838-002-ChatGPT Image 2026년 6월 13일 오후 08_54_01.png]]

**1) 데이터 준비**

모델을 학습시키기 위해서는 먼저 데이터를 수집해야 한다.

학습 데이터, 검증 데이터, 테스트 데이터로 구분하여 수집하는 것이 일반적이다.

**2) 데이터 전처리**

수집한 데이터는 학습을 위해 전처리 과정을 거쳐야 한다.

이 과정에서는 데이터를 정제하고, 스케일링하고, 변환하고, 잡음을 제거하고, 필요한 경우 데이터를 라벨링하는 등의 작업을 수행한다.

**3) 모델 설계**

모델을 설계하는 단계로, 이 단계에서는 입력 데이터와 출력 데이터, 그리고 모델의 아키텍처와 하이퍼파라미터 등을 결정한다.

**4) 모델 학습**

모델을 학습시키는 단계로, 입력 데이터와 출력 데이터를 이용하여 모델을 학습시킨다.

이 과정에서는 손실 함수(loss function)를 정의하고, 역전파 알고리즘을 사용하여 모델의 가중치와 편향을 업데이트한다.

**5) 모델 평가**

학습된 모델을 검증 데이터 또는 테스트 데이터를 사용하여 평가한다.

이 단계에서는 모델의 성능을 측정하고, 문제가 있으면 다시 학습 단계로 돌아가서 모델을 개선한다.

**6) 모델 배포**

모델이 충분히 검증되면, 실제 운영 환경에서 사용할 수 있도록 배포한다.

이 단계에서는 모델을 제품에 통합하고, 사용자의 입력을 받아 모델의 출력을 반환하는 인터페이스를 구성한다.

## 2. 패키지 설치

설치한 파이썬 패키지 버전은 다음과 같다.

> pip install tensorflow

> pip install numpy

> pip install matplotlib

## 3. 테스트 이미지 표시

MNIST 데이터셋을 로딩한다. 손으로 숫자를 쓴 이미지와 이미지에 대한 라벨로 되어있다.

matplotlib 라이브러리를 사용하여 20개의 MNIST 훈련 이미지와 라벨을 표시한다.

```
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf

# MNIST 데이터셋 로드
mnist = tf.keras.datasets.mnist
(train_images, train_labels), (test_images, test_labels) = mnist.load_data()

# 데이터셋 확인
print('train_images.shape =', train_images.shape)
print('train_labels.shape =', train_labels.shape)
print('test_images.shape =', test_images.shape)
print('test_labels.shape =', test_labels.shape)

# MNIST 데이터셋 이미지를 표시
fig, axes = plt.subplots(4, 5)
fig.set_size_inches(8, 5)

for i in range(20):
    ax = axes[i//5, i % 5]
    ax.imshow(train_images[i])
    ax.axis('off')
    ax.set_title(str(train_labels[i]))

plt.tight_layout()
plt.show()
```

**실행 결과**

크기가 28x28인 이미지가 6만개 있다.

```
train_images.shape = (60000, 28, 28)
train_labels.shape = (60000,)
test_images.shape = (10000, 28, 28)
test_labels.shape = (10000,)
```

![[03 Attachments/티스토리 Vento AI Lab/838/838-003-image.png]]

## 4. 모델 생성부터 예측까지

훈련 데이터와 테스트 데이터를 최대값 255로 나누어 데이터 정규화를 한다. 정규화를 마친 데이터의 shape는 (60000, 28, 28)이다. 훈련 데이터가 준비되면 모델을 생성한다. 그리고 생성한 모델을 컴파일한다. 모델을 생성할 때 어떻게 레이어를 구성해야 하는지 경험이 필요하다. 첫번째 레이어는 Flatten 으로 하였고 input_shapes는 (28, 28)로 지정하고 마지막 레이어는 Dense에 10개의 출력으로 지정하고 활성화 함수로 softmax를 선택했다.

```
# 데이터 정규화
train_images = train_images / 255
test_images = test_images / 255

# 모델 생성
model = tf.keras.Sequential([
    tf.keras.layers.Flatten(input_shape=(28, 28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dense(32, activation='relu'),
    tf.keras.layers.Dense(10, activation='softmax'),
])

# 모델 컴파일
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# 모델 훈련
model.fit(train_images, train_labels, validation_data=(
    test_images, test_labels), epochs=10,)

# 모델 평가
test_loss, test_acc = model.evaluate(test_images,  test_labels)
print("test_loss =", test_loss)
print("test_acc =", test_acc)

# 모델 예측
preds = model.predict(test_images)
print(np.argmax(preds[:20], axis=1))
```

**실행 결과**

Epoch 10으로 모델을 학습하고 나니 정확도가 99.38%가 나왔다.

테스트 데이터로 평가해 보니 정확도가 97.93%나 되었다.

```
Epoch 1/10
1875/1875 [==============================] - 8s 4ms/step - loss: 0.2627 - accuracy: 0.9241 - val_loss: 0.1248 - val_accuracy: 0.9620
Epoch 2/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.1104 - accuracy: 0.9668 - val_loss: 0.1210 - val_accuracy: 0.9638
Epoch 3/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0784 - accuracy: 0.9757 - val_loss: 0.0793 - val_accuracy: 0.9766
Epoch 4/10
1875/1875 [==============================] - 8s 4ms/step - loss: 0.0593 - accuracy: 0.9815 - val_loss: 0.0735 - val_accuracy: 0.9771
Epoch 5/10
1875/1875 [==============================] - 8s 4ms/step - loss: 0.0459 - accuracy: 0.9856 - val_loss: 0.0799 - val_accuracy: 0.9761
Epoch 6/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0371 - accuracy: 0.9883 - val_loss: 0.0718 - val_accuracy: 0.9786
Epoch 7/10
1875/1875 [==============================] - 8s 4ms/step - loss: 0.0301 - accuracy: 0.9904 - val_loss: 0.0762 - val_accuracy: 0.9780
Epoch 8/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0253 - accuracy: 0.9918 - val_loss: 0.0819 - val_accuracy: 0.9782
Epoch 9/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0213 - accuracy: 0.9927 - val_loss: 0.0924 - val_accuracy: 0.9760
Epoch 10/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0181 - accuracy: 0.9938 - val_loss: 0.0874 - val_accuracy: 0.9793
313/313 [==============================] - 1s 2ms/step - loss: 0.0874 - accuracy: 0.9793

test_loss = 0.08743911981582642
test_acc = 0.9793000221252441

313/313 [==============================] - 1s 2ms/step
[7 2 1 0 4 1 4 9 5 9 0 6 9 0 1 5 9 7 3 4]
```

## 5. 테스트 이미지와 예측한 값 표시

matplotlit으로 테스트 이미지와 예측한 값을 같이 표시해 보자.

```
def get_one_result(idx):
    t_imgs, t_lable, t_pred, confidence = test_images[idx], test_labels[idx], np.argmax(
        preds[idx]), 100*np.max(preds[idx])
    return t_img, t_lable, t_pred, confidence

# 데이터 시각화
fig, axes = plt.subplots(4, 5)
fig.set_size_inches(12, 10)

for i in range(20):
    ax = axes[i//5, i % 5]
    t_img, t_label, t_pred, confidence = get_one_result(i)
    ax.imshow(t_img)
    ax.set_xticks([])
    ax.set_yticks([])
    ax.set_title(f'True: {t_label}')
    ax.set_xlabel(f'Prediction: {t_pred}\nConfidence: ({confidence:.2f} %)')

plt.tight_layout()
plt.show()
```

**실행 화면**

예측한 값과 이미지를 표시해 보았는데 학습한 모델이 100% 모두 맞추었다.

![[03 Attachments/티스토리 Vento AI Lab/838/838-004-image.png]]

## 6. 전체코드

```
import numpy as np
import matplotlib.pyplot as plt
import tensorflow as tf

# MNIST 데이터셋 로드
mnist = tf.keras.datasets.mnist
(train_images, train_labels), (test_images, test_labels) = mnist.load_data()

# 데이터셋 확인
print('train_images.shape =', train_images.shape)
print('train_labels.shape =', train_labels.shape)
print('test_images.shape =', test_images.shape)
print('test_labels.shape =', test_labels.shape)

# MNIST 데이터셋 이미지를 표시
fig, axes = plt.subplots(4, 5)
fig.set_size_inches(8, 5)

for i in range(20):
    ax = axes[i//5, i % 5]
    ax.imshow(train_images[i])
    ax.axis('off')
    ax.set_title(str(train_labels[i]))

plt.tight_layout()
plt.show()

# 데이터 정규화
train_images = train_images / 255
test_images = test_images / 255

# 모델 생성
model = tf.keras.Sequential([
    tf.keras.layers.Flatten(input_shape=(28, 28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dense(32, activation='relu'),
    tf.keras.layers.Dense(10, activation='softmax'),
])

# 모델 컴파일
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# 모델 훈련
model.fit(train_images, train_labels, validation_data=(
    test_images, test_labels), epochs=10,)

# 모델 평가
test_loss, test_acc = model.evaluate(test_images,  test_labels)
print("test_loss =", test_loss)
print("test_acc =", test_acc)

# 모델 예측
preds = model.predict(test_images)
print(np.argmax(preds[:20], axis=1))

def get_one_result(idx):
    t_imgs, t_lable, t_pred, confidence = test_images[idx], test_labels[idx], np.argmax(
        preds[idx]), 100*np.max(preds[idx])
    return t_img, t_lable, t_pred, confidence

# 데이터 시각화
fig, axes = plt.subplots(4, 5)
fig.set_size_inches(12, 10)

for i in range(20):
    ax = axes[i//5, i % 5]
    t_img, t_label, t_pred, confidence = get_one_result(i)
    ax.imshow(t_img)
    ax.set_xticks([])
    ax.set_yticks([])
    ax.set_title(f'True: {t_label}')
    ax.set_xlabel(f'Prediction: {t_pred}\nConfidence: ({confidence:.2f} %)')

plt.tight_layout()
plt.show()
```

![[03 Attachments/티스토리 Vento AI Lab/838/838-005-주한길.png]]
