---
title: Easy Diffusion - 사용하기 편리한 Easy Diffusion
type: blog-archive
status: active
created: '2026-05-09'
updated: '2026-08-16'
published: '2026-05-09T11:30:51+09:00'
source: https://agapeuni.tistory.com/808
source_blog: agapeuni.tistory.com
post_id: 808
category: 🎨 이미지 생성 AI/Easy Diffusion
tags:
- AI이미지생성도구추천
- EasyDiffusionLoRA적용방법
- EasyDiffusion사용법
- EasyDiffusion설치방법
- EasyDiffusion시스템요구사항
- EasyDiffusion윈도우설치
- EasyDiffusion이미지설정가이드
- EasyDiffusion프롬프트작성법
- StableDiffusion모델변경방법
- StableDiffusion초보자가이드
body_hash: 5a042de9c32ead8e906f333ef93de5b5d317bf1452281b4d2ac56d539ce51037
visibility: private
rag: exclude
---

# Easy Diffusion - 사용하기 편리한 Easy Diffusion

- 원문: https://agapeuni.tistory.com/808
- 게시일: 2026-05-09T11:30:51+09:00
- 분류: 🎨 이미지 생성 AI/Easy Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/808/808-001-img1.daumcdn.png]]

## 1. Easy Diffusion

Easy Diffusion은 Stable Diffusion을 가장 쉽게 설치하고 실행할 수 있도록 도와주는 배포판이다. 초보자도 몇 번의 클릭만으로 쉽게 설치할 수 있고 텍스트 입력만으로 이미지를 생성할 수 있다. 복잡한 설정에 익숙하지 않은 사람에게 유용하다.

[https://easydiffusion.github.io/](https://easydiffusion.github.io/)

[Easy Diffusion v3

A simple 1-click way to create beautiful images on your computer, by installing Stable Diffusion. No dependencies or technical knowledge required

easydiffusion.github.io](https://easydiffusion.github.io/)

## 2. 시스템 요구사항

Easy Diffusion은 Python으로 작성되어 있어 실행을 위해 Python 환경이 필요하다.

[https://www.python.org/downloads/](https://www.python.org/downloads/)

[Download Python

The official home of the Python Programming Language

www.python.org](https://www.python.org/downloads/)

설치 가능한 운영 체제는 윈도우, 리눅스, 또는 맥OS면 된다. 필요한 시스템 자원은 다음과 같다.

- 시스템 메모리(RAM) 최소 8GB 이상

- 하드디스크 여유 공간 최소 25GB 이상

운영체제별 권장 사양은 다음과 같다.

- **Windows**에서는 NVIDIA 또는 AMD 그래픽 카드를 권장하며, 최소 2GB 이상의 그래픽 메모리(VRAM)가 필요하다.

- **Linux** 역시 NVIDIA 또는 AMD 그래픽 카드를 권장한다. 최소 2GB 이상의 VRAM이 필요하다.

- **Mac**의 경우 Apple Silicon(M1, M2, M3, M4) 칩을 사용하는 모델이 가장 적합하다. 인텔 기반 Mac에서는 AMD 그래픽 카드가 있는 경우에 한해 활용할 수 있다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-002-img1.daumcdn.png]]

그래픽 카드는 NVIDIA 제품을 권장한다. 최소 4GB 이상의 VRAM을 갖춘 모델이면 기본적인 이미지 생성은 무리 없이 가능하다. 물론 VRAM이 클수록 해상도와 생성 속도 면에서 훨씬 여유가 생긴다.

만약 호환 가능한 그래픽 카드가 없다면 CPU 모드로도 실행할 수 있다. 다만 이 경우 생성 속도는 크게 느려진다. GPU 대비 수 배 이상 시간이 걸릴 수 있지만, 기능 자체는 정상적으로 동작한다.

시스템 요구 사항은 비교적 단순하다.

최소 RAM 8GB 이상, 그리고 모델 파일과 캐시를 포함해 20GB 이상의 디스크 공간을 확보하는 것이 좋다. 모델을 여러 개 사용할 계획이라면 더 많은 저장 공간이 필요하다.

추가로 WSL, Docker, Conda 같은 별도의 가상화·패키지 관리 도구는 필수 사항이 아니다. 기본 설치 스크립트가 필요한 구성 요소를 자동으로 처리하므로, 일반적인 Ubuntu 환경이면 바로 설치를 진행할 수 있다.

## 3. Easy Diffusion 설치 (for Window)

Easy Diffusion은 AI를 활용하여 컴퓨터에서 이미지를 만드는 간편한 방법을 제공한다. 별다른 기술 지식이 필요하지 않다. Easy Diffusion은 최고의 오픈 소스 텍스트-이미지 AI 소프트웨어인 Stable Diffusion의 설치 및 사용이 쉬운 배포판이다. 필요한 모든 소프트웨어 구성 요소와 사용자 친화적이고 강력한 웹 인터페이스를 무료로 제공한다.

**시스템 요구사항**

- **운영체제**: Windows 10/11 (64bit)

- **GPU**: NVIDIA GPU 권장 (최소 4GB VRAM, 6GB 이상 권장)

- **드라이버**: 최신 NVIDIA 드라이버 설치 (CUDA 포함)

- **Python**: 따로 설치할 필요 없음 (Easy Diffusion이 자체 포함)

[https://easydiffusion.github.io/docs/installation/](https://easydiffusion.github.io/docs/installation/)

**Easy-Diffusion-Windows.zip 다운로드**

![[03 Attachments/티스토리 Vento AI Lab/808/808-003-img1.daumcdn.png]]

다운로드한 설치 파일을 관리자 권한으로 실행한다.

한참을 설치하는데 용량이 10GB를 넘으니 저장 공간이 충분한 드라이브를 지정한다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-004-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-005-img.png]]

## 4. Easy Diffusion 실행

Easy Diffusion이 설치된 폴더에 있는 "Start Stable Diffusion UI.cmd" 파일을 실행한다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-006-img1.daumcdn.png]]

