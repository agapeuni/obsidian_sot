---
title: Stable Diffusion - 챗GTP를 활용해 한편의 그림동화를 쉽게 생성
type: blog-archive
status: active
created: '2026-05-10'
updated: '2026-08-16'
published: '2026-05-10T21:11:19+09:00'
source: https://agapeuni.tistory.com/823
source_blog: agapeuni.tistory.com
post_id: 823
category: 🎨 이미지 생성 AI/Stable Diffusion
tags:
- AI그림동화만드는법
- AI동화이미지프롬프트
- AI동화제작방법
- AI창작자동화가이드
- ChatGPTStableDiffusion활용
- ChatGPT동화만들기
- StableDiffusion동화그림생성
- StableDiffusion프롬프트활용
- 생성형AI콘텐츠제작
- 인공지능동화창작가이드
body_hash: 478bbecfc23fd8dc43f196a0ec5bed89748935e1b69de48135bda990b82346c0
visibility: private
rag: exclude
---

# Stable Diffusion - 챗GTP를 활용해 한편의 그림동화를 쉽게 생성

- 원문: https://agapeuni.tistory.com/823
- 게시일: 2026-05-10T21:11:19+09:00
- 분류: 🎨 이미지 생성 AI/Stable Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/823/823-001-img1.daumcdn.png]]

## 1. 동화만들기

먼저 ChatGTP로 동화 이야기를 하나 생성한다. 그리고 생성된 문장으로 Stable Diffusion으로 그림을 생성한다. 한편이 동화 이야기를 만들기 위해 사람이 하는 일은 두 가지를 잘 조합하기만 하면 완성이 된다. 컴퓨터 사양에 따라 걸리는 시간의 차이는 있을 수 있겠지만 한두 시간 정도면 충분하다.

## 2. 스토리 작성 (ChatGPT)

Please make a touching fairy tale story with a girl as the main character.

여자 소녀가 주인공으로 감동적인 동화이야기 하나 만들어줘

ChatGPT에게 요청하여 손쉽게 동화 이야기를 하나 만들었다. 이 동화 이야기를 Stable Diffusion 입력으로 하여, 이야기에 어울리는 이미지를 생성해 동화를 완성해 보자.

| Once upon a time, in a far-off kingdom, there lived a girl named Lily. She was a kind and gentle soul who loved to spend her days tending to the flowers in the royal garden.  One day, while she was working, she heard a soft whimpering sound coming from a nearby bush. Curious, she went over to investigate and found a tiny fairy who had gotten stuck in a thorn bush.  Lily gently freed the fairy and was amazed to see that she was the most beautiful fairy she had ever seen. The fairy was so grateful to Lily that she granted her three wishes.  Lily was overjoyed and thought long and hard about what she wanted to wish for. She decided that her first wish would be to have the ability to speak to animals. Her second wish was to be able to heal the sick and injured. And for her final wish, she wished for a life filled with love and happiness.  The fairy granted all of Lily's wishes, and she became known throughout the kingdom as the girl who could talk to animals and heal the sick. Everyone loved her, and she was always surrounded by friends and family.  One day, while Lily was walking in the forest, she came across a wounded deer. She used her powers to heal the deer and soon found herself face to face with a handsome prince who had been hunting in the forest.  The prince was amazed by Lily's kindness and beauty, and the two of them fell deeply in love. They were married in a grand ceremony, and Lily's life was filled with all the love and happiness she had ever wished for.  Years passed, and Lily became an old woman. On her deathbed, she smiled knowing that she had lived a full and happy life. As she closed her eyes for the final time, she saw the fairy from long ago standing at the foot of her bed. The fairy leaned down and whispered, "You have been a true friend to all creatures, and your kindness will be remembered for generations to come."  And with that, Lily's spirit was lifted up to the heavens, where she joined the ranks of the great angels and lived on forever as a symbol of love and kindness. |
| --- |

## 3. 그림 생성 (Stable Diffusion)

ChatGTP가 생성한 영문을 그대로 Stable Diffusion의 Prompt 값으로 입력했다.

옛날에, 먼 왕국에 릴리라는 이름의 소녀가 살았습니다.

그녀는 왕실 정원의 꽃들을 돌보며 하루하루를 보내는 것을 좋아하는 친절하고 온화한 소녀였습니다.

Once upon a time, in a far-off kingdom, there lived a girl named Lily. She was a kind and gentle soul who loved to spend her days tending to the flowers in the royal garden.

![[03 Attachments/티스토리 Vento AI Lab/823/823-002-img1.daumcdn.png]]

어느 날, 그녀가 일을 하고 있을 때, 그녀는 근처 덤불에서 나는 부드러운 훌쩍이는 소리를 들었습니다.

호기심에 사로잡힌 그녀는 조사하러 갔고 가시덤불에 갇힌 작은 요정을 발견했습니다.

One day, while she was working, she heard a soft whimpering sound coming from a nearby bush. Curious, she went over to investigate and found a tiny fairy who had gotten stuck in a thorn bush.

![[03 Attachments/티스토리 Vento AI Lab/823/823-003-img1.daumcdn.png]]

