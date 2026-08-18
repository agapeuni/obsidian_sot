---
title: Stable Diffusion - 그림판에서 그린 그림을 사진으로 변환
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T20:57:49+09:00'
source: https://agapeuni.tistory.com/818
source_blog: agapeuni.tistory.com
post_id: 818
category: 🎨 이미지 생성 AI/Stable Diffusion
tags:
- AI이미지생성실험
- StableDiffusionCFGScale설정
- StableDiffusionDenoisingStrength조절
- StableDiffusionimg2img사용법
- StableDiffusion결과비교가이드
- StableDiffusion그림변환
- StableDiffusion설정값비교
- StableDiffusion프롬프트작성법
- 그림판그림AI변환
- 하늘을나는사람이미지생성
body_hash: e2576cddb73e208d4501b2063956093c503247ab666bc44dc801dc458d7034e0
visibility: private
rag: exclude
---

# Stable Diffusion - 그림판에서 그린 그림을 사진으로 변환

- 원문: https://agapeuni.tistory.com/818
- 게시일: 2026-05-10T20:57:49+09:00
- 분류: 🎨 이미지 생성 AI/Stable Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/818/818-001-img1.daumcdn.png]]

## 그림판에서 가볍게 그 린 그림

그림 실력이 좋지 않지만 윈도에 기본으로 설치되어 있는 그림판에서 "하늘을 나는 사람"의 그림을 그렸다. 먼저 배경에 하늘색을 칠하고 하얀색으로 구름을 그려놓고 가운데 사람을 그려보았다. Stable Diffusion이 어떤 결과물을 만들어 낼지 기대해 본다.

![[03 Attachments/티스토리 Vento AI Lab/818/818-002-img1.daumcdn.png]]

## Stable Diffusion 입력 및 설정

Prompt :

(masterpiece), best quality, ultra high resolution, RAW photo, symmetrical face, balanced face, clear facial features, well-defined eyes, nose, lips, natural skin texture, smooth skin, detailed eyes, looking at camera, stable face, front view, a human flying above the clouds, floating in sky, soft clouds, blue sky, soft sunlight, natural lighting, soft light, cinematic lighting, 35mm photograph, sharp focus, high detail

Nagative Prompt :

worst quality, low quality, blurry, out of focus, distorted face, deformed face, asymmetrical face, bad anatomy, bad hands, extra fingers, missing fingers, 3d, render, CGI, cartoon, anime, overexposed face, shadow on face, face cut, cropped face, noise, grain, watermark, text

CFG Scale 값과 Denoising strength 값을 조절하면서 이미지를 생성했다. CFG Scale 값을 높이면 입력한 프롬프트를 충실하게 따르고 Denoising strength 값을 높이면 AI에게 자유도를 준다. 반대로 CFG Scale 값을 낮추면 입력한 프롬프트를 가볍게 따르고 Denoising strength 값을 낮추면 원본 이미지의 변형을 적게 한다.

## 1. 기준값 (CFG Scale : 7, Denoising strength : 0.7)

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 7

- Denoising strength : 0.7

## 2. CFG Scale : 6

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 6

- Denoising strength : 0.7

![[03 Attachments/티스토리 Vento AI Lab/818/818-003-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-004-img.png]]

3. CFG Scale : 5

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 5

- Denoising strength : 0.7

![[03 Attachments/티스토리 Vento AI Lab/818/818-005-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-006-img.png]]

## 4. CFG Scale : 4

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 4

- Denoising strength : 0.7

![[03 Attachments/티스토리 Vento AI Lab/818/818-007-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-008-img.png]]

## 5. Denoising strength : 0.75

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 7

- Denoising strength : 0.75

![[03 Attachments/티스토리 Vento AI Lab/818/818-009-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-010-img.png]]

## 6. Denoising strength : 0.7

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 7

- Denoising strength : 0.7

![[03 Attachments/티스토리 Vento AI Lab/818/818-011-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-012-img.png]]

## 7. Denoising strength : 0.65

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 7

- Denoising strength : 0.65

민망하지 않은 그림 두개를 골라서 올린다.

![[03 Attachments/티스토리 Vento AI Lab/818/818-013-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-014-img.png]]

## 8. Denoising strength : 0.6

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 7

- Denoising strength : 0.6

![[03 Attachments/티스토리 Vento AI Lab/818/818-015-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-016-img.png]]

## 9. Denoising strength : 0.55

- Sampling method : Euler a

- Sampling steps : 25

- CFG Scale : 7

- Denoising strength : 0.55

![[03 Attachments/티스토리 Vento AI Lab/818/818-017-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-018-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/818/818-019-주한길.png]]
