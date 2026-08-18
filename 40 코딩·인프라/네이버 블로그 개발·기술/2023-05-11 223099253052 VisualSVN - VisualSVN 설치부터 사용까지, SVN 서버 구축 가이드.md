---
title: "2023-05-11 223099253052 VisualSVN - VisualSVN 설치부터 사용까지, SVN 서버 구축 가이드"
type: blog-archive
status: active
created: 2023-05-11
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223099253052&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223099253052
published: "2023. 5. 11. 15:10"
body_hash: d6a2672002d05be997d7e70fc6a1adbd900f696e09f3be24c98e268e3d7a33a0
visibility: private
rag: exclude
---
# 2023-05-11 223099253052 VisualSVN - VisualSVN 설치부터 사용까지, SVN 서버 구축 가이드

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223099253052&categoryNo=982
- 게시일: 2023. 5. 11. 15:10

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfMTEw/MDAxNzQ0Mjk0NjYyODY0.hOOaj7ZNWwvdSiy2m5SNqfhxeq3tmzCUf0baFiOJnT4g.ZR6WbSAbezGADB3E2o3rDewcYk1eQG3zBezkltG8Zjsg.PNG/%ED%98%95%EC%83%81%EA%B4%80%EB%A6%AC-001.png?type=w80_blur)

​

VisualSVN 개요

VisualSVN은 Windows 환경에서 Subversion(SVN) 기반 버전 관리를 간편하게 사용할 수 있도록 돕는 도구로, Visual Studio와 통합되어 개발자들이 IDE 내에서 직접 소스 코드 관리 작업을 수행할 수 있게 한다. 서버와 클라이언트 설정이 간단하며, GUI를 통해 브랜치 관리, 커밋, 로그 확인 등 SVN의 주요 기능을 직관적으로 지원한다. 또한 VisualSVN Server를 통해 중앙 집중식 저장소 관리, Active Directory 통합, HTTPS 보안 등을 제공하여 팀 협업과 코드 관리에 최적화된 환경을 제공한다.

​

​

VisualSVN 설치

아래의 URL에 가서 VisualSVN Server 설치 파일을 다운로드한다.

<https://www.visualsvn.com/server/download/>

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMjQ3/MDAxNjgzNzgxMzYzNjAz.j9iduWt1ShCvuKskqk2utWhLGjxVP6hVp2dgIY17Tm4g.fT1dh4IQlyACjsse2w4a9Pk28MAd_NmZa-9IJBVbyM4g.PNG.agapeuni/img.png?type=w80_blur)

​

다운로드한 파일 "VisualSVN-Server-4.3.1-x64.msi"로 설치를 진행한다.

VisualSVN Server and Adminisration Tools를 선택을 확인하고 Next 클릭한다. 

![](https://postfiles.pstatic.net/MjAyMzA1MTFfNTEg/MDAxNjgzNzgxMzcwOTEz.4d3mcJcK1ZFVMbH6bVeYn04frEgAzDS8EZ4rWSWkpWkg.Gqf3v5mlv-vuC25xeUe1QDoSAr-h_k_0df19eMoQHRQg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMjYw/MDAxNjgzNzgxMzc0ODYz.b2QixLZpm6KCeEznzM_kbfTYULyd_31beJMrvs1hx_Mg.pifKRBCNgNEZ8AY0ZIP9Yh10S8zYvAXBRXS1R5486P0g.PNG.agapeuni/img.png?type=w80_blur)

​

Server Port는 기본값 443을 사용하고 있어서 444로 변경하였고 Repositories 경로는 D 드라이브를 지정했다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTk0/MDAxNjgzNzgxMzg2MTk4._igW4sYSS2h7FBO8TzTytPyFNmxKKupC_rivAuR5584g.PgJg-DxpsIofd_UQgQCT6a4cnYI0bMZK31jSO1fonnAg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTAy/MDAxNjgzNzgxMzkwNjY4.f7_qJiFF35U-z2Gy9-XgJZ6Pl6y7J3BfKQiIMQPud8Yg.t5ZY9u3w8UhIWuGIs9nOSZGNeRfDDjdGsO67ikd4G7Mg.PNG.agapeuni/img.png?type=w80_blur)

​

VisualSVN 실행

설치가 완료되면 VisualSVN Server Manager를 실행할 수 있다.

현재는 users, groups 모두 0이고 repositories도 0이다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMjg3/MDAxNjgzNzgxNDAyNjky.Uwf_BDR1YExdfYUWZZm-huzDCN0k48eO7b3PStGgohsg.Tsnr24pcZcuB65ScRV64_wem09EYQXUDh-1isdeA5Msg.PNG.agapeuni/img.png?type=w80_blur)

​

**1) Repositories 생성**

Repositories에서 우클릭으로 Create New Repository를 선택하여 신규 저장소를 만든다.

그리고 기본 설정인 Regular FSFS repository를 선택한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTA3/MDAxNjgzNzgxNDA5MTM2.bWM3ZGY5FNzm9S0es0FvCKZcxXq71aXDmcr1lM5Mf1wg.oNQcc4haZ5sm1Tb55R2z2fzsxMxOmXOFebve1xT2V3Eg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfOTEg/MDAxNjgzNzgxNDE0MDA3.5O2Zxk2HvX7cr7Kq5_LgPdUvNlToJBUiG8ndhMRdAs0g.pUN_BP97naSFNJtNbpKYCEOXn5vy00YfomyVH4p8cPIg.PNG.agapeuni/img.png?type=w80_blur)

