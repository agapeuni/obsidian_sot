---
title: Vault 태그 사전
type: guideline
status: active
created: 2026-08-18
updated: 2026-08-18
tags:
  - vault/운영
  - knowledge/management
aliases:
  - 태그 사전
visibility: private
rag: include
---

# Vault 태그 사전

태그는 폴더를 반복하는 분류가 아니라, 여러 영역을 가로질러 검색할 속성을 표현한다. 새 태그를 만들기 전에 이 문서의 표준 계층을 우선 사용한다.

## 역할 구분

- 폴더: 자료의 주 소유 영역
- `type`: 문서 형식과 처리 방식
- `status`: 문서의 성숙도와 생명주기
- `tags`: 주제·기술·출처처럼 영역을 가로지르는 속성
- `visibility`: 공개 범위
- `rag`: 검색 증강 생성 포함 여부

## 표준 계층

| 계층 | 용도 | 예시 |
|---|---|---|
| `area/` | 횡단 업무 영역 | `area/automation` |
| `ai/` | AI 기술 주제 | `ai/llm`, `ai/rag`, `ai/agent` |
| `dev/` | 개발 기술 | `dev/python`, `dev/database` |
| `knowledge/` | 지식관리 방식 | `knowledge/management` |
| `vault/` | Vault 운영 | `vault/운영`, `vault/지식연결` |
| `source/` | 수집 출처 | `source/naver-blog` |

기존 대량 수집 태그는 원본 추적을 위해 유지한다. `naver-blog/archive` 같은 기존 태그는 일괄 변경하지 않고, 새 문서부터 표준을 적용한다.

## 작성 규칙

1. 소문자 영문 계층과 한글 주제를 혼용할 수 있지만 같은 의미의 중복 태그는 만들지 않는다.
2. 문서 하나에 핵심 태그 2~5개를 권장한다.
3. 폴더명·`type`·`status`를 태그로 다시 쓰지 않는다.
4. 회사명·사람 이름·프로젝트명은 공개 범위를 확인한 뒤 사용한다.
5. 새 공통 태그가 3개 이상 문서에서 필요할 때 이 사전에 먼저 추가한다.

## 관련

- [[Home]]
- [[LLM Wiki 작성 규칙]]
- [[OpenClaw Obsidian 변경 정책]]
