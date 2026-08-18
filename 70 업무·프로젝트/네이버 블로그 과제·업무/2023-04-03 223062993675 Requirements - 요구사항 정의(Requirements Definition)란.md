---
title: "2023-04-03 223062993675 Requirements - 요구사항 정의(Requirements Definition)란"
type: blog-archive
status: active
created: 2023-04-03
updated: 2026-08-12
tags:
  - 과제·업무
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223062993675&categoryNo=1123"
source_blog: agapeuni
source_category: 1123
log_no: 223062993675
published: "2023. 4. 3. 4:24"
body_hash: 67d93de89bee9ed2f997bfb3c7ede0a364e42d17229681dd47ef0db53d8f720c
visibility: company-confidential
rag: exclude
---
# 2023-04-03 223062993675 Requirements - 요구사항 정의(Requirements Definition)란

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223062993675&categoryNo=1123
- 게시일: 2023. 4. 3. 4:24

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTA3/MDAxNzQ0NDI4MDg2NjY4.N4IX1OXPY8AfVvdIEvtZOlH15PRV-JuFGmzd5ORxJb8g.LfWA1aLxRu1_obYVHf8FWC0MpM67nZ7wkx9LO9L56bog.PNG/%EC%9A%94%EA%B5%AC-%EB%B6%84%EC%84%9D-001.png?type=w80_blur)

​

요구사항 정의란 구현할 것을 결정하는 단계로 사용자와 이해관계자의 필요사항을 체계적으로 분석하고 정리하여 문서화하는 과정을 의미한다. 이는 프로젝트의 성공 여부를 결정짓는 중요한 단계이며, 개발팀이 정확한 목표를 이해하고 구현할 수 있도록 가이드 역할을 한다.

​

정의할 것이 많은 경우 중요한 것과 우선순위 기준으로 단계를 나누는 것이 좋다. 우선 요구사항 정의 단계에서 정의할 수 있는 것을 먼저 정의하고, 이해관계자와 협의하며 이후에 추가하는 것도 하나의 방법이다. 그리고 '어떻게 해야 하는지'를 정의하는 것도 중요하지만 '현재 어떻게 되어 있는지'를 확인하는 것도 중요하다. 

​

​

1\. 요구사항 정의의 목적

  * 프로젝트가 해결해야 할 문제를 명확히 식별하고 목표를 구체화하기 위함.

  * 개발팀과 이해관계자 간의 오해를 최소화하고, 동일한 방향성을 유지하기 위함.

  * 프로젝트 진행 중 발생할 수 있는 요구사항 변경을 효율적으로 관리하기 위함.

  * 개발 후 테스트 및 검증이 가능하도록 명확한 기준을 제공하기 위함.

​

​

2\. 요구사항 정의의 주요 요소

요구사항 정의는 크게 기능 요구사항과 비기능 요구사항으로 나뉜다.

​

**① 기능 요구사항(Functional Requirements)**

시스템이 수행해야 하는 구체적인 기능 및 동작을 정의하는 요구사항이다.

​

예시:

  * 사용자는 이메일과 비밀번호를 입력하여 로그인할 수 있어야 한다.

  * 관리자는 사용자의 계정을 생성, 수정, 삭제할 수 있어야 한다.

  * 주문이 완료되면 사용자에게 이메일로 알림이 전송되어야 한다.

​

**② 비기능 요구사항(Non-Functional Requirements)**

시스템의 성능, 보안, 안정성, 유지보수성 등 품질과 관련된 요구사항을 정의하는 부분이다.

​

예시:

  * 로그인 요청은 2초 이내에 처리되어야 한다. (성능)

  * 사용자의 비밀번호는 암호화되어 저장되어야 한다. (보안)

  * 시스템은 하루 24시간, 주 7일 동안 동작해야 한다. (가용성)

  * 장애 발생 시 30분 이내에 복구가 가능해야 한다. (복구성)

​

​

3\. 요구사항 정의 과정

요구사항을 정의하는 과정은 다음과 같이 진행된다.

​

① 요구사항 수집(Requirement Elicitation)

  * 이해관계자(고객, 사용자, 개발팀 등)와 인터뷰, 설문조사, 워크숍 등을 통해 요구사항을 수집한다.

  * 기존 시스템 분석, 벤치마킹 등을 활용하여 추가적인 요구사항을 도출한다.

