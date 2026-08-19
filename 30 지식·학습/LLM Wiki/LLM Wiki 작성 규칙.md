---
title: LLM Wiki 작성 규칙
type: guideline
status: active
created: 2026-08-15
updated: 2026-08-18
tags:
  - ai/llm
  - knowledge/management
visibility: private
rag: include
source_checked: 2026-08-18
---

# LLM Wiki 작성 규칙

## 노트 유형

- `concept`: 변하지 않는 핵심 개념
- `model`: 특정 모델·모델군
- `pattern`: RAG, Agent 같은 설계 패턴
- `experiment`: 가설과 측정 결과가 있는 실험
- `tool`: 프레임워크와 도구
- `paper`: 논문 요약과 재현 메모
- `decision`: 선택과 근거
- `operations`: 배포와 운영 절차
- `architecture`: 시스템 구조와 계층별 책임
- `security`: 위협 모델과 통제 기준
- `methodology`: 평가·분석 방법론
- `roadmap`: 단계별 학습·도입 경로
- `glossary`: 공통 용어와 정의
- `moc`: 주제별 탐색 허브
- `guideline`: 작성·검증·운영 규칙

## 필수 메타데이터

```yaml
title:
type:
status: seed | active | verified | deprecated
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
source_checked:
visibility: private
rag: include
```

`source_checked`는 마지막으로 핵심 출처와 사실을 확인한 날짜다. 출처가 없는 개인 판단 노트도 검토일을 기록하고, 본문에 판단 근거를 구분해 남긴다.

## 본문 원칙

- 한 노트는 하나의 핵심 질문에 답한다.
- 정의 다음에 적용 조건, 한계, 실패 사례를 쓴다.
- 모델·가격·벤치마크처럼 변하는 정보는 확인 날짜와 출처를 남긴다.
- 실험은 환경, 입력, 파라미터, 결과, 실패, 재현 절차를 기록한다.
- 최소 2개의 관련 노트와 연결한다.
- 회사 기밀·개인정보·인증정보는 일반 지식 노트에 넣지 않는다.

## 상태 기준

- `seed`: 제목과 질문만 있는 초기 노트
- `active`: 기본 내용과 연결이 있는 작업 노트
- `verified`: 출처·실험·검토가 완료된 노트
- `deprecated`: 더 이상 권장하지 않으며 대체 노트가 있는 상태

## 품질 점검

- [ ] 제목이 검색어로 자연스러운가?
- [ ] 핵심 정의를 첫 문단에서 알 수 있는가?
- [ ] 적용 조건과 한계가 있는가?
- [ ] 최신 정보에 날짜와 출처가 있는가?
- [ ] 관련 노트 링크가 있는가?
- [ ] RAG에 포함해도 안전한가?

## 관련

- [[LLM Wiki]]
- [[템플릿 - LLM 개념]]
- [[템플릿 - LLM 실험]]
- [[Vault 태그 사전]]
