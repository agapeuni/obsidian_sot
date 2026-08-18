---
title: TensorFlow - 텐서플로를 사용하여 MNIST 예제를 실행
type: blog-archive
status: active
created: '2026-06-16'
updated: '2026-08-16'
published: '2026-06-16T10:14:36+09:00'
source: https://agapeuni.tistory.com/847
source_blog: agapeuni.tistory.com
post_id: 847
category: ✨ 딥러닝·머신러닝
tags:
- Dropout과적합방지
- FlattenDense레이어
- MNIST데이터셋정규화
- Sequential모델구성
- sparse_categorical_crossentropy
- TensorFlow튜토리얼
- 딥러닝숫자분류모델
- 케라스손글씨숫자인식
- 텐서플로MNIST예제
- 학습정확도시각화
body_hash: 7871674cb995c6c3d4b098f9279b2f2d9d21ef6064bb105e62adcc98083ff2a2
visibility: private
rag: exclude
---

# TensorFlow - 텐서플로를 사용하여 MNIST 예제를 실행

- 원문: https://agapeuni.tistory.com/847
- 게시일: 2026-06-16T10:14:36+09:00
- 분류: ✨ 딥러닝·머신러닝

## 본문

![[03 Attachments/티스토리 Vento AI Lab/847/847-001-딥러닝_머신러닝-001.png]]

텐서플로 사이트에 있는 튜토리얼 예제를 실행해 본다. 이 코드는 텐서플로 라이브러리를 사용하여 손글씨 숫자 이미지를 인식하는 간단한 인공 신경망 모델을 만들고 훈련하는 과정을 수행한다. MNIST 데이터셋을 사용하며, MNIST는 0부터 9까지의 숫자로 작성된 손글씨 이미지로 구성된 데이터셋이다.

TensorFlow와 Keras를 사용하여 MNIST 데이터셋을 로드하고, 그 데이터를 신경망 모델에 입력할 수 있도록 정규화한다. 이 정규화된 데이터를 사용하여 딥러닝 모델을 훈련하고 평가할 수 있다. MNIST는 딥러닝 학습자들이 자주 사용하는 기본적인 데이터셋 중 하나로, 이 데이터셋을 통해 손글씨 숫자 인식 모델을 구축하는 연습을 할 수 있다.

```
# 1. 텐서플로 라이브러리 임포트
import tensorflow as tf

# 2. MNIST 데이터셋 로드
mnist = tf.keras.datasets.mnist

# 3. 학습 데이터와 테스트 데이터 반환
(x_train, y_train), (x_test, y_test) = mnist.load_data()

# 4. 데이터 전처리: 정규화
x_train = x_train / 255.0
x_test = x_test / 255.0
```

TensorFlow 라이브러리를 tf라는 이름으로 가져온다.

TensorFlow는 딥러닝 및 머신러닝 모델을 구축하고 훈련시키는 데 널리 사용되는 라이브러리다.

TensorFlow의 Keras API에 포함된 MNIST 데이터셋을 로드한다. MNIST는 손으로 쓴 숫자(0-9)가 포함된 28x28 픽셀의 흑백 이미지로 구성된 데이터셋이다. 이 데이터셋은 머신러닝 및 딥러닝 모델을 훈련하는 데 자주 사용된다.

학습용 데이터(x_train, y_train)와 테스트용 데이터(x_test, y_test)를 반환한다.

- x_train : 훈련 이미지. 28 x 28 크기의 픽셀로 구성된 숫자 이미지.

- y_train : 훈련 라벨로 각 이미지에 해당하는 숫자 (0-9)

- x_test: 테스트용 이미지

- y_test : 테스트용 라벨.

이미지 데이터를 0에서 1 사이의 값으로 정규화한다.

```
# 5. 모델 생성
model = tf.keras.models.Sequential([
    tf.keras.layers.Flatten(input_shape=(28, 28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dropout(0.2),
    tf.keras.layers.Dense(10, activation='softmax')
])

# 6. 모델 컴파일
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])
```

