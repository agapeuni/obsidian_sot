---
title: Stable Diffusion - 텍스트 입력으로 자유롭게 이미지를 생성
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T20:56:08+09:00'
source: https://agapeuni.tistory.com/817
source_blog: agapeuni.tistory.com
post_id: 817
category: 🎨 이미지 생성 AI/Stable Diffusion
tags:
- AI이미지생성방법
- LatentDiffusionModel원리
- StableDiffusionCheckpoint추천
- StableDiffusionLoRA활용
- StableDiffusion개요
- StableDiffusion사용법
- StableDiffusion샘플링설정
- StableDiffusion아키텍처
- StableDiffusion프롬프트가이드
- 이미지생성AI가이드
body_hash: c6318cee3fb81f8c0fbb3d60e1b46fd46b3676b38c2bf2962a208bbf8a046534
visibility: private
rag: exclude
---

# Stable Diffusion - 텍스트 입력으로 자유롭게 이미지를 생성

- 원문: https://agapeuni.tistory.com/817
- 게시일: 2026-05-10T20:56:08+09:00
- 분류: 🎨 이미지 생성 AI/Stable Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/817/817-001-img1.daumcdn.png]]

1. Stable Diffusion 개요

Stable Diffusion은 텍스트 입력만으로 이미지를 생성하는 text-to-image 기반의 오픈소스 인공지능 모델이다. 사용자는 프롬프트만 입력하면 원하는 장면, 인물, 스타일을 손쉽게 만들어낼 수 있다.

최근에는 다양한 커스텀 모델과 LoRA가 공개되면서, 전문 지식이 없는 사용자도 고품질 이미지를 제작할 수 있는 환경이 빠르게 확산되고 있다. 특히 개인 GPU 환경에서도 수 초 내 결과를 생성할 수 있어 활용성이 매우 높다.

또한 Stable Diffusion은 단순 이미지 생성에 그치지 않는다. image-to-image 변환, 스타일 변경, 업스케일링, 특정 영역 수정(Inpainting) 등 다양한 기능을 제공한다. 이러한 확장성은 콘텐츠 제작 자동화 측면에서 매우 중요한 장점이다.

## 2. Stable Diffusion 아키텍처

![[03 Attachments/티스토리 Vento AI Lab/817/817-002-img1.daumcdn.jpg]]

Stable Diffusion 아키텍처

Stable Diffusion은 Latent Diffusion Model 구조를 기반으로 동작한다. 핵심은 고해상도 이미지를 직접 처리하는 것이 아니라, 저차원의 잠재 공간(latent space)에서 연산을 수행한다는 점이다. 모델은 각 단계에서 샘플의 노이즈를 약간 제거하는 방법을 예측하도록 훈련되며, 몇 번의 반복 후에 결과를 얻는다.

Stable Diffusion 아키텍처에는 세 가지 주요 구성 요소가 있다. 구성 요소 두 개는 샘플을 더 낮은 차원의 잠재 공간으로 줄인 다음 무작위 가우시안 노이즈를 제거한다. 나머지 구성 요소는 텍스트 처리를 위한 것이다.

### 1) VAE (Autoencoder)

VAE는 이미지를 압축하고 복원하는 역할을 담당한다.
입력 이미지를 저차원 잠재 공간으로 변환하고, 최종 결과를 다시 원본 해상도로 복원한다.

- 인코더: 이미지를 latent로 압축

- 디코더: latent를 이미지로 복원

이 과정을 통해 연산 비용을 크게 줄이면서도 품질을 유지할 수 있다.

### 2) U-Net (Diffusion 핵심 엔진)

U-Net은 노이즈 제거를 담당하는 핵심 모델이다.
랜덤 노이즈 상태에서 시작하여 점진적으로 의미 있는 이미지로 복원한다.

- 입력: 노이즈가 섞인 latent

- 출력: 노이즈가 제거된 latent

