---
title: Easy Diffusion - AI 이미지 생성으로 모델 비교 분석
type: blog-archive
status: active
created: '2026-05-09'
updated: '2026-08-16'
published: '2026-05-09T11:32:08+09:00'
source: https://agapeuni.tistory.com/810
source_blog: agapeuni.tistory.com
post_id: 810
category: 🎨 이미지 생성 AI/Easy Diffusion
tags:
- AI이미지생성모델가이드
- EasyDiffusion모델비교
- EasyDiffusion모델추천
- EasyDiffusion프롬프트설정
- FastNegativeV2활용법
- StableDiffusion네거티브프롬프트
- StableDiffusion모델비교
- StableDiffusion인물모델추천
- 실사이미지생성모델
- 애니이미지생성모델
body_hash: 1f8c4c2489e9de0f2cc04799510928a49a09fedf45aa3ea0cb80ff86ef4519b9
visibility: private
rag: exclude
---

# Easy Diffusion - AI 이미지 생성으로 모델 비교 분석

- 원문: https://agapeuni.tistory.com/810
- 게시일: 2026-05-09T11:32:08+09:00
- 분류: 🎨 이미지 생성 AI/Easy Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/810/810-001-img1.daumcdn.png]]

각각의 모델 특성을 확인하기 위해 Prompt는 동일하게 입력했고 Nagative Prompt도 간단하게 입력하고 이미지를 생성했다.

- 사용 도구 : Easy Diffusion v3.0.9

- 프로세서 : Intel(R) Xeon(R) Silver 4314 CPU @ 2.40GHz

- 그래픽 카드 : Tesla T4 (cuda:0) (15.6 Gb total), Tesla T4 (cuda:1) (15.6 Gb total)

- **프롬프트 :****8k, (best quality, masterpiece, colorful, dynamic angle, highest detailed), upper body photo, fashion photography of flirting golden bobbed hair girl, detailed green eyes, dressing high detailed white suit (high resolution textures), in dynamic pose, bokeh, (intricate details, hyperdetailed:1.15), detailed, sunlight passing through hair, colorful splash art background, (high contrast, extreme detailed, highest detailed)**

- 이미지 설정값 :

![[03 Attachments/티스토리 Vento AI Lab/810/810-002-img1.daumcdn.png]]

## absolutereality_v181 모델

이 모델은 사실적인 이미지 생성에 중점을 둔 AI 모델이다. 인물과 배경의 세부 묘사가 뛰어나고, 사진 같은 사실적인 표현이 가능하다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-003-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-004-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-005-img.png]]

### 네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-006-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-007-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-008-img.png]]

## aniverse_V11Pruned 모델

모델의 이름은 애니메이션(Animation)과 유니버스(Universe)라는 두 단어의 합성어다. 애니메이션 스타일의 이미지를 생성하는 모델로, 만화나 게임 캐릭터와 같은 시각적으로 강렬한 이미지를 만들기 위해 최적화되었다. 프루닝을 통해 모델의 크기와 성능을 조정했다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-009-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-010-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-011-img.png]]

###  네거티브 : F astNegativeV2, b&w, black&white, sepia, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-012-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-013-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-014-img.png]]

## braBeautifulRealistic_brav5 모델

아시아 여성의 사실적인 이미지를 생성하는 데 특화된 모델로, 3개월간 훈련된 대규모 데이터셋을 사용해 사실적이고 고해상도의 이미지를 만든다. 머리 색깔, 의상 등 구체적인 특징을 설명하는 프롬프트를 통해 이미지를 생성한다.

### 네거티브 : ( low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-015-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-016-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-017-img.png]]

### 네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-018-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-019-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-020-img.png]]

## chilloutmix_NiPrunedFp32Fix 모델

사진 스타일의 사실적인 이미지를 생성하는 데 최적화되어 있는 모델로 많은 사람들이 사용하고 있는 모델이다. 사실적인 이미지 생성에 특화된 모델로, 인물 묘사가 뛰어나며 특히 여성 캐릭터 이미지를 생성하는 데 탁월하다. 불필요한 부분을 제거해 성능을 높였다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-021-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-022-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-023-img.png]]

###  네거티브 : FastNe gativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-024-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-025-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-026-img.png]]

## cuteyukimixAdorable_neochapter2 모델

귀여운 애니메이션 스타일의 이미지를 생성하는 데 최적화된 모델로, 밝고 생동감 있는 캐릭터와 배경을 표현하는 데 강점을 가지고 있다. 세밀한 캐릭터와 매력적인 시각 요소를 강조하며, 활기차고 밝은 색상의 소녀 캐릭터 이미지를 만드는 데 탁월하다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-027-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-028-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-029-img.png]]

###  네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-030-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-031-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-032-img.png]]

## majicmixRealistic_v7 모델

방대한 이미지 데이터셋을 통해 다양한 이미지 표현을 생성하며, 예술, 게임, 디자인, 건축 등 여러 분야에서 시각화 및 창의적인 프로젝트에 유용하게 사용된다. 사실적이면서도 반-현실적인 이미지를 생성할 수 있는 모델이다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-033-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-034-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-035-img.png]]

###  네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-036-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-037-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-038-img.png]]

## perfectWorld_perfectWorldBakedVAE 모델

현실적인 이미지와 반-현실적이고 매우 정교한 이미지를 모두 생성할 수 있다. 얼굴이나 인물 표현에 강점을 가지며, 주로 창작 및 학습 목적으로만 사용하도록 권장된다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-039-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-040-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-041-img.png]]

**네거티브 : FastNegativeV2, (low quality:1)**

![[03 Attachments/티스토리 Vento AI Lab/810/810-042-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-043-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-044-img.png]]

## realcartoon3d_v17 모델

애니메이션 스타일, 만화, 디지털 아트 및 사실적인 3D 이미지를 생성을 모두 지원한다. 사실적인 스타일과 더불어 만화적인 요소도 잘 구현한다. 이 모델은 세밀한 튜닝을 거쳐 캐릭터 디자인과 디테일한 환경 묘사에 강점을 가지고 있다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-045-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-046-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-047-img.png]]

###  네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-048-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-049-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-050-img.png]]

## xxmix9realistic_v30 모델

사진과 같은 현실적인 이미지를 생성한다. 이 모델은 손과 같은 복잡한 부분을 개선하여 이전보다 향상된 결과를 제공한다. 주로 사진과 같은 고해상도 인물 이미지를 생성하는 데 강점을 가지고 있다.

### 네거티브 : (low quality:1 )

![[03 Attachments/티스토리 Vento AI Lab/810/810-051-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-052-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-053-img.png]]

### 네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-054-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-055-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-056-img.png]]

## zemihr_v2 모델

애니메이션 스타일과 사실적인 이미지 생성을 모두 아우르는 모델로, 캐릭터 표현에서 높은 수준의 디테일을 제공한다. 반실사 스타일의 이미지를 제작하는 데 유용하며 높은 품질의 여성 캐릭터 이미지를 생성하기에 적합하다.

### 네거티브 : (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-057-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-058-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-059-img.png]]

###  네거티브 : FastNegativeV2, (low quality:1)

![[03 Attachments/티스토리 Vento AI Lab/810/810-060-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-061-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-062-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/810/810-063-주한길.png]]