Keras의 Sequential API를 사용하여 레이어를 순차적으로 쌓은 모델을 만든다. tf.keras.models.Sequential을 사용하여 Sequential 모델을 생성한다. 이 모델은 여러 층을 순차적으로 쌓는 방식으로 신경망을 정의하는 데 사용된다.

**1) Flatten 레이어**

Flatten 층은 입력 데이터를 1차원 벡터로 변환한다. 28x28 크기의 2D 이미지(즉, MNIST 데이터)를 1차원 벡터(28 * 28 = 784 길이)로 변환한다. 이 변환된 벡터는 신경망의 Dense 층에 입력으로 사용된다.

**2) Dense 레이어**

기본적인 완전 연결된 신경망 층(Fully Connected Layer)이다. 이 층에는 128개의 뉴런이 있고, 각 뉴런은 이전 층의 모든 출력과 연결된다. activation='relu'는 ReLU(Rectified Linear Unit) 활성화 함수를 사용한다는 것을 의미한다. ReLU는 딥러닝에서 가장 널리 사용되는 활성화 함수로, 비선형성을 모델에 추가하여 학습이 가능하게 한다.

**3) Dropout 레이어**

Dropout 층은 훈련 중 과적합(overfitting)을 방지하기 위해 사용된다. 이 층은 학습 중 무작위로 20% (0.2)의 뉴런을 "드롭"(즉, 비활성화)하여 모델이 특정 뉴런에 너무 의존하지 않도록 한다.

**4) Dense 레이어**

마지막 Dense 층은 10개의 뉴런을 가지고 있으며, MNIST 데이터셋의 10가지 클래스(0부터 9까지의 숫자)를 예측하기 위해 사용된다. activation='softmax'는 출력값을 확률로 변환하는 함수이다. 각 뉴런은 특정 숫자(클래스)에 해당하는 확률을 출력하게 된다.

모델을 컴파일한다. 컴파일 단계에서 모델은 다음과 같은 설정을 가진다.

******1) optimizer='adam'**:

Adam 옵티마이저는 딥러닝에서 자주 사용되는 최적화 알고리즘이다. 학습 과정에서 가중치를 업데이트하는 방법을 결정한다. Adam은 경사하강법의 변형된 버전으로, 학습 속도와 성능이 우수한 것으로 알려져 있다.

******2) loss='sparse_categorical_crossentropy'**

교차 엔트로피 손실 함수는 모델의 예측이 얼마나 정확한지를 측정한다. 여기서 sparse_categorical_crossentropy는 라벨이 원-핫 인코딩되지 않은 정수형일 때 사용되는 손실 함수이다. MNIST의 경우, 출력이 10개의 클래스 중 하나의 정수 값(0~9)이기 때문에 이 손실 함수를 사용한다.

******3) metrics=['accuracy']**

모델 평가 시 사용할 지표를 정의한다. 여기서는 accuracy(정확도)를 사용하여 모델이 얼마나 정확하게 예측하는지를 평가한다.

```
# 7. 모델 훈련
history = model.fit(x_train, y_train, epochs=10,
                    validation_data=(x_test, y_test))

# 8. 모델 평가
test_loss, test_accuracy = model.evaluate(x_test,  y_test, verbose=2)
print(f"Test Accuracy: {test_accuracy * 100:.2f}%")
```

모델을 훈련한다. model.fit() 함수로 훈련 데이터(x_train, y_train)를 사용하여 모델을 5번의 에포크(epoch) 동안 훈련한다. 모델이 fit 함수를 통해 훈련되는 동안, TensorFlow는 데이터셋을 기반으로 가중치를 조정하고, 손실(loss)을 최소화하도록 모델을 최적화한다. 훈련이 완료되면 모델은 주어진 데이터에 대해 학습된 상태가 된다.

**1) x_train**

훈련용 데이터셋의 입력(특징)이다. MNIST의 경우, 각 입력은 28x28 크기의 이미지이다.

**2) y_train**

훈련용 데이터셋의 출력(레이블)이다. 각 이미지는 0부터 9까지의 숫자로 라벨링된다.

**3) epochs=10**