이 과정이 반복되면서 점점 선명한 이미지가 만들어진다.

### 3) 텍스트 인코더

텍스트 인코더는 프롬프트를 벡터 형태로 변환한다.
이 벡터가 U-Net에 전달되어 “어떤 이미지를 생성해야 하는지” 방향을 결정한다.

즉, 텍스트 의미 → 이미지 생성 방향으로 연결하는 역할을 수행한다.

## 3. Stable Diffusion 구성 단계

Stable Diffusion은 크게 두 단계의 확률적 과정으로 동작한다.

### 1) Forward Diffusion

원본 데이터에 점진적으로 노이즈를 추가하는 과정이다.
이미지는 반복적으로 변형되면서 결국 완전한 랜덤 노이즈 상태가 된다.

이 과정은 학습 단계에서 사용되며, 모델이 “노이즈가 어떻게 추가되는지”를 이해하게 만든다.

![[03 Attachments/티스토리 Vento AI Lab/817/817-003-img1.daumcdn.jpg]]

### 2) Parametrized Reverse

Forward Diffusion의 역과정이다.
랜덤 노이즈에서 시작하여 점진적으로 노이즈를 제거하면서 이미지를 생성한다.

- 노이즈 → 의미 있는 구조 → 최종 이미지

이 과정이 Stable Diffusion의 핵심이며, 실제 이미지 생성은 이 단계에서 이루어진다.

![[03 Attachments/티스토리 Vento AI Lab/817/817-004-img1.daumcdn.jpg]]

## 4. 작업 결과

테스트를 위해 아래와 같은 값을 입력해 보았다. 입력 값은 인터넷에서 검색한 결과를 참고했다.

#### 【 Positive 프롬프트 】

<lora:koreanDollLikeness_v15:0.3>, 8k, raw photo, (masterpiece), (best quality), highres, (realistic, photo-realistic:1.4),ultra detailed, physically-based rendering, detailed beautiful eyes and detailed face, 1girl, hair ribbon, a pretty gold necklace, in house

#### 【 Negative 프롬프트 】

ng_deepnegative_v1_75t, paintings, sketches, (worst quality:2), (low quality:2), (normal quality:2), lowres, normal quality, ((monochrome)), ((grayscale)), skin spots, acnes, skin blemishes, age spot, ((wrong feet)),(wrong shoes), bad feet, distorted, blurry, bad hands, missing fingers, multiple feet, bad knees, extra fingers

Stable Diffusion checkpoint : chilloutmix_NiPrunedFp32Fix.safetensors

Sampling method : Euler a

Sampling steps :25

CFG Scale : 6

Seed : -1

결과를 보면 머리카락 디테일, 광원 처리, 그림자 표현까지 매우 자연스럽게 구현되었다. 특히 피부 질감과 눈 디테일은 실제 사진과 구분이 어려운 수준이다.

![[03 Attachments/티스토리 Vento AI Lab/817/817-005-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/817/817-006-img.png]]

다만 한 가지 특징적인 한계도 존재한다. 지나치게 완벽한 결과는 오히려 “비현실적인 느낌”을 줄 수 있다. 이는 모델이 학습된 이상적인 패턴을 과도하게 반영하기 때문이다.

![[03 Attachments/티스토리 Vento AI Lab/817/817-007-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/817/817-008-img.png]]

## 핵심 정리

Stable Diffusion의 본질은 단순하다. “노이즈에서 시작해 점진적으로 이미지를 복원하는 과정”이다. 하지만 실제 활용에서는 다음 세 가지 요소가 결과 품질을 좌우한다.

이 세 가지를 어떻게 조합하느냐에 따라 결과는 크게 달라진다.

- 프롬프트 설계

- 모델(Checkpoint, LoRA) 선택

- 샘플링 파라미터 설정

![[03 Attachments/티스토리 Vento AI Lab/817/817-009-주한길.png]]