​

​

Repository 이름을 지정한다. 추천 옵션인 Empty repository를 선택했다. 

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMjY2/MDAxNjgzNzgxNDE3NDA2.V5dgjQ4Aksk1tKNhyJXt-NijJ7aEg97xOTd-v8IfNdQg.GpKxAvLJOV4Cg0zBLyi-bDky7GJlUakSojEYYVLVwaQg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfNTUg/MDAxNjgzNzgxNDIxMjc1.1WH6Vf2BreCAVeYO_ivpRXpDun-HQSgG7yWILRdVV4kg.yg0KIeVwME83cupzSSkEXk18GQebX9F6V4cuUOPonJ0g.PNG.agapeuni/img.png?type=w80_blur)

​

접근 권한은 All Subverstion users have Read / Write access를 선택했다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMjkx/MDAxNjgzNzgxNDI1MTE0.JOpSVnWEc8fx92av3-G6OdVBXlLZnwg0qz1aFP5DLTog.EwboG37KHqN0Go6scCdagu1elKn3fkBN4q5cfp2FaOMg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfNTYg/MDAxNjgzNzgxNDI5NDI0._CG2zb9KJMRasF5L2HlOWkUk2t3DpENZRD6l1MIIZbIg.crPRfVOibWGu0P1Alo9FOvPgCk6DoRBxb_TVFDWSTScg.PNG.agapeuni/img.png?type=w80_blur)

**​**

**2) Users 생성**

이제 사용자를 생성한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTQx/MDAxNjgzNzgxNDQyNDcw.n3keApcYz2c4OuG92XYCmAaM7083Htb-ZJxzVCZVYPwg.Vb8qiaGiwlzAb5z2lWNtNzLz9cHAUEizma95TCxLNqIg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfNTgg/MDAxNjgzNzgxNDQ0NzY5.SXJ6s1TOELw5V3Wvf8Z6y3-onXoTOa0Itov6yLblXDog.pMTF88vfyScQZ04gtrIpHBnycawWVH-XAOb1gcVi8F0g.PNG.agapeuni/img.png?type=w80_blur)

​

생성한 사용자를 저장소에 매핑한다. 저장소 이름에서 우클릭하여 Properties를 선택한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfOTIg/MDAxNjgzNzgxNDQ4Nzgy.NScpCR4ZubX96U3qEwCdIuFsGtNoh4mJ8u_SF1CiCN8g.h5MtzLxH3kI8gjrzm2iF_-YJreVVVKG2PjN5hazmH3Eg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTQg/MDAxNjgzNzgxNDUyNjA1.FfEemt3Gc2LiucViXiox6OW_X7Rme2Z_qmiKxocoraog.k1saKmVS30DNiDugZhy3FU1dteVyFoYtWdR06KqFXpAg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTIg/MDAxNjgzNzgxNDU1ODI4.GpDJPd9zphdTLSctRgNHFlsXeXA2rYnrH6DylT4jpfQg.5zIRTe5fXh3b_24w27pALIaqN46TWdLkT6bcNc5qLysg.PNG.agapeuni/img.png?type=w80_blur)

​

VisualSVN 사용

자 그럼 브라우저로 간단히 접속해 보자. 저장소 이름에서 우클릭하여 Copy URL to Clipboard를 선택하면 주소가 복사된다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMzIg/MDAxNjgzNzgxNDU5NjYz.24vp-nx_FS96_6XINuUfnEA9vnXsIdhPIVKAtSbMvFsg.sX3GVSQSWegAVIFMGG7FMwqxvAofyhiggmiE_OcTzAEg.PNG.agapeuni/img.png?type=w80_blur)

​

복사된 주소를 브라우저에 입력하면 로그인 화면이 표시되고 생성한 사용자 정보를 입력하면 된다.

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTY2/MDAxNjgzNzgxNDY0NjU4.95QSv2PFdZpNrXaWeEUjEGdzylq5mS6hTsp0zH7vp8cg.-94qBea6feiq70OSZOCWoCtMF75gtTYJKOjAaACwTd0g.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTFfMTE2/MDAxNjgzNzgxNDY4MzM4.Bts-5JNA59LzIdRKsEzWtCdv3uy1iVY6vVUIks7wgwog.FIJw0-NIrE4f6Gsv2xMxDLKwEghAB9RXHu320npoLOAg.PNG.agapeuni/img.png?type=w80_blur)

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#VisualSVN #SVN설치 #버전관리 #소스코드관리 #개발툴 #VisualSVNServer #저장소생성 #사용자관리 #서버설정 #프로젝트관리 #개발자 #코드버전관리 #프로그램설치 #개발환경 #소프트웨어개발 #개발팁 #코드협업 #소프트웨어관리 #버전관리시스템 #팀워크 #프로젝트협업 #서버관리 #개발자도구 #소스관리 #VisualSVN사용법 #Git대안 #소스코드 #SVN서버 #프로그래밍 #코드관리

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