전체 훈련 데이터셋에 대해 10번 반복하여 훈련을 수행한다. 1 epoch는 모델이 전체 훈련 데이터를 한 번 순회하며 학습하는 과정을 의미한다.

테스트 데이터를 사용하여 모델을 평가한다.

model.evaluate() 함수로 테스트 데이터(x_test, y_test)를 사용하고 평가 결과를 출력한다.

모델 평가 과정에서는 테스트 데이터셋을 사용하여 모델의 성능을 측정합니다. 여기서 측정된 성능(예: 정확도)은 모델이 학습하지 않은 새로운 데이터에 대해 얼마나 잘 일반화되는지를 나타냅니다.

**1) model.evaluate(x_test, y_test, verbose=2)**

이 코드는 훈련된 모델을 테스트 데이터셋에서 평가한다.

**2) x_test**

테스트 데이터셋의 입력이다. 훈련되지 않은 데이터로 모델을 평가하기 위해 사용된다.

**3) y_test**

테스트 데이터셋의 실제 레이블이다. 모델의 예측과 비교하여 정확도를 측정한다.

**4) verbose=2**

평가 중 출력되는 정보를 설정한다. 2로 설정하면 간결하게 출력된다.

**전체 코드 : tensor1_mnist.py**

```
import tensorflow as tf

# MNIST 데이터셋 로드
mnist = tf.keras.datasets.mnist
(x_train, y_train), (x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

# 모델 생성
model = tf.keras.models.Sequential([
    tf.keras.layers.Flatten(input_shape=(28, 28)),
    tf.keras.layers.Dense(128, activation='relu'),
    tf.keras.layers.Dropout(0.2),
    tf.keras.layers.Dense(10, activation='softmax')
])

# 모델 컴파일
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# 모델 훈련
history = model.fit(x_train, y_train, epochs=10,
                    validation_data=(x_test, y_test))

# 모델 평가
test_loss, test_accuracy = model.evaluate(x_test,  y_test, verbose=2)
print(f"Test Accuracy: {test_accuracy * 100:.2f}%")
```

정상적으로 실행되었다. 97.98%의 정답률이 나왔다.

```
Epoch 1/10
1875/1875 [==============================] - 8s 4ms/step - loss: 0.2927 - accuracy: 0.9143 - val_loss: 0.1435 - val_accuracy: 0.9554
Epoch 2/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.1406 - accuracy: 0.9578 - val_loss: 0.0970 - val_accuracy: 0.9689
Epoch 3/10
1875/1875 [==============================] - 6s 3ms/step - loss: 0.1048 - accuracy: 0.9685 - val_loss: 0.0844 - val_accuracy: 0.9732
Epoch 4/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0857 - accuracy: 0.9734 - val_loss: 0.0789 - val_accuracy: 0.9762
Epoch 5/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0724 - accuracy: 0.9776 - val_loss: 0.0786 - val_accuracy: 0.9764
Epoch 6/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0642 - accuracy: 0.9798 - val_loss: 0.0702 - val_accuracy: 0.9793
Epoch 7/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0552 - accuracy: 0.9820 - val_loss: 0.0764 - val_accuracy: 0.9778
Epoch 8/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0520 - accuracy: 0.9828 - val_loss: 0.0665 - val_accuracy: 0.9802
Epoch 9/10
1875/1875 [==============================] - 7s 4ms/step - loss: 0.0468 - accuracy: 0.9845 - val_loss: 0.0688 - val_accuracy: 0.9797
Epoch 10/10
1875/1875 [==============================] - 6s 3ms/step - loss: 0.0438 - accuracy: 0.9851 - val_loss: 0.0716 - val_accuracy: 0.9798
313/313 - 1s - loss: 0.0716 - accuracy: 0.9798 - 595ms/epoch - 2ms/step
Test Accuracy: 97.98%
```

다음의 코드로 학습 과정에서 생성한 데이터로 손실 함수와 정확도를 시각화해 본다.

```
import matplotlib.pyplot as plt
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

![[03 Attachments/티스토리 Vento AI Lab/847/847-002-Figure_2.png]]

![[03 Attachments/티스토리 Vento AI Lab/847/847-003-주한길.png]]
