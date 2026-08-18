---
title: Easy Diffusion - Easy Diffusion v3.0.9c 화면 구성
type: blog-archive
status: active
created: '2026-05-09'
updated: '2026-08-16'
published: '2026-05-09T11:32:39+09:00'
source: https://agapeuni.tistory.com/811
source_blog: agapeuni.tistory.com
post_id: 811
category: 🎨 이미지 생성 AI/Easy Diffusion
tags:
- AI이미지생성도구
- EasyDiffusionGPU설정
- EasyDiffusionImageSettings
- EasyDiffusionRenderSettings
- EasyDiffusionSystemSettings
- EasyDiffusion사용법
- EasyDiffusion설정가이드
- EasyDiffusion프롬프트입력
- EasyDiffusion화면구성
- StableDiffusionUI설명
body_hash: 3052ceb3806daf38c68eb361346f1a13b843d547660b8c1c241be8665810beff
visibility: private
rag: exclude
---

# Easy Diffusion - Easy Diffusion v3.0.9c 화면 구성

- 원문: https://agapeuni.tistory.com/811
- 게시일: 2026-05-09T11:32:39+09:00
- 분류: 🎨 이미지 생성 AI/Easy Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/811/811-001-img1.daumcdn.png]]

**Easy Diffusion v3.0.9c**의 화면구성을 살펴보자.

![[03 Attachments/티스토리 Vento AI Lab/811/811-002-img1.daumcdn.png]]

## 상단 탭 메뉴

![[03 Attachments/티스토리 Vento AI Lab/811/811-003-img1.daumcdn.png]]

다섯개의 탭 메뉴가 있다.

- **Generate** : 이미지를 만드는 기본 화면이다. 프롬프트를 입력하고 설정을 조정하는 공간이다.

- **Settings** : 전체 환경 설정 메뉴다. 기본 해상도, 기본 모델, VRAM 관련 옵션, 저장 경로 등을 바꿀 수 있다.

- **Help & Community** : 사용 설명서와 커뮤니티 연결 창이다. 문제가 생겼을 때 참고하는 영역이다.

- **What’s new** : 업데이트 내역을 보여준다. 새로 추가된 기능이나 수정된 사항을 확인할 수 있다.

- **Model tools** : 모델 관리 메뉴다. 모델 다운로드, 삭제, 변환, 관리 등을 할 수 있다.

## 이미지 생성 패널

이 화면은 Easy Diffusion에서 실제로 이미지를 생성하는 곳이다.

![[03 Attachments/티스토리 Vento AI Lab/811/811-004-img1.daumcdn.png]]

**Enter Prompt** : 프롬프트를 입력한다.

**Load from a file** : 프롬프트를 파일에서 불러오는 기능이다.

**Image Modifiers** : 스타일, 조명, 화질, 카메라 효과 등을 설정한다.

**Embedding** : 학습된 스타일이나 개념을 불러오는 기능이다.

****

**Negative Prompt (optional)** : “이런 요소는 제외해라”라고 지시하는 공간이다.

**Negative Embedding** : 학습된 스타일이나 개념을 불러오는 기능이다.

## Initial Image (img2img) 영역

**Browse** : PC 이미지를 업로드하는 기능이다..

**Draw** : 간단한 스케치를 직접 그리는 기능이다. 이 기능을 사용하면 완전한 텍스트 생성이 아니라 “기존 이미지를 변형”하는 작업이 된다.

****

**Make Image** : 지금까지 입력한 텍스트, 모델, 시드, 샘플러, 모든 설정을 종합해 노이즈를 제거하는 확률적 과정을 시작하는 버튼이다.

## Image Settings

Easy Diffusion의 Image Settings 전체 제어 패널이다. 상세한 설정으로 생성할 이미지를 제어한다.

![[03 Attachments/티스토리 Vento AI Lab/811/811-005-img1.daumcdn.png]]

**Seed** : Seed는 난수의 시작점이다. Random을 선택하면 무작위로 입력한다. 같은 Seed 값 설정이면 거의 같은 결과가 나온다.

**Number of Images** : 한 번에 몇 장을 만들지 정한다. parallel 값은 동시에 생성할 개수다. VRAM을 더 사용한다.

**Model**: 이미지를 생성할 모델을 선택한다. 모델은 화풍이 아니라 “세계관”에 가깝다.

**Clip Skip** : 텍스트 해석 깊이를 조절한다. 미묘하게 얼굴 분위기가 달라진다.

**ControlNet Image** : 포즈나 구조를 강제하고 싶을 때 사용한다. 텍스트의 자유도를 줄이고, 구조의 정확도를 높이는 장치다.

**Custom VAE** : 생성하는 이미지에 색감과 디테일 복원에 영향을 준다. 잘 맞는 VAE를 쓰면 더 자연스럽다.

**Sampler**: 이미지를 생성할 때 사용하는 샘플 방식이다. 노이즈 제거 알고리즘이다. 같은 재료라도 조리법이 다르면 결과가 달라진다.

