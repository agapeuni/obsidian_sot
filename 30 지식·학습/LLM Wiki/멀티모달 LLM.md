---
title: 멀티모달 LLM
type: concept
status: verified
created: 2026-08-18
updated: 2026-08-18
tags:
  - ai/llm
  - ai/multimodal
source_checked: 2026-08-18
visibility: private
rag: include
---

# 멀티모달 LLM

멀티모달 LLM은 텍스트와 이미지·음성·영상 등 둘 이상의 입력 또는 출력 양식을 함께 처리하는 모델과 애플리케이션 구조를 뜻한다.

## 설계 질문

- 어떤 modality를 입력·출력으로 지원해야 하는가?
- OCR, ASR, vision encoder 같은 전처리 결과를 어떻게 추적할 것인가?
- 원본 파일과 추출 텍스트 중 무엇을 근거로 보존할 것인가?
- 이미지·음성에 포함된 개인정보와 공격성 콘텐츠를 어떻게 통제할 것인가?
- modality별 품질과 비용·지연시간을 어떻게 평가할 것인가?

## 적용 사례

- 문서·도면·화면 이미지 질의응답
- 회의 음성 전사와 실행 항목 추출
- 제품 이미지 검사와 설명 생성
- 영상 장면 검색과 요약

## 실패 패턴

- OCR이나 전사 오류를 모델 추론 오류와 구분하지 않는다.
- 이미지에 숨은 지시문을 신뢰해 간접 프롬프트 인젝션이 발생한다.
- 해상도·프레임 샘플링·오디오 구간이 평가마다 달라 재현되지 않는다.
- 텍스트 벤치마크만으로 멀티모달 품질을 판단한다.

## 검증 기준

- modality별 입력 성공률과 전처리 오류율
- 근거 영역·시간 구간 인용 정확성
- 개인정보·유해 콘텐츠 탐지와 차단 성능
- 파일당 처리 시간·토큰·비용

## 출처

- [Learning Transferable Visual Models From Natural Language Supervision](https://arxiv.org/abs/2103.00020)
- [Flamingo: a Visual Language Model for Few-Shot Learning](https://arxiv.org/abs/2204.14198)

## 관련

- [[LLM 애플리케이션 아키텍처]]
- [[LLM 평가]]
- [[LLM 보안]]
