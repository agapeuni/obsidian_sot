# CLAUDE.md — Obsidian Vault (G:\Obsidian)

이 볼트는 김승구의 **Single Source of Truth(SSOT)** 다. Claude Code가 이 저장소 안에서 작업할 때 이 문서의 규칙을 따른다. 작업 절차(수집→분류→정제→연결→검증→커밋)는 [PROCESS.md](PROCESS.md)를 따른다.

우선순위: **볼트 데이터 보존 > 기존 체계와의 정합성 > 기능 > 편의성**

모든 보고·문서·커밋 메시지는 한국어로 작성한다.

## 정본 문서 체계

규칙이 이 문서와 충돌하면 아래 볼트 내 정본을 따르고 사용자에게 알린다.

| 문서 | 역할 |
|---|---|
| `01 Dashboard\Vault 구조 및 운영 가이드.md` | 폴더 구조·프론트매터 규격·Inbox/Archive 처리의 **정본** |
| `01 Dashboard\Home.md` | 볼트 전체 진입점, 영역 MOC 인덱스 |
| `01 Dashboard\Vault 데이터 현황.md` | 데이터 구성·품질 점검 결과 (점검 후 갱신 대상) |
| `01 Dashboard\Vault 태그 사전.md` | 태그 표준 계층. 새 태그 생성 전 필수 확인 |
| `60 자동화·Agent\OpenClaw Obsidian 변경 정책.md` | 자동 변경의 등급·검증·중단 기준 (Claude Code에도 준용) |

## 볼트 구조 요약

약 4,900개 Markdown 노트. 폴더는 큰 영역만 구분하고 세부 관계는 `[[링크]]`·태그·Properties로 표현한다.

- `00 Inbox` 분류 전 자료 / `01 Dashboard` MOC·운영 현황 / `02 Templates` 템플릿 / `03 Attachments` 첨부
- `10 신앙·성경` `20 생활·가족` `30 지식·학습` `31 독서·서평` `32 블로그` `33 스레드`
- `40 코딩·인프라` `50 개인·과제` `60 자동화·Agent` `65 생성·창작` `70 업무·프로젝트` `80 사업·전략` `90 재무·투자`
- `99 Archive` 완료·중단·비활성 보존 / `Excalidraw` 사용자 생성 자료 (구조 밖, 보존)

영역 경계가 애매할 때: 자동화 일반 설계·연구 → `60` / 회사 업무 자동화 프로젝트 → `70` / 개인 목표·과제 → `50` / 코드·서버 구현 세부 → `40`. 분류가 확실하지 않으면 `00 Inbox`에 만든다.

## 프론트매터 규격

재사용 산출물(설계·문제해결·결정·기록)에만 붙인다. 일반 메모에는 붙이지 않는다. 루트의 저장소 문서(`README.md`, `CLAUDE.md`, `PROCESS.md`)는 적용 제외.

```yaml
---
title:
type: note        # note / project / meeting / book / experiment / content / reference (+ guide, policy, dashboard, moc 등 기존 사용 값)
status: active    # inbox / active / review / done / archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: []          # 태그 사전의 표준 계층 우선 (area/ ai/ dev/ knowledge/ vault/ source/)
aliases: []
source:           # 원본 추적 식별자 — 임의 변경 금지
project:
visibility: private   # private / company-confidential / public
rag: include          # include / exclude — 판단이 서지 않으면 exclude
---
```

- 기존 노트 수정 시 `updated`만 오늘 날짜로 갱신하고 `created`·기존 프론트매터는 보존한다.
- 개인·가족·재무 → `private` + `rag: exclude` / 회사 업무·기밀 → `company-confidential` + `rag: exclude` / 일반 지식·기술 → `private` + `rag: include`.
- `source`, `body_hash`, manifest는 수집 자동화의 추적 계약이므로 임의로 바꾸지 않는다.

## 안전 규칙 (필수)

1. **수정 전 반드시 읽는다.** 같은 주제의 기존 노트를 `-Recurse`로 검색한 후, 새 노트 생성보다 기존 노트 갱신을 우선한다.
2. 기존 노트는 전체 교체가 아니라 필요한 부분만 수정한다.
3. **대량 이동·이름 변경·삭제는 사용자 승인 없이 하지 않는다.** 볼트 내 삭제는 단 1개라도 이유를 명시하고 승인 받는다.
4. `.obsidian\` 폴더는 수정하지 않는다.
5. 폴더 구조·분류 체계를 임의로 만들지 않는다. 새 분류가 필요하면 먼저 제안한다.
6. 파일 쓰기는 **UTF-8**을 보장한다 (`Set-Content -Encoding utf8`). 수정 후 한글 깨짐을 확인한다.
7. 노트 이동·이름 변경은 가능하면 Obsidian 안에서 한다 (내부 링크 자동 갱신).
8. 이 볼트는 **Obsidian Sync로 실시간 동기화**된다. 잘못된 변경은 되돌리기 전에 이미 다른 기기로 퍼진다고 가정한다. 충돌 파일(`sync-conflict` 등)은 삭제하지 말고 보고한다.
9. 원본 아카이브(블로그·성경·수집 자료)는 보존하고, 해석·요약·연결은 별도 지식 노트에서 한다.
10. 새 노트를 만들면 해당 영역 MOC나 관련 문서에서 `[[링크]]`로 연결한다. 고아 노트를 남기지 않는다.

## 승인 필요 vs 자율 수행

| 승인 필요 | 자율 수행 |
|---|---|
| 볼트 내 삭제·이동·이름 변경 | 검색·읽기, 새 노트 작성, 기존 노트 보강 |
| 폴더 구조·분류 체계 변경 | 로컬 `git add` / `git commit` (한국어 메시지) |
| `git push`, 원격 변경 | 백업 생성 |
| 공개 범위(`visibility`/`rag`) 일괄 변경 | Inbox 노트 신규 생성 |

## 보안

- API Key·토큰·비밀번호를 노트·커밋에 남기지 않는다. 노트에서 secret을 발견하면 삭제하지 말고 보고한다.
- `visibility: company-confidential` 문서는 외부 전송·게시·RAG 포함 대상에서 제외한다.
- 이 저장소는 비공개다. 공개 전환 전 민감정보·공개 범위 전수 점검이 필요하다.
