---
title: Stable Diffusion - 브라우저에서 바로 실행하는 Online 버전
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T21:08:53+09:00'
source: https://agapeuni.tistory.com/822
source_blog: agapeuni.tistory.com
post_id: 822
category: 🎨 이미지 생성 AI/Stable Diffusion
tags:
- AI이미지생성온라인서비스
- ComfyUIForgeUI비교
- Flux이미지생성AI
- SDXL이미지생성활용
- StableCascadeVRAM절약
- StableDiffusionOnline가이드
- StableDiffusion발전과정
- 생성형AI이미지모델추천
- 스테이블디퓨전로컬설치비교
- 스테이블디퓨전온라인사용법
body_hash: 61fab3ff354b95692ebad4bc20ab6f215780465a8de19951c7a880610fef6c5d
visibility: private
rag: exclude
---

# Stable Diffusion - 브라우저에서 바로 실행하는 Online 버전

- 원문: https://agapeuni.tistory.com/822
- 게시일: 2026-05-10T21:08:53+09:00
- 분류: 🎨 이미지 생성 AI/Stable Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/822/822-001-img1.daumcdn.png]]

인공지능 이미지 생성 기술은 지난 몇 년 사이 눈부시게 발전했다. 그 중심에는 바로 스테이블 디퓨전(Stable Diffusion)이 있다. 스테이블 디퓨전은 **2022년 8월**, Stability AI가 독일 뮌헨 대학 연구팀(CompVis), Runway, EleutherAI 등과 함께 공개한 오픈소스 모델이다.

이전까지 이미지 생성 AI는 막대한 연산 자원과 고가의 장비가 필요했지만, 스테이블 디퓨전은 Latent Diffusion Model(LDM)을 적용하여 일반 GPU 환경에서도 실행할 수 있다. 텍스트를 입력하면 AI가 이미지를 생성하는 기술이 대중에게 열린 순간이었고, 이는 곧 “**생성형 AI의 민주화**”라 불릴 만큼 혁명적인 사건이었다.

Automatic1111 WebUI 이후 **ComfyUI**와 **ForgeUI** 같은 새로운 인터페이스가 등장하며 모델 교체와 기능 확장이 더 쉬워졌다.

## Stable Diffusion 발전과정

**SD v1.x (2022년)**

- v1.4와 v1.5 버전은 가장 널리 알려졌으며, 지금도 많은 커뮤니티 모델과 플러그인이 이 기반에서 만들어졌다.

- LoRA, Dreambooth 같은 커스텀 학습 기법이 본격적으로 퍼져나간 것도 이 시기다.

**SD v2.x (2022년 말)**

- 업스케일링, 인페인팅 기능이 강화되었지만, 학습 데이터와 안전성 문제로 인해 사용자들은 여전히 v1.5를 더 선호했다.

**Stable Diffusion XL (SDXL, 2023년)**

- 해상도를 1024x1024까지 기본 지원하며 디테일한 표현력이 크게 개선되었다.

- 특히 **Base + Refiner 구조**로 고품질 이미지를 만들어낼 수 있어 상업적 활용도 활발해졌다.

**Stable Cascade (2024 초)**

- 이미지를 단계적으로 생성하는 **Stage 기반 구조**를 채택하여 속도와 효율성을 강화했다.

- 적은 GPU 메모리로도 고해상도 이미지를 만들 수 있다.

**Flux (2024 하반기)**

- Stability AI가 공개한 차세대 모델로, 기존 확산(Diffusion) 방식이 아닌 **흐름 기반(Flow Matching)** 방식을 사용한다.

- 속도와 품질 면에서 한 단계 도약한 모델로, 차세대 이미지 생성 AI의 방향성을 보여주고 있다.

| 연도 | 버전 / 모델 | 특징 |
| --- | --- | --- |
| 2022.08 | Stable Diffusion v1.4 | 오픈소스 공개, Latent Diffusion 기반. 텍스트 → 이미지 혁명 시작. |
| 2022.10 | v1.5 | 가장 대중적 버전. DreamBooth, LoRA 학습 붐. |
| 2022.11~12 | v2.x | 업스케일링·인페인팅 강화. 그러나 커뮤니티는 여전히 v1.5 선호. |
| 2023.07 | SDXL (Stable Diffusion XL) | 해상도 1024 기본, Base + Refiner 구조, 상업적 활용 본격화. |
| 2024 초 | Stable Cascade | 다단계(Stage) 방식. 빠르고 VRAM 절약. |
| 2024 하반기 | Flux | 차세대 모델. Diffusion → Flow Matching 전환. 효율성과 품질 개선. |

## Stable Diffusion Online

Stable Diffusion Online은 로컬 설치 없이 웹에서 Stable Diffusion을 사용할 수 있는 서비스다. 성능좋은 그래픽카드가 장착되어 있는 컴퓨터에 설치하지 않아도 되고 구글 Colab에 설정하고 실행하지 않아도 된다. 언제든지 온라인에서 이미지를 손쉽게 생성할 수 있다.

아래의 주소에서 바로 실행해 보자.

[https://stablediffusionweb.com/#demo](https://stablediffusionweb.com/#demo)

![[03 Attachments/티스토리 Vento AI Lab/822/822-002-img1.daumcdn.png]]

## 이미지 생성 1

![[03 Attachments/티스토리 Vento AI Lab/822/822-003-img1.daumcdn.png]]

화면에 다음과 같이 입력하고 "그리기"버튼을 클릭했다.

- 프롬프트 : a woman teacher giving a lecture on the blackboard (칠판에서 강의를 하고 있는 여자 선생님)

- 모델 : 표준

- 스타일 :자동

![[03 Attachments/티스토리 Vento AI Lab/822/822-004-img1.daumcdn.webp]]

## 이미지 생성 2

![[03 Attachments/티스토리 Vento AI Lab/822/822-005-img1.daumcdn.png]]

이번에는 아래와 같이 프롬프트를 입력하고 모델은 향상을 선택하고 생성해 본다.

- 프롬프트 : a girl wearing a dress made of milky way with outer gods, conquest the earth, occlusion shadow, specular reflection, rim light, unreal engine, artgerm, artstation, art by hiroaki samura and ilya kuvshinov and ossdraws, extremely beautiful and aesthetic shape of face and body

- 모델 : 향상

- 스타일 :자동

![[03 Attachments/티스토리 Vento AI Lab/822/822-006-img1.daumcdn.png]]

## 온라인 vs 로컬 비교

| 구분 | 온라인 | 로컬 |
| --- | --- | --- |
| 설치 | 불필요 | 필요 |
| 초기 비용 | 낮음 | GPU 필요 |
| 운영 비용 | 지속 과금 | 없음 |
| 속도 | 빠름 | GPU 성능 의존 |
| 커스터마이징 | 제한 | 매우 높음 |
| 자동화 | 제한 | 매우 유리 |
| 보안 | 낮음 | 높음 |

![[03 Attachments/티스토리 Vento AI Lab/822/822-007-주한길.png]]
