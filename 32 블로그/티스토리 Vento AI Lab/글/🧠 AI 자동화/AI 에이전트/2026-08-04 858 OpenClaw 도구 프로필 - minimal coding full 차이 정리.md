---
title: OpenClaw 도구 프로필 - minimal coding full 차이 정리
type: blog-archive
status: active
created: '2026-08-04'
updated: '2026-08-16'
published: '2026-08-04T16:01:34+09:00'
source: https://agapeuni.tistory.com/858
source_blog: agapeuni.tistory.com
post_id: 858
category: 🧠 AI 자동화/AI 에이전트
tags: []
body_hash: e62c451b29e184dcad28f7b5b592246f7b0831027393e972dcb397528476f370
visibility: private
rag: exclude
---

# OpenClaw 도구 프로필 - minimal coding full 차이 정리

- 원문: https://agapeuni.tistory.com/858
- 게시일: 2026-08-04T16:01:34+09:00
- 분류: 🧠 AI 자동화/AI 에이전트

## 본문

![[03 Attachments/티스토리 Vento AI Lab/858/858-001-AI-Agent-001 (1).png]]

OpenClaw의 **도구 프로필(tool profile)**은 에이전트가 기본적으로 사용할 수 있는 도구 범위를 결정하는 보안·권한 설정입니다. tools.profile이 기본 허용 목록을 먼저 정하고, 이후 tools.allow, tools.deny, 에이전트별 설정이 추가 적용됩니다.

주요 프로필은 다음과 같습니다.

| 프로필 | 기본 | 범위 |
| --- | --- | --- |
| minimal | 상태 확인 전용 | 사실상 session_status 중심 |
| messaging | 채팅·메시지 중심 에이전트 | 메시지 및 세션 관련 제한된 도구 |
| coding | 파일·코드·명령 실행 | read, write, edit, exec, 세션·서브에이전트 등 |
| full | 모든 도구 허용 | 프로필 차원의 제한 제거 |

새로운 로컬 OpenClaw 설치는 명시하지 않으면 일반적으로 coding 프로필을 기본 사용합니다. full은 모든 도구를 개방하므로, 신뢰할 수 있는 단일 사용자 환경에서만 사용하는 것이 권장됩니다.

현재 설정 확인:

```
openclaw config get tools.profile
```

전체 도구 확인:

```
/tools compact
```

또는 자세히:

```
/tools verbose
```

현재 coding에서 full로 변경하려면:

```
openclaw config set tools.profile full
openclaw gateway restart
```

변경 확인:

```
openclaw config get tools.profile
openclaw gateway status
```

설정 파일에서는 다음 형태입니다.

```
{
  "tools": {
    "profile": "full"
  }
}
```

특정 도구만 추가하고 싶다면 full보다 기존 프로필에 도구를 추가하는 방식이 안전합니다.

```
{
  "tools": {
    "profile": "coding",
    "alsoAllow": [
      "browser",
      "cron"
    ]
  }
}
```

특정 도구를 차단하려면:

```
{
  "tools": {
    "profile": "full",
    "deny": [
      "camera.snap",
      "camera.clip",
      "screen.record"
    ]
  }
}
```

적용 우선순위는 대체로 다음과 같습니다.

```
tools.profile
→ tools.allow / tools.alsoAllow
→ tools.deny
→ 에이전트별 agents.entries[].tools
→ 채널·샌드박스·승인 정책
```

즉 full로 설정해도 tools.deny, 샌드박스 정책, 실행 승인 정책 또는 모델의 Tool Calling 미지원 때문에 일부 도구가 보이지 않거나 실행되지 않을 수 있습니다. 프로필은 도구를 설치하는 기능이 아니라, **이미 설치·연결된 도구를 사용할 수 있게 허용하는 정책**입니다.

개인이 직접 통제하고 Telegram 사용자가 본인으로 제한된 환경이라면 다음 구성이 현실적입니다.

```
{
  "tools": {
    "profile": "full",
    "deny": [
      "camera.snap",
      "camera.clip",
      "screen.record"
    ]
  }
}
```

반대로 외부 사용자나 여러 사람이 Telegram Bot에 접근할 수 있다면 full보다 coding을 유지하고 필요한 도구만 추가하는 편이 안전합니다. full은 명령 실행, 파일 수정, 외부 연계 도구까지 폭넓게 허용할 수 있습니다.

![[03 Attachments/티스토리 Vento AI Lab/858/858-002-주한길.png]]