릴리는 조심스럽게 요정을 풀어주었고 그녀가 지금까지 본 것 중 가장 아름다운 요정이라는 것을 보고 깜짝 놀랐습니다.

요정은 릴리에게 너무 감사해서 그녀의 세 가지 소원을 들어주었습니다.

릴리는 너무 기뻐서 그녀가 무엇을 바라고 싶은지에 대해 오랫동안 그리고 열심히 생각했습니다.

Lily gently freed the fairy and was amazed to see that she was the most beautiful fairy she had ever seen. The fairy was so grateful to Lily that she granted her three wishes.

![[03 Attachments/티스토리 Vento AI Lab/823/823-004-img1.daumcdn.png]]

그녀는 첫 번째 소원은 동물들과 대화할 수 있는 능력을 갖는 것이라고 결심했습니다.

그녀의 두 번째 소원은 아프고 다친 사람들을 치유하는 것이었습니다.

그리고 그녀의 마지막 소원을 위해, 그녀는 사랑과 행복으로 가득 찬 삶을 소원했습니다.

Lily was overjoyed and thought long and hard about what she wanted to wish for. She decided that her first wish would be to have the ability to speak to animals. Her second wish was to be able to heal the sick and injured. And for her final wish, she wished for a life filled with love and happiness.

![[03 Attachments/티스토리 Vento AI Lab/823/823-005-img1.daumcdn.png]]

요정은 릴리의 모든 소원을 들어주었습니다.

그녀는 동물들과 대화하고 아픈 사람들을 치유할 수 있는 소녀로 왕국 전역에 알려지게 되었습니다.

모든 사람들은 그녀를 사랑했고, 그녀는 항상 친구들과 가족들에게 둘러싸여 있었습니다.

The fairy granted all of Lily's wishes, and she became known throughout the kingdom as the girl who could talk to animals and heal the sick. Everyone loved her, and she was always surrounded by friends and family.

![[03 Attachments/티스토리 Vento AI Lab/823/823-006-img1.daumcdn.png]]

어느 날, 릴리가 숲을 걷고 있는 동안, 그녀는 상처 입은 사슴을 우연히 만나게 되었습니다.

그녀는 사슴을 치료하기 위해 그녀의 힘을 사용했고 곧 숲에서 사냥을 하던 잘생긴 왕자와 얼굴을 마주하게 되었습니다.

One day, while Lily was walking in the forest, she came across a wounded deer. She used her powers to heal the deer and soon found herself face to face with a handsome prince who had been hunting in the forest.

![[03 Attachments/티스토리 Vento AI Lab/823/823-007-img1.daumcdn.png]]

왕자는 릴리의 친절함과 아름다움에 놀랐고, 그들 둘은 깊은 사랑에 빠졌습니다.

그들은 성대한 결혼식을 치렀고, 릴리의 삶은 그녀가 바라던 모든 사랑과 행복으로 가득 찼습니다.

The prince was amazed by Lily's kindness and beauty, and the two of them fell deeply in love. They were married in a grand ceremony, and Lily's life was filled with all the love and happiness she had ever wished for.

![[03 Attachments/티스토리 Vento AI Lab/823/823-008-img1.daumcdn.png]]

오랜 시간이 지나고, 릴리는 늙은 할머니가 되었습니다.

임종 때 그녀는 자신이 충만하고 행복한 삶을 살았다는 것을 알고 미소를 지었습니다.

그녀가 마지막으로 눈을 감았을 때, 그녀는 오래전부터 그녀의 침대 발치에 서 있는 요정을 보았습니다.

Years passed, and Lily became an old woman. On her deathbed, she smiled knowing that she had lived a full and happy life. As she closed her eyes for the final time, she saw the fairy from long ago standing at the foot of her bed. The fairy leaned down and whispered, "You have been a true friend to all creatures, and your kindness will be remembered for generations to come."

![[03 Attachments/티스토리 Vento AI Lab/823/823-009-img1.daumcdn.png]]

요정은 몸을 숙이고 속삭였습니다. "당신은 모든 생물에게 진정한 친구였고, 당신의 친절은 대대로 기억될 것입니다." 그리고 그것으로 릴리의 영혼은 하늘로 올라가 위대한 천사들의 대열에 합류했고 사랑과 친절의 상징이 되었습니다.

And with that, Lily's spirit was lifted up to the heavens, where she joined the ranks of the great angels and lived on forever as a symbol of love and kindness.

![[03 Attachments/티스토리 Vento AI Lab/823/823-010-img1.daumcdn.png]]

4. 결론

인공지능으로 동화 이야기를 하나 만들어 보면서 만들어진 결과에 놀라웠다. 생성된 결과를 바로 사용하기는 했지만 시간을 들여 작업을 한다면 보다 좋은 결과물을 인공지능의 도움으로 손쉽게 만들 수 있다. 앞으로 창작과 예술 영역에 커다란 변화가 일어날 거 같다. 앞으로 어떻게 변하게 될지...

![[03 Attachments/티스토리 Vento AI Lab/823/823-011-주한길.png]]
