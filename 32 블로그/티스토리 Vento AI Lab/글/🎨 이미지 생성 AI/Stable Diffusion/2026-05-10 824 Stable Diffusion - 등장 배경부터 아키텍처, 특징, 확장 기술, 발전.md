---
title: Stable Diffusion - 등장 배경부터 아키텍처, 특징, 확장 기술, 발전
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T21:14:55+09:00'
source: https://agapeuni.tistory.com/824
source_blog: agapeuni.tistory.com
post_id: 824
category: 🎨 이미지 생성 AI/Stable Diffusion
tags:
- AI이미지생성자동화
- CLIPUNetVAE동작원리
- LatentDiffusionModel설명
- LoRAControlNet활용
- SDXL활용방법
- StableCascade비교
- StableDiffusion구조가이드
- StableDiffusion아키텍처
- 생성형AI이미지모델비교
- 스테이블디퓨전원리
body_hash: bc4130b6c6650ccda1090e377a57c5b211ab38c2d9f48f1435df8c9bdf78db30
visibility: private
rag: exclude
---

# Stable Diffusion - 등장 배경부터 아키텍처, 특징, 확장 기술, 발전

- 원문: https://agapeuni.tistory.com/824
- 게시일: 2026-05-10T21:14:55+09:00
- 분류: 🎨 이미지 생성 AI/Stable Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/824/824-001-img1.daumcdn.png]]

## 1. Stable Diffusion 등장 배경

기존 이미지 생성 모델은 크게 두 가지 흐름이었다.

**첫째, GAN(Generative Adversarial Network) 기반 모델**
대표적으로 Generative Adversarial Network이 있다. 생성자와 판별자가 경쟁하며 학습한다. 결과는 빠르고 선명하지만 학습 불안정, 모드 붕괴 문제가 존재한다.

**둘째, Diffusion 기반 모델**
Diffusion Model은 노이즈를 점진적으로 제거하며 데이터를 복원하는 방식이다. 학습 안정성은 높지만 계산 비용이 매우 크다.

문제는 다음과 같다.

- GAN → 품질은 좋지만 불안정

- Diffusion → 안정적이지만 너무 느림

**이 한계를 해결한 것이 Latent Diffusion Model이다.**

핵심 아이디어는 “이미지 공간이 아니라 잠재 공간(latent space)에서 diffusion을 수행”하는 것이다.

이 접근으로 다음이 가능해졌다.

- 연산량 대폭 감소

- 개인 GPU에서도 실행 가능

- 오픈소스 생태계 확장

## 2. Stable Diffusion 아키텍처

Stable Diffusion은 크게 3개의 핵심 컴포넌트로 구성되어 있다. CLIP 텍스트 인코더가 프롬프트를 벡터로 바꾸고, U-Net이 노이즈를 단계적으로 제거해 잠재공간(latent)에서 이미지를 복원한 뒤, VAE가 최종 픽셀 이미지로 디코딩한다.

![[03 Attachments/티스토리 Vento AI Lab/824/824-002-img1.daumcdn.png]]

### 1) Text Encoder (CLIP)

텍스트 프롬프트를 임베딩 벡터로 변환한다.

텍스트 의미와 latent 이미지 공간을 매칭한다.

이 텍스트 임베딩이 U-Net의 생성 방향을 제어한다.

### 2) U-Net 기반 Diffusion Model

Diffusion의 핵심 엔진으로 노이즈 추가/제거 과정을 담당한다.

- 입력: 노이즈가 섞인 latent

- 출력: 노이즈 제거 방향

반복적으로 실행되면서 단계에 따라 점점 이미지가 선명해진다.

### 3) Variational Autoencoder (VAE)

이미지를 압축하고 복원하는 역할이다.

- Encoder → 이미지 → latent 벡터

- Decoder → latent → 이미지

고해상도 이미지를 저차원 공간으로 축소한다. (속도 향상)

Diffusion은 원본 이미지가 아니라 이 latent 공간에서 이루어진다.

## 3. 동작 흐름 (Pipeline)

전체 흐름은 다음과 같다.

- 텍스트 입력 → CLIP → 텍스트 임베딩 생성

- 랜덤 노이즈 생성

- U-Net이 노이즈 제거 반복

- latent 이미지 생성

- VAE Decoder → 실제 이미지 출력

“이해해서 그리는 것이 아니라, 노이즈를 점진적으로 제거하며 확률적으로 생성”

이 구조는 LLM의 Next Token Prediction과 유사한 패턴이다.

![[03 Attachments/티스토리 Vento AI Lab/824/824-003-img1.daumcdn.png]]

## 4. Stable Diffusion 특징