**Image Size** : 가로, 세로 이미지 크기를 정한다. 해상도는 VRAM 사용량과 직결된다.

**Inference Steps** : 노이즈 제거 반복 횟수다. 20~30 구간이 효율적이다.

**Guidance Scale** : 프롬프트를 얼마나 강하게 따를지 정한다. 값이 높을수록 프롬프트에 집착한다. 7~8 값을 입력한다.

**LoRA** : LoRA는 특정 스타일이나 얼굴 특성을 주입한다. 0.5면 은은하게 적용된다. 1.0 이상이면 개성이 강해진다.

**Seamless Tiling** : 반복 패턴용 옵션이다. 텍스처 제작 시 사용한다.

**Output Format** : 결과물 형식을 정한다. 작업용이면 PNG가 좋다. JPEG는 압축 손실이 있다.

**Image Quality** : 압축률이다. 높을수록 용량이 커진다.

**Enable VAE Tiling** : 큰 이미지 생성 시 메모리 절약 옵션이다.

## Render Settings

![[03 Attachments/티스토리 Vento AI Lab/811/811-006-img1.daumcdn.png]]

**Show live preview**: 실시간 미리보기. VRAM 더 사용.

**Fix incorrect faces and eyes** : 얼굴 왜곡 보정 기능이다. 인물 생성 시 매우 유용하다.

**Scale up by 4x with RealESRGAN**: 업스케일 기능이다. 해상도를 키우면서 디테일을 보강한다.

**Show only the corrected/upscaled image**: 보정된 결과만 표시한다.

> 프롬프트는 아이디어고, Seed는 주사위이며,
> Sampler는 계산 방식이고, Guidance는 간섭 강도다.

## System Settings

작업 환경을 정의한다. 이미지 한 장이 아니라, 작업 방식을 정한다.

![[03 Attachments/티스토리 Vento AI Lab/811/811-007-img1.daumcdn.png]]

**Theme** : UI 테마 설정이다. Light로 되어 있다.

**Auto-Save Images** : 생성된 이미지를 자동 저장한다. 켜두는 것이 안전하다. 작업 손실 방지용이다.

**Save Location** : 이미지가 저장되는 경로다. 지금은 /home/sgkim/Easy-Diffusion/output 로 설정되어 있다.

**Metadata format** : 이미지에 프롬프트 등 메타정보를 저장할지 결정한다. 작업 재현을 하려면 메타 저장이 유리하다.

**Models Folder** : 모델이 저장되는 폴더 경로다. 여기 경로를 잘 관리하면 모델 정리가 편해진다.

**Block NSFW images** : 민감 이미지 자동 블러 처리 옵션이다. 필요에 따라 선택한다.

**Enable Sound** : 작업 완료 시 알림음. 이미지 생성이 완료될 때 소리로 알 수 있어 유용하다.

**Process newest jobs first**: 대기열 처리 순서를 바꾼다. 여러 명이 접속하는 환경에서 의미가 있다.

**Extract LoRA tags from the prompt**: 프롬프트에 <lora:모델이름:0.4> 같은 문장이 있으면 자동 적용한다.

**Open browser on startup :**서버 실행 시 자동 브라우저 오픈 여부다. 원격 서버면 꺼도 된다.

![[03 Attachments/티스토리 Vento AI Lab/811/811-008-img1.daumcdn.png]]

**GPU Memory Usage** : Balanced로 설정되어 있다. High는 VRAM 최대 사용, 속도 빠름. Low는 VRAM 적게 사용, 느림.

**Use CPU (not GPU) :**GPU 대신 CPU 사용. CPU만 사용하면 이미지 생성이 매우 느리다. 일반적으로 끈다.

**Automatically pick the GPUs :**멀티 GPU 자동 선택.

**Auto-Save Settings**: 브라우저 로드시 설정 복원. 켜두는 것이 편하다.

**Confirm dangerous actions :**위험 작업 확인 옵션. 데이터 보호용이다.

**Profile Name** : 프로파일 이름이다. 설정 세트를 나눠 쓰는 경우 유용하다.

Beta channel : 최신 기능을 먼저 받는다. 안정성이 낮을 수 있다.

**Use the new v3 engine (diffusers) :**v3 엔진 사용 여부다. LoRA, ControlNet, SDXL 등 최신 기능은 이 엔진이 유리하다.

![[03 Attachments/티스토리 Vento AI Lab/811/811-009-img1.daumcdn.png]]

**Make Stable Diffusion available on your network :**네트워크 공유 옵션이다. 켜져 있다. 다른 기기에서 접속 가능하다는 의미다.

**Network port :**17850 포트 사용 중이다. 외부 접속 허용 환경이다.

**Cloudflare tunnel :**공인 IP 없이 외부 공유할 수 있는 기능이다.

![[03 Attachments/티스토리 Vento AI Lab/811/811-010-주한길.png]]