Easy Diffusion을 실행하면 Github에서 코드를 내려받고, 프로그램을 실행하기 위한 여러가지 파일을 내려받는다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-007-img1.daumcdn.png]]

우측 상단에 녹색으로 "● Stable Diffusion is ready"가 보이면 이제 사용할 수 있다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-008-img1.daumcdn.png]]

## 5. 이미지 생성

Easy Diffusion가 성공적으로 실행하면 브라우저에서 접속하여 이미지를 생성해 본다.

주소 : [http://localhost:9000/](http://localhost:9000/)

![[03 Attachments/티스토리 Vento AI Lab/808/808-009-img1.daumcdn.png]]

Enter Prompt에 프롬프트를 입력한 뒤 "Make Image"버튼을 클릭한다.

**석양을 바라보고 있는 아름다운 여성의 뒷모습**

**The back of a beautiful woman looking at the sunset**

![[03 Attachments/티스토리 Vento AI Lab/808/808-010-img1.daumcdn.png]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-011-img1.daumcdn.png]]

****

입력한 텍스트로 이미지가 생성되었다.

생성된 이미지와 유사한 이미지를 다시 생성해 보자.

이미지에 마우스를 올리면 다양한 기능을 실행할 수 있다.

유사한 이미지를 생성하기 위해 "Make Similar Images"를 클릭한다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-012-img1.daumcdn.png]]

유사한 이미지를 생성하고 있다. 배치로 5장의 이미지를 생성한다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-013-img1.daumcdn.png]]

결과가 썩 마음에 들지는 않지만, 처름 생성한 이미지와 비교해서 헤어스타일이나 자세가 조금씩 다르게 만들어졌다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-014-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-015-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-016-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-017-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-018-img.jpg]]

## 6. 이미지 설정값 변경

Enter Prompt에 ", wearing a hat, holding bag"를 추가했다.

Enter Prompt : The back of a beautiful woman looking at the sunset, wearing a hat, holding bag.

다음과 같이 이미지 설정(Image Settings) 값을 변경하여 이미지를 생성한다. 나름 괜찮은 이미지가 생성되었다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-019-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-020-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-021-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-022-img.jpg]]

## 7. 모델 변경 및 LoRA 적용

인터넷에서 다운로드한 "chilloutmix_NiPrunedFp32Fix" 모델 파일을 아래의 경로에 옮기고서 Easy Diffution을 재시작 했다.

경로 \EasyDiffusion\models\stable-diffusion

![[03 Attachments/티스토리 Vento AI Lab/808/808-023-img1.daumcdn.png]]

**▣ Enter Prompt**

(pureerosface_v1:1), 8k, raw photo, (masterpiece), (best quality), highres, (realistic, photo-realistic:1.4),ultra detailed, physically-based rendering, detailed beautiful eyes and detailed face, 25 years old gorgeous beautiful cute Korean woman, a female college student studying hard in the study room

**▣ Negative Prompt**

ng_deepnegative_v1_75t, badhandv4, nsfw, (worst quality, low quality:1.3), (depth of field, blurry:1.2), (greyscale, monochrome:1.1), 2d, 3d, cropped, lowres, text, jpeg artifacts, signature, watermark, username, blurry, artist name, trademark, watermark, title, (tan, muscular, loli, petite, child, infant, toddlers, chibi, sd character:1.1), multiple view, lace, Reference sheet, (worst quality, low quality, normal quality:1.4), (bad_prompt, bad_prompt_version2:0.8), (mature, comic, cartoon:0.5), bad anatomy, low quality anatomy, bad hands, bad nails, bad legs, bad fingers, extra digit, extar hands, extra fingers, extra arms, extra legs, fewer digit, nail polish, lowres low quality face, lowres low quality eyes, cropped hands, cropped legs, cropped arms, cropped fingers, fused fingers, too many fingers, tattoo, missing fingers, ugly, text, (thai, thai girl, thai style, thai face, thai makeup), (chinese girl, chinese, chinese style, chinese face, chinese makeup), (muscular:0.4), collage, more than one person in focus, bad anatomy, (more than two arm per body:1.5), (more than two leg per body:1.4), (more than five fingers on one hand:1.4), multi arms, bad finger anatomy, unclear architectural outline, non-linear background, elf-ears, hair crosses the screen border, obesity, fat, lowres, worst quality, low quality, blurry, mutated hands and fingers, disfigured, fused, pencil, pink, flag, small breast, medium breast

![[03 Attachments/티스토리 Vento AI Lab/808/808-024-img1.daumcdn.png]]

**▣ Image Settings**

![[03 Attachments/티스토리 Vento AI Lab/808/808-025-img1.daumcdn.png]]

****

**▣ 생성된 이미지**

![[03 Attachments/티스토리 Vento AI Lab/808/808-026-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-027-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-028-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-029-img.jpg]]

생성된 이미지 중에 왼쪽이 분위기가 괜찮아서 왼쪽 이미지로 유사한 이미지를 생성해 본다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-030-img1.daumcdn.png]]

Easy Diffution을 이용해서 빠르고 쉽게 이미지를 생성해 보았다.

![[03 Attachments/티스토리 Vento AI Lab/808/808-031-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-032-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-033-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-034-img.jpg]]

![[03 Attachments/티스토리 Vento AI Lab/808/808-035-주한길.png]]