### 1) 개인 GPU에서 실행 가능

- Tesla T4, RTX 3060 이상이면 충분

- 온프레미스 환경에서도 운영 가능

### 2) 오픈소스 생태계

- 모델, LoRA, ControlNet 등 자유롭게 확장 가능

- 커뮤니티 중심 발전

- AUTOMATIC1111, ComfyUI 등 수많은 WebUI 툴이 발전.

### 3) 프롬프트 기반 제어

- 텍스트 → 이미지 생성

- Prompt Engineering 중요

### 4) 높은 확장성

- 이미지 편집

- 스타일 변환

- 영상 생성까지 확장 가능

## 5. Stable Diffusion 확장 기술

![[03 Attachments/티스토리 Vento AI Lab/824/824-004-img1.daumcdn.png]]

### 1) LoRA (Low-Rank Adaptation)

- 소량 데이터로 특정 스타일 학습

- 빠르고 가볍다

- 캐릭터, 화풍 생성에 핵심

### 2) ControlNet

- 포즈, 스케치, depth 등 조건 입력 가능

- 구조를 강하게 제어

### 3) DreamBooth

- 특정 인물/사물 학습

- 개인화 모델 생성

### 4) Img2Img / Inpainting

- 기존 이미지를 기반으로 변형

- 일부 영역만 수정 가능

## 6. Stable Diffusion 발전

### 1) Stable Diffusion v1 (2022.8)

- LMU Munich(CompVis) + Stability AI + Runway 공동 개발

- Latent Diffusion 기반, 512×512 이미지 생성 가능

- 오픈소스로 공개되어 전 세계적으로 폭발적인 확산

### 2) Stable Diffusion v2 (2022.11)

- 해상도 768×768 지원

- 새로운 text encoder(OpenCLIP) → 텍스트 이해력 강화

- Depth-to-Image, Upscaler 모델 제공

### 3) Stable Diffusion XL, SDXL (2023.7)

- 1024x1024 해상도, 품질 비약적 향상.

- 베이스(Base) + 리파이너(Refiner) 구조. → 디테일 향상

- 상업·디자인 업계에서 본격적으로 활용

### 4) Stable Cascade (2024 초)

- 3단계 Cascaded Diffusion 구조 도입 (Stage A, B, C)

- 효율성과 디테일을 동시에 잡은 차세대 모델

- 초고해상도 출력 및 멀티모달 확장 기반 마련

### 5) Stable Diffusion 3 (2024~2025)

- Stability AI, SDXL 후속으로 SD3 개발

- 텍스트 이해력 강화, 멀티모달 지원(이미지+텍스트+비디오 확장).

- 오픈소스 생태계와 API 상용화 전략 동시 진행

### 참고) Stable Diffusion과 Stable Cascade의 차이

| 구조 | 단일 Latent Diffusion | 다단계 Cascade 구조 |
| --- | --- | --- |
| 생성 방식 | 한 번에 이미지 생성 | 단계별 생성 (의미 → 이미지 → 업스케일) |
| 아키텍처 | VAE + U-Net + CLIP | Prior + Decoder + Upscaler |
| 기반 모델 | Latent Diffusion | Würstchen 계열 |
| 속도 | 비교적 느림 | 더 빠르고 효율적 |
| 메모리 | 중간~높음 | 낮음 (고압축 latent) |
| 품질 | 안정적, 검증됨 | 이론상 고효율, 아직 초기 |
| 확장성 | LoRA, ControlNet 등 풍부 | 생태계 부족 |
| 실무 활용 | 매우 높음 (표준) | 낮음 (연구/실험 단계) |

## 6. 최근 동향

“Stable Diffusion은 모델이 아니라, 자동화 가능한 생성 시스템으로 진화 중이다.”

### 1) 구조 변화

U-Net 중심에서 Transformer 기반 Diffusion(예: DiT)으로 이동 중이다.
→ LLM과 구조적으로 통합되는 방향

### 2) 속도 혁신

LCM, Turbo 모델 등장으로 거의 실시간 생성 가능
→ 20~50 step → 1~4 step 수준으로 감소

### 3) 제어 강화

ControlNet, IP-Adapter 등으로 이미지 구조까지 정밀 제어
→ 텍스트 중심 → 멀티 입력 기반 생성

### 4) 개인화 표준화

DreamBooth → LoRA 중심으로 전환
→ 가볍고 빠른 커스터마이징 가능

### 5) 자동화 전환 (핵심)

단순 생성 → Agent 기반 자동화 시스템으로 변화
→ 프롬프트 생성부터 콘텐츠 제작까지 자동화

![[03 Attachments/티스토리 Vento AI Lab/824/824-005-주한길.png]]
