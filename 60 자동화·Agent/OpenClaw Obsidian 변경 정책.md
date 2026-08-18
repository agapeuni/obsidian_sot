---
title: OpenClaw Obsidian 변경 정책
type: policy
status: active
created: 2026-08-18
updated: 2026-08-18
tags:
  - vault/운영
  - area/automation
aliases:
  - OpenClaw Vault 수정 정책
visibility: private
rag: exclude
---

# OpenClaw Obsidian 변경 정책

OpenClaw가 이 Vault를 Single Source of Truth로 유지하면서 자동 수정할 때 적용하는 안전 기준이다.

## 기본 원칙

1. 읽기·분석은 허용하되, 쓰기는 사용자 요청 범위로 제한한다.
2. 대량 변경 전 Git 상태와 변경 대상을 확인하고 복구 지점을 만든다.
3. `visibility: company-confidential` 문서는 외부 전송·게시·RAG 포함 대상에서 제외한다.
4. API 키·토큰·비밀번호·개인정보는 Markdown에 기록하지 않는다.
5. 원본 아카이브는 보존하고, 해석과 연결은 MOC·개념 노트에서 추가한다.

## 변경 등급

| 등급 | 예시 | 실행 조건 |
|---|---|---|
| 낮음 | 오탈자, 확실한 broken link, 인덱스 링크 추가 | 변경 후 검증과 diff 확인 |
| 중간 | frontmatter 정규화, 파일명 변경, 문서 이동 | 사전 목록·백업·링크 갱신 검증 |
| 높음 | 삭제, 병합, 대량 이동, 공개 범위·RAG 변경 | 사용자 승인과 별도 브랜치 필수 |

## 보호 계약

- `source`: 원본 위치를 추적하는 식별자이므로 임의로 바꾸지 않는다.
- `body_hash`: 수집 재실행 시 중복·변경 판단에 사용하므로 본문 변경과 함께 검증한다.
- manifest: 수집 원본과 생성 문서의 대응 관계를 유지한다.
- 템플릿 placeholder: 생성 시점에 치환되는 값이므로 일괄 정규화에서 제외한다.
- `.obsidian/workspace*.json`, 캐시, 플러그인 `data.json`: 사용자 UI 상태이므로 버전 관리와 자동 편집에서 제외한다.

## 파일 이동과 이름 변경

- 일반 `mv` 대신 Obsidian의 링크 자동 갱신 기능 또는 Obsidian-aware 도구를 사용한다.
- 이동 전후 wikilink, embed, `source` 절대경로, manifest 참조를 검사한다.
- Windows와 WSL 경로 표현을 구분하고 절대경로 변경은 원본 존재 여부까지 검증한다.

## 실행 절차

1. Git 저장소·브랜치·working tree 상태를 확인한다.
2. 대상 파일, 변경 수, 보안 등급을 목록화한다.
3. 작은 표본으로 먼저 실행하고 YAML·링크·첨부를 검사한다.
4. 전체 적용 후 Markdown 수, frontmatter 파싱, broken link, 누락 첨부를 검사한다.
5. diff에서 요청 범위 밖 변경과 민감정보를 확인한다.
6. 의미 단위로 로컬 커밋하고, 외부 push는 사용자 지시가 있을 때만 수행한다.

## 중단 조건

- `.git` 또는 원격 추적 상태가 예상과 다름
- Obsidian과 자동화가 같은 파일을 동시에 수정함
- 회사 기밀 문서가 `rag: include` 또는 외부 전송 대상에 포함됨
- 삭제·병합 대상의 중복 여부가 확정되지 않음
- 변경 후 링크나 첨부 누락이 증가함

## 관련

- [[Home]]
- [[Vault 태그 사전]]
- [[Vault 데이터 현황]]
