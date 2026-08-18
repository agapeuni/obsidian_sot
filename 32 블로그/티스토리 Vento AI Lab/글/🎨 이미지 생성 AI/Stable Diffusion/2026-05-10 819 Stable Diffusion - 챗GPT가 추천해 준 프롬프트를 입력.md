---
title: Stable Diffusion - 챗GPT가 추천해 준 프롬프트를 입력
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T21:02:27+09:00'
source: https://agapeuni.tistory.com/819
source_blog: agapeuni.tistory.com
post_id: 819
category: 🎨 이미지 생성 AI/Stable Diffusion
tags:
- AI이미지생성실험
- CFGScale조절방법
- DenoisingStrength설정법
- StableDiffusion사용법
- StableDiffusion설정가이드
- StableDiffusion파라미터비교
- StableDiffusion프롬프트예시
- 그림판그림AI변환
- 이미지투이미지활용법
- 하늘을나는사람이미지생성
body_hash: 731663e0cbeb142f0a6c96505a2ddcb7c3f2aa22b8d2933e40f29c6ca829d9a6
visibility: private
rag: exclude
---

# Stable Diffusion - 챗GPT가 추천해 준 프롬프트를 입력

- 원문: https://agapeuni.tistory.com/819
- 게시일: 2026-05-10T21:02:27+09:00
- 분류: 🎨 이미지 생성 AI/Stable Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/819/819-001-img1.daumcdn.png]]

Stable Diffusion의 설정값은 아래의 그림처럼 Sampling steps 25, 이미지 크기는 512x512, CFG Scale은 6으로 설정했다. Negative 프롬프트는 아래와 같이 고정하고 ChatGPT가 추천한 프롬프트만 변경하면서 입력하여 이미지를 생성해 본다.

ng_deepnegative_v1_75t, paintings, sketches, (worst quality:2), (low quality:2), (normal quality:2), lowres, fewer digits, normal quality, ((monochrome)), ((grayscale)), ugly, skin spots, acnes, skin blemishes, age spot, ((wrong feet)),(wrong shoes), bad feet, distorted, blurry, bad anatomy, bad hands, missing fingers, multiple feet, bad knees, extra fingers, signature, watermark, username, blurry, artist name, trademark, watermark, title, letters, loli, childish, multiple eyeblows, missing_body

ChatGPT에게 Stable Diffusion으로 만들 수 있는 "인공지능"관련 이미지 프롬프트를 추천해 달라고 했더니 5개를 추천해 주었다. 추천한 텍스트를 바로 입력해서 이미지를 생성해 보았다.

## 추천 1.

인공지능을 핵심으로 한 미래형 도시 경관으로, 날렵하고 반사적인 표면을 가진 우뚝 솟은 건물과 자율주행차와 로봇으로 가득 찬 번화한 거리가 특징이다. 네온 불빛과 홀로그래픽 디스플레이의 광채는 또 다른 세계적인 분위기를 자아내는 반면, 도시에 동력을 공급하는 첨단 AI 시스템은 겉보기에는 어디에나 있지만 보이지 않는 배경에서 조용히 웅성거린다. 이 이미지는 생생한 색감과 복잡한 디테일로 사실적인 스타일로 묘사될 수도 있고, 첨단 대도시에 몰입한 느낌을 강조하는 보다 추상적이고 인상적인 스타일로 묘사될 수도 있다.

A futuristic cityscape with artificial intelligence at its core, it features towering buildings with sleek, reflective surfaces, and busy streets filled with self-driving cars and robots. The glow of neon lights and holographic displays creates another global atmosphere, while the advanced AI systems that power the city quietly hum in a seemingly ubiquitous but invisible background. The image can be depicted in a realistic style with vivid colors and intricate details, or in a more abstract and impressive style that emphasizes the feeling of immersion in a high-tech metropolis.

![[03 Attachments/티스토리 Vento AI Lab/819/819-002-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/819/819-003-img.png]]

## 추천 2.

복잡한 세부 기능과 사실적이고 실제와 같은 외관을 가진 안드로이드의 클로즈업 초상화입니다. 안드로이드는 금속 피부와 빛나는 눈의 모든 미묘한 디테일을 포착하는 사실적인 그림부터, 날렵하고 미래적인 디자인을 강조하는 좀 더 양식화된 일러스트까지 다양한 스타일로 묘사될 수 있다. 이 이미지는 또한 첨단 기계와 장비로 가득 찬 실험실과 같이 안드로이드를 가능하게 한 기술적 진보를 강조하는 배경을 특징으로 할 수 있다.

