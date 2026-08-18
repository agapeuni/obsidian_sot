---
title: "2023-04-14 223074821789 Fedora Server - GNOME 설치 (X Window)"
type: blog-archive
status: active
created: 2023-04-14
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223074821789&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223074821789
published: "2023. 4. 14. 20:19"
body_hash: 76fc57bafe5b5722cdbfb149e1652f33103197963a6b93bc7a6af9d16ae9cf1b
visibility: private
rag: exclude
---
# 2023-04-14 223074821789 Fedora Server - GNOME 설치 (X Window)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223074821789&categoryNo=982
- 게시일: 2023. 4. 14. 20:19

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfOTQg/MDAxNzQ0MjIzNjA1OTYy.V3Mi7nj_saFzSQs4-yk7iFQdwCaDKK4e0vxA-kWonVsg.f1FFbhfYWTLlfr9iqnSferdbfxp_A6jGt_2JMjs2uD0g.PNG/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-001.png?type=w80_blur)

​

1\. CLI 모드

Fedora Server 설치를 마치고 새롭게 부팅하면 CLI (Command Line Interface) 모드로 까만 화면이 표시된다. 그래픽 화면으로 사용자와 소통하는 것이 아니라 터미널에서 텍스트 명령어로 소통한다. X Window 환경을 사용하기 위해 GNOME을 설치해 본다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNiAg/MDAxNjgxNDcxMTM1NDYx.DyxZ4s6Qsf1HLLWIkSudHRxby50io0PxfTrzNnD8zIEg.pnMhF3MbJSBznpQT5Ul08o1MQgUBQuVUGMwEXyBh0O0g.PNG.agapeuni/img.png?type=w80_blur)

​

​

2\. GNOME 설치

sudo 권한으로 yum을 이용하여 GNOME을 설치한다.

> sudo yum groupinstall gnome

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTIz/MDAxNjgxNDcxMTYyODcy.ntqpLksUnbOxUCJnroN2MA0yyNw55Ps3qiALhIGEJ7sg.knt0iLSlYEvR6C8Ws2iYe8Il8h2SWn-f0yPsREY28UIg.PNG.agapeuni/img.png?type=w80_blur)

​

"Installing Groups : GNOME" 다운로드 크기는 409 메가이고 설치하는 패키지는 735개나 된다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjA0/MDAxNjgxNDcxMTY2NzM0.EH2rUyfiUgy32ZB3d2a6z1wUhASitL2cDK0VkyLfW88g.hYjhas-genaNTf1XS26dG8M25RM3rQEVyRoeID_jOlQg.PNG.agapeuni/img.png?type=w80_blur)

​

패키지 설치가 완료되었다. 

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTM2/MDAxNjgxNDcxMTY5Njg0.1pkG3EI2nOIpSNSl1oX91JHxGbMrmJE_Pm5NGv7biNEg.HzRVemO2B0pk-YF-Y_TFcQu2q8CBsKHlq1VsC-bKiaAg.PNG.agapeuni/img.png?type=w80_blur)

​

3\. 시스템 기본값 변경

GNOME 설치가 완료되면 시스템 기본값이 변경된다.

다음의 명령어로 값을 확인해 본다.

> systemctl get-default​

![](https://postfiles.pstatic.net/MjAyMzA0MTRfOTkg/MDAxNjgxNDcxMTc0OTY3._bqr_hOIa2Gfacdur6HfzJxOkTN8zOaCuz8NhhRc9R8g._BoojBpq9a67mM39lOYNFbv7xgIJfKATXpxqKgObvYwg.PNG.agapeuni/img.png?type=w80_blur)

​

값이 graphical.target이 아니라면 다음의 명령어로 GUI로 부팅하도록 값을 수정한다.

> systemctl set-default graphical.target

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNDUg/MDAxNjgxNDcxMTc5MDY0.wBpdsH19UqohY_tNPny01qF8su29DdeayW7tinVznrUg.LwFT7fgd7YXcWv0Cj2_rbJrrCKPl8dD9Y2DCbC8irP0g.PNG.agapeuni/img.png?type=w80_blur)

​

이제 재시작하면 GNOME 환경으로 부팅된다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjI5/MDAxNjgxNDcxMTgyOTcx.LSTbEYqFuksGxl-mohNFqaxOZfxu2WiMrMpnoWB2mrwg.npbMtEIxuVQSkY-FZh69P4zvnxPoinxWmkGocxK0sFYg.PNG.agapeuni/img.png?type=w80_blur)

​

![](https://blogfiles.pstatic.net/MjAyNjA2MTdfMTI4/MDAxNzgxNjIzNzc1NzA1.2QYwsPb7SzsAzNxbABqntGpXAscgNcqLRqQrRj6RQL0g.sS1rzJuq4-3ERN9qM8z69dPB5Y6mWd4F-WOitRfYhhEg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w1)

#Fedora #리눅스 #CLI모드 #명령어 #CommandLineInterface #GNOME #GNOME설치 #yum #서버설치 #시스템기본값 #그래픽환경 #XWindow #터미널 #패키지설치 #LinuxServer #FedoraServer #그래픽유저인터페이스 #서버관리 #LinuxCLI #리눅스명령어 #FedoraGNOME #GUI부팅 #systemctl #시스템설정 #소프트웨어설치 #리눅스기초 #리눅스환경 #서버운영체제 #Fedora커뮤니티 #오픈소스소프트웨어

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
