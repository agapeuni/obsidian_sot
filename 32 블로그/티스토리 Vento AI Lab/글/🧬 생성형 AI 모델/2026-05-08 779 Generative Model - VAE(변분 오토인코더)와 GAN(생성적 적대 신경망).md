---
title: Generative Model - VAE(변분 오토인코더)와 GAN(생성적 적대 신경망)
type: blog-archive
status: active
created: '2026-05-08'
updated: '2026-08-16'
published: '2026-05-08T20:59:13+09:00'
source: https://agapeuni.tistory.com/779
source_blog: agapeuni.tistory.com
post_id: 779
category: 🧬 생성형 AI 모델
tags:
- GAN개념정리
- GenerativeAdversarialNetwork설명
- VAEGAN비교
- VAEGAN활용사례
- VAE개념정리
- VariationalAutoencoder가이드
- 딥러닝이미지생성모델
- 생성모델딥러닝
- 생성자판별자구조
- 잠재공간LatentSpace
body_hash: bd484fcb1c55e285855fad3b97b5127b3824b37a2feeb57f63d729451b4352ed
visibility: private
rag: exclude
---

# Generative Model - VAE(변분 오토인코더)와 GAN(생성적 적대 신경망)

- 원문: https://agapeuni.tistory.com/779
- 게시일: 2026-05-08T20:59:13+09:00
- 분류: 🧬 생성형 AI 모델

## 본문

![[03 Attachments/티스토리 Vento AI Lab/779/779-001-img1.daumcdn.png]]

VAE(Variational Autoencoder)와 GAN(Generative Adversarial Network)는 딥러닝에서 생성 모델로 널리 사용되는 대표적인 두 가지 기술이다. 이들은 모두 기존 데이터를 학습하여 새로운 데이터를 생성하는 데 중점을 둔 모델이라는 공통점을 가지고 있지만, 그 작동 방식과 목표에는 분명한 차이가 있다.

VAE는 확률론적인 접근법을 기반으로 작동하며, 입력 데이터를 잠재 공간(latent space)으로 변환하고 이를 이용해 데이터를 생성한다. 이 과정에서 VAE는 데이터의 분포를 학습하여, 학습 데이터와 유사한 새로운 데이터를 생성할 수 있다. VAE는 잠재 공간에서의 조작을 통해 데이터의 특징을 조절하거나 새로운 조합을 만들 수 있는 점에서 활용도가 높다. 예를 들어, 얼굴 이미지를 학습한 VAE는 특정 표정, 머리카락 색상, 또는 조명 조건 등을 제어하여 새로운 얼굴 이미지를 생성할 수 있다.

반면, GAN은 두 개의 신경망, 즉 생성자(Generator)와 판별자(Discriminator)가 서로 경쟁하며 학습하는 구조를 가지고 있다. 생성자는 새로운 데이터를 생성하려고 시도하며, 판별자는 생성된 데이터가 진짜(실제 데이터)인지 가짜인지 판별한다. 이 경쟁 과정을 통해 생성자는 점점 더 실제와 구분이 어려운 데이터를 생성할 수 있게 된다. GAN은 고해상도 이미지 생성, 동영상 생성, 스타일 전이(style transfer)와 같은 고품질 데이터 생성 작업에서 강력한 성능을 발휘한다.

VAE와 GAN은 생성 모델이라는 공통점을 공유하지만, VAE는 데이터 분포의 이해와 잠재 공간 조작에 초점을 맞추는 반면, GAN은 생성자와 판별자의 경쟁을 통해 사실감 높은 데이터를 생성하는 데 강점을 가지고 있다.

## VAE (Variational Autoencoder)

VAE는 확률적 접근법을 사용하는 오토인코더(encoder-decoder)의 변형이다. 인코더는 입력 데이터를 잠재 공간(latent space)의 분포로 변환하고, 디코더는 이 잠재 공간에서 샘플링된 값으로 새로운 데이터를 생성하여 원본과 유사한 데이터를 만든다.

**인코더(Encoder)**는 입력 데이터를 잠재 공간에 매핑하고 잠재 변수의 평균과 분산을 예측한다. **디코더(Decoder)**는 잠재 공간에서 샘플링된 값을 원래 데이터 형태로 복원한다.

