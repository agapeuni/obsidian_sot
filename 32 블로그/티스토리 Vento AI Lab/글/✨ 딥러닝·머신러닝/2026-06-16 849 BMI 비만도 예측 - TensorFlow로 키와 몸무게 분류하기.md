---
title: BMI 비만도 예측 - TensorFlow로 키와 몸무게 분류하기
type: blog-archive
status: active
created: '2026-06-16'
updated: '2026-08-16'
published: '2026-06-16T10:36:48+09:00'
source: https://agapeuni.tistory.com/849
source_blog: agapeuni.tistory.com
post_id: 849
category: ✨ 딥러닝·머신러닝
tags:
- Dense레이어회귀분석
- Sequential회귀모델
- SGD옵티마이저활용
- TensorFlow회귀분석예제
- 선형회귀예측방법
- 케라스선형회귀모델
- 텐서플로선형회귀
- 파이썬선형회귀구현
- 평균제곱오차손실함수
- 회귀선시각화방법
body_hash: 9ed3dcae7c31dcd4b7cf003ec902e92566e3c8d679c553b195c4c544f3448480
visibility: private
rag: exclude
---

# BMI 비만도 예측 - TensorFlow로 키와 몸무게 분류하기

- 원문: https://agapeuni.tistory.com/849
- 게시일: 2026-06-16T10:36:48+09:00
- 분류: ✨ 딥러닝·머신러닝

## 본문

![[03 Attachments/티스토리 Vento AI Lab/849/849-001-딥러닝-머신러닝-001.png]]

## 1. 데이터 준비

먼저, BMI 데이터를 생성하거나 불러온다. BMI는 키와 몸무게를 바탕으로 계산되며, 비만도를 라벨로 사용한다. 여기서는 임의의 키와 몸무게 데이터를 생성하고, 이를 바탕으로 BMI를 계산하여 라벨(저체중, 정상, 과체중, 비만)을 지정한다. 데이터는 학습용과 테스트용으로 나누고, StandardScaler를 사용해 스케일링한다.

```
import numpy as np
import pandas as pd
import tensorflow as tf
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# BMI 계산 함수
def calculate_bmi(height, weight):
    return weight / (height / 100) ** 2

# 임의의 데이터 생성
np.random.seed(42)
heights = np.random.uniform(150, 190, 1000)  # 150~190 cm 범위의 키
weights = np.random.uniform(50, 100, 1000)   # 50~100 kg 범위의 몸무게
bmi = calculate_bmi(heights, weights)

# 비만도 라벨링
labels = []
for b in bmi:
    if b < 18.5:
        labels.append(0)  # 저체중
    elif 18.5 <= b < 24.9:
        labels.append(1)  # 정상 체중
    elif 25 <= b < 29.9:
        labels.append(2)  # 과체중
    else:
        labels.append(3)  # 비만

# 데이터프레임 생성
data = pd.DataFrame({
    'Height': heights,
    'Weight': weights,
    'BMI': bmi,
    'Label': labels
})

# 입력 데이터와 라벨 분리
X = data[['Height', 'Weight']].values
y = tf.keras.utils.to_categorical(data['Label'], num_classes=4)  # 원-핫 인코딩

# 데이터 분할 (학습용, 테스트용)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 데이터 스케일링
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

![[03 Attachments/티스토리 Vento AI Lab/849/849-002-image.png]]

****

****

## 2. 모델 구성 및 컴파일

입력층은 2개의 입력(키와 몸무게)을 받고, 중간층에서 Relu 활성화 함수로 활성화된 3개의 은닉층을 사용한다. 출력층은 4개의 유닛을 가지고 있으며, 소프트맥스 활성화 함수를 통해 각 클래스(저체중, 정상, 과체중, 비만)에 대한 확률을 출력한다.

- 0 - 저체중

- 1 - 정상 체중

- 2 - 과체중

- 3 - 비만

```
# 모델 구성
model = tf.keras.Sequential([
    tf.keras.layers.Dense(64, activation='relu', input_shape=(2,)),
    tf.keras.layers.Dense(32, activation='relu'),
    tf.keras.layers.Dense(16, activation='relu'),
    tf.keras.layers.Dense(4, activation='softmax')  # 4개의 클래스 (저체중, 정상, 과체중, 비만)
])