​

② 요구사항 분석(Requirement Analysis)

  * 수집된 요구사항을 정리하고, 모호하거나 중복된 요구사항을 제거한다.

  * 요구사항 간 우선순위를 설정하여 중요도를 평가한다.

  * 기술적으로 실현 가능한지 여부를 검토한다.

​

③ 요구사항 명세(Requirement Specification)

  * 분석한 요구사항을 문서화하여 SRS(Software Requirements Specification) 문서 또는 기능명세서를 작성한다.

  * 이해관계자들이 쉽게 이해할 수 있도록 다이어그램, 표, 프로토타입을 활용한다.

​

④ 요구사항 검증 및 승인(Requirement Validation & Approval)

  * 문서화된 요구사항을 개발팀, QA 팀, 고객과 함께 검토하여 오류를 수정한다.

  * 최종적으로 이해관계자의 승인을 받아 공식적인 요구사항으로 확정한다.

​

​

4\. 요구사항 정의 시 고려해야 할 사항

요구사항 정의는 프로젝트 성공의 핵심이므로, 다음 사항을 유의해야 한다.

  * 명확성(Clarity): 모호한 표현 없이, 누구나 이해할 수 있도록 구체적으로 작성해야 한다.

  * 일관성(Consistency): 요구사항 간 충돌이 없어야 한다.

  * 검증 가능성(Verifiability): 요구사항이 테스트 가능해야 한다.

  * 추적 가능성(Traceability): 요구사항이 변경될 경우 어디에 영향을 미치는지 추적 가능해야 한다.

  * 변경 용이성(Modifiability): 요구사항이 변경될 가능성을 고려하여 관리해야 한다.

​

​

5\. 요구사항 정의의 산출물

요구사항 정의의 최종 결과물로는 다음과 같은 문서가 생성된다.

  * SRS(Software Requirements Specification, 소프트웨어 요구사항 명세서)

  * 프로젝트 목표, 범위, 기능/비기능 요구사항, 제약 사항 등을 포함한 공식 문서

  * Use Case Diagram(사용 사례 다이어그램)

  * 사용자와 시스템의 상호작용을 나타낸 다이어그램

  * Wireframe, Prototype(와이어프레임, 프로토타입)

  * UI/UX 요구사항을 시각적으로 표현한 모델

  * Requirement Traceability Matrix(RTM, 요구사항 추적 매트릭스)

  * 요구사항과 테스트 케이스 간의 연관성을 추적하는 문서

​

​

6\. 요구사항 정의의 중요성

잘 정의된 요구사항은 프로젝트의 성공 가능성을 높이고, 개발 기간과 비용을 절감하는 데 큰 영향을 미친다.

  * 명확한 요구사항 정의 → 개발 중 혼선 방지

  * 테스트 가능 요구사항 → 품질 보장

  * 변경 관리 체계 구축 → 프로젝트 일정 및 비용 절감

​

따라서, 요구사항 정의 단계에서 충분한 시간을 투자하고 철저한 검토를 거치는 것이 프로젝트의 성공을 위한 필수 요소다. 

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#요구사항정의 #소프트웨어개발 #프로젝트관리 #KPI #요구사항분석 #IT기획 #소프트웨어요구사항 #시스템설계 #개발자 #비즈니스분석 #프로젝트성공 #소프트웨어엔지니어링 #요구사항명세서 #비기능요구사항 #기능요구사항 #UX디자인 #프로덕트매니지먼트 #프로토타입 #소프트웨어테스트 #개발프로세스 #애자일개발 #IT전략 #소프트웨어문서화 #시스템개발 #비즈니스전략 #요구사항관리 #테스트케이스 #UIUX디자인 #벤치마킹 #프로젝트리스크관리

![](https://postfiles.pstatic.net/MjAyNTAyMTVfNzIg/MDAxNzM5NjEzMzc0MTIw.6r3uMQaKjdbU1ebRcloat0kZ2H6nTiM8nqYBJwVSygQg.vpkJPyvCKfJd2oMX67pVdOKXkxA6NnMObJM7ja4zimYg.PNG/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