![[03 Attachments/티스토리 Vento AI Lab/779/779-002-1.png]]

[출처] [https://data-science-blog.com/blog/2022/04/19/variational-autoe](https://data-science-blog.com/blog/2022/04/19/variational-autoencoders/)[ncoders/](https://data-science-blog.com/blog/2022/04/19/variational-autoencoders/)

자동 인코더의 핵심 개념은 **잠재 공간(latent space)**이다. 잠재 공간은 관찰된 데이터의 기본 구조를 설명하는 **잠재 변수(latent variable)**를 포함하며, 직접 관찰할 수 없는 데이터의 숨겨진 특징을 나타낸다. 예를 들어, 다리에 차량 무게를 측정하는 센서가 있다고 가정하면, 차량 무게(관찰 변수)는 측정 가능하지만, 차량 유형(잠재 변수)은 직접 알 수 없다. 하지만 차량 유형이 무게에 영향을 미친다는 것을 추론할 수 있다.

자동 인코더의 목표는 이러한 잠재 변수를 학습하고, 입력 데이터를 효율적으로 모델링하는 것이다. 데이터 분포를 명시적으로 학습하므로 잠재 공간의 의미를 해석하기 쉽다. 하지만 생성된 데이터의 품질이 GAN에 비해 낮을 수 있다.

****

****

## GAN (Generative Adversarial Network)

GAN은 이미지를 생성하는 모델로 두 개의 신경망(생성기와 판별기)이 서로 경쟁하면서 데이터를 생성하는 모델이다. 제로섬 게임처럼 훈련하며, 생성기가 판별기를 속일 수 있을 때까지 서로 경쟁하면서 성능을 개선해 나간다.

- **생성기(Generator)********** : 임의의 노이즈에서 시작해 가짜 데이터를 생성하고 진짜와 비슷한 데이터를 만들도록 학습한다.

- **판별기(Discriminator)********** : 입력 데이터가 진짜(학습 데이터)인지 가짜(생성기 출력)인지 구별한다. 생성자를 이기려고 학습한다.

판별자는 진짜와 가짜를 정확히 구별하려 노력하고 생성자는 판별자를 속이려 노력한다. 이 두 신경망은 서로 경쟁하며 학습한다. 생성기는 판별기를 속이기 위해 더 사실적인 데이터를 만들고, 판별기는 더 정확히 진짜와 가짜를 구별하려 한다. 이렇게 적대적으로 훈련되면서 점점 더 현실과 구별하기 어려운 데이터를 생성할 수 있게 된다.

![[03 Attachments/티스토리 Vento AI Lab/779/779-003-2.jpg]]

[출처] [https://www.linkedin.com/pulse/exploring-fascinating-realm-generative-adversarial-networks-kaurav](https://www.linkedin.com/pulse/exploring-fascinating-realm-generative-adversarial-networks-kaurav)

VAE는 분포를 학습하고 이해하는 데 적합하며, GAN은 고품질의 현실적인 데이터를 생성하는 데 강점이 있다. VAE은 훈련이 안정적이지만 평균적인 특징으로 인해 흐릿한 이미지를 생성하는 경향이 있다. 반면에 GAN은 고품질의 선명한 이미지를 생성하지만, 훈련이 불안정할 수 있어 모드가 붕괴하거나 학습 실패 가능성이 있다.

## VAE와 GAN의 비교

| 특징 | VAE | GAN |
| --- | --- | --- |
| 모델 구조 | 확률적 오토인코더 | 생성자와 판별자의 경쟁 구조 |
| 손실 함수 | 재구성 손실 + KL 발산 | 판별자와 생성자의 미니맥스 게임 |
| 생성 데이터 품질 | 보통 (약간 흐릿함) | 매우 높음 |
| 학습 안정성 | 안정적 | 불안정할 수 있음 |
| 활용 사례 | 데이터 압축, 잠재 공간 분석 | 고품질 이미지/비디오 생성 |

![[03 Attachments/티스토리 Vento AI Lab/779/779-004-주한길.png]]