# 모델 컴파일
model.compile(optimizer='adam',
              loss='categorical_crossentropy',  # 교차 엔트로피 손실 함수
              metrics=['accuracy'])
```

## 3. 모델 학습

50 에포크 동안 학습시키며, 학습과정에서 손실과 정확도를 기록한다.

```
# 모델 학습
history = model.fit(X_train, y_train, epochs=50, validation_data=(X_test, y_test))
```

```
Epoch 1/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 1s 5ms/step - accuracy: 0.4237 - loss: 1.3278 - val_accuracy: 0.6450 - val_loss: 1.1761
Epoch 2/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 2ms/step - accuracy: 0.7088 - loss: 1.0965 - val_accuracy: 0.7000 - val_loss: 0.9324
Epoch 3/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 2ms/step - accuracy: 0.7397 - loss: 0.8505 - val_accuracy: 0.7550 - val_loss: 0.6867
Epoch 4/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.7641 - loss: 0.6327 - val_accuracy: 0.7850 - val_loss: 0.5314
Epoch 5/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.7783 - loss: 0.5435 - val_accuracy: 0.8850 - val_loss: 0.4276
Epoch 6/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.8512 - loss: 0.4373 - val_accuracy: 0.9000 - val_loss: 0.3640
Epoch 7/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.8769 - loss: 0.3735 - val_accuracy: 0.9200 - val_loss: 0.3101
Epoch 8/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.8992 - loss: 0.3147 - val_accuracy: 0.9250 - val_loss: 0.2675
Epoch 9/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9041 - loss: 0.2927 - val_accuracy: 0.9000 - val_loss: 0.2399
Epoch 10/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9219 - loss: 0.2619 - val_accuracy: 0.9200 - val_loss: 0.2161
Epoch 11/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9195 - loss: 0.2489 - val_accuracy: 0.9500 - val_loss: 0.1954
Epoch 12/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9352 - loss: 0.2218 - val_accuracy: 0.9500 - val_loss: 0.1708
Epoch 13/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9456 - loss: 0.1846 - val_accuracy: 0.9500 - val_loss: 0.1624
...
Epoch 49/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9771 - loss: 0.0638 - val_accuracy: 0.9750 - val_loss: 0.0554
Epoch 50/50
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 1ms/step - accuracy: 0.9750 - loss: 0.0565 - val_accuracy: 0.9800 - val_loss: 0.0563
Output is truncated. View as a scrollable element or open in a text editor. Adjust cell output settings...
```

## 4. 학습 과정 시각화

학습과 검증 데이터에 대한 손실과 정확도의 변화를 시각화하여 학습이 잘 진행되고 있는지 확인한다.

```
import matplotlib.pyplot as plt

# 학습 과정 시각화
plt.figure(figsize=(12, 4))

# 손실 함수 시각화
plt.subplot(1, 2, 1)
plt.plot(history.history['loss'], label='Training Loss')
plt.plot(history.history['val_loss'], label='Validation Loss')
plt.title('Loss')
plt.xlabel('Epochs')
plt.ylabel('Loss')
plt.legend()

# 정확도 시각화
plt.subplot(1, 2, 2)
plt.plot(history.history['accuracy'], label='Training Accuracy')
plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
plt.title('Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()

plt.show()
```

![[03 Attachments/티스토리 Vento AI Lab/849/849-003-8fa1499e-c8d3-48aa-8394-78d12abe8a2a.png]]

****

## 5. 모델 평가

테스트 데이터로 모델의 최종 성능을 평가하여 정확도를 출력한다.

```
# 테스트 데이터로 모델 평가
test_loss, test_accuracy = model.evaluate(X_test, y_test)
print(f"Test Accuracy: {test_accuracy * 100:.2f}%")
```

```
7/7 ━━━━━━━━━━━━━━━━━━━━ 0s 837us/step - accuracy: 0.9800 - loss: 0.0554
Test Accuracy: 98.00%
```

![[03 Attachments/티스토리 Vento AI Lab/849/849-004-주한길.png]]
