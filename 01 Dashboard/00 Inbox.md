---
title: 00 Inbox
type: moc
status: active
created: 2026-08-11
updated: 2026-08-11
tags:
  - moc
  - area/inbox
aliases:
  - Inbox
visibility: private
rag: exclude
---

# 00 Inbox

분류 전 메모, 외부 수집 자료, AI Agent의 임시 작성물이 먼저 들어오는 곳이다.
분류가 확실하지 않은 자료는 임의로 영역에 배치하지 않고 여기에 둔다.

## 처리 절차

1. 제목, 출처, 작성일과 최소 Properties를 기록한다.
2. 내용을 검토하고 가장 적합한 영역을 정한다.
3. 해당 영역으로 옮기고 관련 문서와 `[[링크]]`로 연결한다.
4. 중복으로 보이는 자료는 즉시 삭제하지 않고 원본과의 관계를 먼저 확인한다.

## 처리 대기 문서

```query
path:"00 Inbox"
```

## 관련

- [[Home]]
- [[README - Vault 구조]]