It is a close-up portrait of Android with intricate details and a realistic, lifelike appearance. Android can be depicted in a variety of styles, from realistic drawings that capture every subtle detail of metal skin and glowing eyes to more stylized illustrations that emphasize sleeker, futuristic designs. The image can also feature a background that highlights the technological advances that made Android possible, such as a laboratory full of advanced machinery and equipment.

![[03 Attachments/티스토리 Vento AI Lab/819/819-004-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/819/819-005-img.png]]

## 추천 3.

자연과 기술 사이의 경계를 흐리게 하는 초현실적인 풍경으로, 에너지로 맥박이 뛰고 그들만의 마음을 가진 것처럼 보이는 빛나는 생물 발광 나무들의 숲을 특징으로 합니다. 그 이미지는 섬뜩하고 몽환적인 분위기의 모든 뉘앙스를 포착하는 매우 상세한 사실주의 그림에서부터 빛과 그림자의 상호작용에 초점을 맞춘 더 인상주의적인 해석에 이르기까지 다양한 스타일로 만들어질 수 있었다. 이 이미지는 부드럽고 따뜻한 빛을 방출하는 떠다니는 타원형과 같이 자연환경에 매끄럽게 짜인 미래 기술의 힌트를 특징으로 할 수 있다.

A surreal landscape that blurs the line between nature and technology, it features a forest of glowing bioluminescent trees that pulsate with energy and seem to have their own minds. The image could be created in a variety of styles, from highly detailed realist paintings that capture all the nuances of an eerie and dreamlike atmosphere, to more impressionistic interpretations that focus on the interaction of light and shadow. This image could feature hints of future technologies that are seamlessly woven into the natural environment, such as floating ovals that emit soft and warm light.

![[03 Attachments/티스토리 Vento AI Lab/819/819-006-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/819/819-007-img.png]]

## 추천 4.

인공지능의 윤리적 함의를 탐구하는 개념적 작품으로, 기계가 지나치게 지능화될 때 발생할 수 있는 고립과 이탈을 강조하는 극명하고 미니멀리즘적인 장면이 특징이다. 이미지는 기계와 환경의 극명한 대조를 강조하는 흑백 사진부터 대담한 모양과 색상을 사용하여 긴장감과 불안감을 만들어내는 보다 추상적이고 실험적인 스타일까지 다양한 스타일로 만들어질 수 있었다.

It is a conceptual work that explores the ethical implications of artificial intelligence, featuring stark and minimalistic scenes that emphasize the isolation and disengagement that can occur when machines become overly intelligent. Images could be created in a variety of styles, from black and white photographs emphasizing the stark contrast between machines and their environment to more abstract and experimental styles that use bold shapes and colors to create tension and anxiety.

![[03 Attachments/티스토리 Vento AI Lab/819/819-008-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/819/819-009-img.png]]

## 추천 5.

인간과 친근하고 접근하기 쉬운 방식으로 상호 작용하도록 설계된 매력적이고 변덕스러운 로봇을 특징으로 하는 장난스럽고 가벼운 인공 지능 묘사. 이미지는 로봇의 친근한 태도와 만화 같은 모습을 강조하는 밝고 화려한 그림부터 금속 몸체와 표현력 있는 얼굴의 복잡한 디테일을 포착한 보다 사실적인 사진까지 다양한 스타일로 만들어질 수 있었다. 이 이미지는 또한 로봇이 아이들이나 애완동물과 상호작용하거나 인간 동료들을 즐겁게 하기 위해 우스꽝스러운 춤을 추는 것과 같은 다양한 장난스러운 요소들을 특징으로 할 수 있다.

A playful and lightweight artificial intelligence depiction featuring attractive and fickle robots designed to interact with humans in a friendly and accessible way. Images could be made in a variety of styles, from bright and colorful drawings that highlight the robot's friendly attitude and cartoonish appearance to more realistic pictures that capture the intricate details of a metal body and expressive face. The image can also feature various playful elements, such as the robot interacting with children or pets or performing a silly dance to entertain its human colleagues.

![[03 Attachments/티스토리 Vento AI Lab/819/819-010-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/819/819-011-img.png]]

 인공지능끼리 서로 통하는 것일까? 생각보다 결과물의 품질이 좋다.

추천해 준 프롬프트로 입력했더니 완전히 새로운 분위기로 이미지가 생성되었다.

![[03 Attachments/티스토리 Vento AI Lab/819/819-012-주한길.png]]
