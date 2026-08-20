# PROCESS.md — Vault 운영 프로세스

이 볼트(SSOT)에서 자료가 들어와 지식 자산이 되기까지의 표준 절차다. 규칙 자체는 [CLAUDE.md](CLAUDE.md)와 `01 Dashboard\Vault 구조 및 운영 가이드.md`를 따른다.

```text
수집 → 분류 → 정제 → 연결 → 검증 → 커밋 → (승인 시) push
```

## 1. 수집 — Inbox

- 새 자료·임시 메모·AI Agent 작성물은 분류가 확실하지 않으면 모두 `00 Inbox`에 만든다.
- 생성 시점에 제목, 출처(`source`), 작성일과 최소 프론트매터(`status: inbox`)를 기록한다.
- 외부(내담 서버 등)에서 온 문서는 볼트 규격으로 변환한다: 한글 키(`분류`/`유형`/`상태`) → `type`/`status`/`tags`, 인코딩 UTF-8 확인.

## 2. 분류 — 영역 배치

- 검토 후 가장 적합한 영역 폴더로 옮긴다. **이동은 Obsidian 안에서** 하여 내부 링크가 함께 갱신되게 한다.
- 영역 경계 판단: 자동화 일반 설계·연구 → `60` / 회사 업무 자동화 → `70` / 개인 목표·과제 → `50` / 코드·서버 구현 → `40`.
- 중복 자료는 즉시 삭제하지 않고 원본과의 관계를 먼저 확인한다.
- 하위 폴더는 자료가 실제로 누적되어 필요성이 확인될 때만 추가한다.

## 3. 정제 — 규격화

- 파일명: 사람이 이해할 수 있는 구체적 제목. 날짜가 핵심인 문서만 `YYYY-MM-DD 제목.md`. 구분자는 공백.
- 프론트매터: `status`를 `inbox` → `active`로 올리고 `visibility`·`rag`를 확정한다. 판단이 서지 않으면 `rag: exclude`.
- 태그: `Vault 태그 사전`의 표준 계층(`area/` `ai/` `dev/` `knowledge/` `vault/` `source/`)을 우선 사용. 문서당 2~5개. 새 공통 태그가 3개 이상 문서에서 필요하면 사전에 먼저 등록한다.
- 최종 Markdown은 100KiB 이하로 유지한다.

## 4. 연결 — 지식화

- 본문에서 관련 문서를 `[[문서 제목]]`으로 연결한다.
- 해당 영역의 `01 Dashboard` MOC에 새 노트 링크를 추가한다. 어디서도 링크되지 않는 노트를 남기지 않는다.
- 영역을 넘는 주제는 `지식 연결 허브`에 연결한다.
- 원본 아카이브는 건드리지 않고, 해석·요약은 별도 지식 노트에서 수행한다.

## 5. 검증 — 변경 후 확인

- [ ] 인코딩: 한글 깨짐 없음 (UTF-8)
- [ ] 프론트매터: YAML 파싱 정상, `updated` 갱신, `created` 보존
- [ ] 링크: 새로 깨진 wikilink·embed 없음, MOC 연결 완료
- [ ] 첨부: 참조하는 첨부 파일 존재
- [ ] diff: 요청 범위 밖 변경·민감정보 포함 없음
- [ ] 동기화 충돌 파일(`sync-conflict`) 미발생

## 6. 기록 — 커밋

- 의미 단위로 로컬 커밋한다. 메시지는 한국어로 "무엇을 왜"가 드러나게 쓴다.
- `git push`는 사용자 승인 후에만 수행한다.
- 대량 정비를 했으면 `01 Dashboard\Vault 데이터 현황.md`의 수치와 정비 결과를 갱신한다.

## Archive 처리

1. 완료·중단·비활성 자료만 대상으로 한다.
2. 보관 전 `status: archived`와 `updated`를 갱신한다.
3. Obsidian의 이동 기능으로 `99 Archive`로 옮긴다.
4. 보존 기간·삭제 기준이 정해지기 전에는 영구 삭제하지 않는다.

## 변경 등급과 실행 조건

`OpenClaw Obsidian 변경 정책`을 준용한다.

| 등급 | 예시 | 실행 조건 |
|---|---|---|
| 낮음 | 오탈자, 확실한 broken link 수정, 인덱스 링크 추가 | 변경 후 검증·diff 확인 |
| 중간 | frontmatter 정규화, 파일명 변경, 문서 이동 | 사전 목록화·백업·링크 갱신 검증 |
| 높음 | 삭제, 병합, 대량 이동, `visibility`/`rag` 변경 | **사용자 승인 필수** |

대량 변경 전 절차: Git 상태 확인 → 대상 목록화 → 작은 표본 먼저 실행·검사 → 전체 적용 → 검증 → 커밋.

중단 조건: Obsidian과 동시 수정 감지 / 기밀 문서가 `rag: include`에 포함 / 변경 후 링크·첨부 누락 증가 / 삭제·병합 대상의 중복 여부 미확정.

## 정기 점검 체크리스트

주기적으로(권장: 주 1회 이상) 아래를 점검하고 결과를 `Vault 데이터 현황`에 반영한다.

- [ ] `00 Inbox` 비우기 — 대기 노트 분류·배치
- [ ] `status: review` 문서 처리 (Home의 쿼리 활용)
- [ ] 동기화 충돌·임시 파일 검사 (발견 시 삭제하지 않고 보고)
- [ ] 프론트매터 누락·빈 노트·100KiB 초과 검사
- [ ] Git working tree 정리 — 미커밋 변경 확인

### 점검 명령 (PowerShell)

```powershell
# 폴더별 노트 수
Get-ChildItem "G:\Obsidian" -Directory | Where-Object Name -ne '.obsidian' |
  ForEach-Object { "{0,-20} {1,6}" -f $_.Name, (Get-ChildItem $_.FullName -Recurse -Filter *.md -File | Measure-Object).Count }

# frontmatter 없는 노트 (README·CLAUDE·PROCESS는 의도된 제외)
Get-ChildItem "G:\Obsidian" -Recurse -Filter *.md -File |
  Where-Object { $_.FullName -notmatch '\\\.obsidian\\' -and (Get-Content $_.FullName -TotalCount 1 -Encoding utf8) -ne '---' } |
  Select-Object FullName

# 동기화 충돌·임시 파일
Get-ChildItem "G:\Obsidian" -Recurse -File | Where-Object { $_.Name -match 'conflict|\.tmp$|\.bak' }

# Git 상태
git -C "G:\Obsidian" status --short; git -C "G:\Obsidian" log --oneline -5
```
