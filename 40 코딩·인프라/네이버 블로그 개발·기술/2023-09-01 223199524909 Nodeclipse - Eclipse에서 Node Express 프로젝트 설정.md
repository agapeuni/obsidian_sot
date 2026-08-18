---
title: "2023-09-01 223199524909 Nodeclipse - Eclipse에서 Node Express 프로젝트 설정"
type: blog-archive
status: active
created: 2023-09-01
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223199524909&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223199524909
published: "2023. 9. 1. 17:00"
body_hash: 9280decf88f7b5cc16d11d94d0e53f0b39ad4164bc4a2e892881c19677bd830b
visibility: private
rag: exclude
---
# 2023-09-01 223199524909 Nodeclipse - Eclipse에서 Node Express 프로젝트 설정

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223199524909&categoryNo=982
- 게시일: 2023. 9. 1. 17:00

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTU5/MDAxNzQ0NDY2NzgzNTc4.GbGsCiqrxDVNITKrMR_OqeYAQppAQ28bGne0hoOiAQMg.ntD4BGa4UVGQs-2rqdqPjm2_BqQ0z5mLkGXXBHTYagIg.PNG/Express-001_\(9\).png?type=w80_blur)

​

**1\. 개요**

이클립스(eclipse)에서 Node Express 프로젝트 환경설정을 한다. Nodeclipse 플러그인을 설치한 상태에서 Node Express 프로젝트를 생성하기 위해 "New > Project > Node Express Project"를 실행하면 아래와 같이 Express is not found.라는 오류메시지가 표시되어 진행할 수가 없다. 이런 경우에는 Express를 설치하고 이클립스에 Express 환경정보를 설정해 주어야 한다.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMjgz/MDAxNjkzNTM5ODA3OTk5.rvy8IPmNvXroklkA3E5DdlJ5XJ1_vHvcpELoRmCxdeEg.9FgBY6MNII4wFoefWDsjKceH1S0pAQV9Mji2DC4Oj5Ag.JPEG.agapeuni/img.jpg?type=w80_blur)

​

경우에 따라 네트워크에 프락시가 설정되어 있으면 npm install 이 동작하지 않을 수가 있다.

cmd 창에서 아래의 명령어를 실행해 npm에 프락시를 설정하면 설치가 제대로 진행된다.

npm config set proxy http://XXX.XXX.XXX.XXX:8080 npm config set https-proxy http://XXX.XXX.XXX.XXX:8080 npm config set strict-ssl false

XXX.XXX.XXX.XXX 는 프락시 IP 주소를 입력한다.

​

​

**2\. 설치**

cmd 창에서 다음의 명령을 실행하여 전역으로 express를 설치한다.

**> npm install -g express**

​

cmd 창에서 다음의 명령을 실행하여 전역으로 express generator를 설치한다.

**> npm install -g express-generator**

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMjM0/MDAxNjkzNTM5ODMxNDg5._UPMKXHUFPzB3FS909jCayhBp1XHoTCcnw_P-hst3c4g.XL3ADqZdzKgzRLezff31r8QYhn5N5wsixBW4xKmu90og.PNG.agapeuni/img.png?type=w80_blur)

​

express generator 설치가 완료된 후에 %APPDATA%\npm 폴더에 가보면 express 파일이 있다.

이 파일을 이클립스에서 설정 정보로 지정해 주면 된다.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMTc2/MDAxNjkzNTM5ODM1ODA3.HChUOXO7Hojsa2kfI6QRWA-NP2TVXuEIjg9HnBdHiP4g.m0PesYJOhFQPP6BHeaHcVUflMp7sbOi090IlxsA7P0og.PNG.agapeuni/img.png?type=w80_blur)

​

Window - Preferences로 환경설정 화면을 열고 Nodeclipse 메뉴를 선택하면 아래의 화면이 표시됩니다.

Express Path: 입력란의 Browse 버튼을 누르고 express generator가 설치된 폴더 아래의 express 파일을 선택합니다.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMjQz/MDAxNjkzNTM5ODQwMjc0.9mFeBS5-qfWERiR2XSywSmug47mkZerJofoQ_gLH9iAg.TqJrviBu1o_WAOsqAThYAE82nPgOSQrj29lid-CeOO0g.PNG.agapeuni/img.png?type=w80_blur)

​

​

**3\. 확인**

그럼 다시 Node Express 프로젝트를 생성해 보자.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfNzQg/MDAxNjkzNTM5ODQ0ODIx.q0ovlAMfDYfcab_AqN-FLXDPMLNRuHYcdORkICWf50wg.TZAY_79I_wzRXDDz_XQ_hzfQnD9HoTu6JsWIjRzl6PAg.JPEG.agapeuni/img.jpg?type=w80_blur)

​

이제는 오류메시지가 표시되지 않는다. 그럼 Node Express 프로젝트를 생성을 진행한다.

먼저 Project Name을 입력하고 Template Engine을 ejs로 선택하고 Finish 버튼을 클릭한다.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMTky/MDAxNjkzNTM5ODQ4NDg5.1abDOXmdv4sKc425Kq8KKTWP3DGNX-UDSiYrLB1wR6sg.jp3u5lyefXk1gkqFt3ijxM5ImiipBi89ARygZYl_lYsg.PNG.agapeuni/img.png?type=w80_blur)

​

프로젝트 생성이 완료가 되면 아래와 같이 express generator가 여러 파일을 자동으로 생성해 준다.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMTAw/MDAxNjkzNTM5ODUzODE3.lygMgRhAOxXYTYIb4PBzKuaPKt9t_X4Zt0Q5NSibq8og.cgiaoJ6LuMGjQeBe0nQnFow1xa6aGkdbtcSY7FoZ-Cog.JPEG.agapeuni/img.jpg?type=w80_blur)

​

**​**

**4\. 애플리케이션 생성기**

express-generator를 사용하여 명령창에서 애플리케이션 템플릿을 쉽게 만들 수 있다.

​

다음의 명령어를 입력하여 express와 express-generator를 설치한다.

> npm install express -g

> npm install express-generator -g

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMTUz/MDAxNjkzNTM5ODU4NDM1.bzLbfyThK7qpxLWCTy9MvQOeo4jVL65o2Unfm1KDJW0g.NHEc7TvLkKrkKICZ7sK1N_hWZYKzasdR7wotX_ujpzgg.PNG.agapeuni/img.png?type=w80_blur)

​

express 명령어의 도움말이다.

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMyAg/MDAxNjkzNTM5ODYyMDk0.O4zy4VIn0lGK8mM5G7Mh8ZbVEwUoAOxte_oCFU6fd48g.dWPEjbk0S7Xp9pEmCm3y8OsI8whgBP1SOt4-z8ENVjgg.PNG.agapeuni/img.png?type=w80_blur)

​

HelloExpress 이름의 프로젝트를 생성해 보자. view 엔진은 ejs로 선택했다.

> express --view=ejs HelloExpress

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMjE0/MDAxNjkzNTM5ODY2MTc3.ze-KfZH4vsDOlxJuCJp_RM4xwou5DV7dp3QyOvNegPgg.gIkxiae_TDC_By4nXah_sCPvW4b_FrrH36cBihu518cg.PNG.agapeuni/img.png?type=w80_blur)

​

프로젝트 폴더 아래에 다음과 같은 구조로 파일이 생성되었다.

HelloExpress ├── app.js ├── bin │ └── www ├── package.json ├── public │ ├── images │ ├── javascripts │ └── stylesheets │ └── style.css ├── routes │ ├── index.js │ └── users.js └── views ├── error.ejs └── index.ejs

​

생성된 프로젝트 폴더에 가서 의존성 패키지를 설치한다.

> cd HelloExpress

> npm install

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMTY1/MDAxNjkzNTM5ODg3MTMy.CrwRpfCx9jqUdrPSDwarACmPMQYLuznClKYrsCDxOBgg.xmNOaQuzdTKEKl_h6KK-El3sGyHtGf8nUUeFZ3eAgZ8g.PNG.agapeuni/img.png?type=w80_blur)

​

다음의 명령어로 프로젝트를 실행한다.

> npm start

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMjA3/MDAxNjkzNTM5ODkwNzI2.j5a6kXMbeEpNPG5-Eer6S6rbpvgsHaVwXvdVwHVctQYg.7Hihgii46eTik9mwwhr6Lao3AKHStinoDEfSTor5n8cg.PNG.agapeuni/img.png?type=w80_blur)

실행 화면

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMjgz/MDAxNjkzNTM5ODk0NDMx.dQWx4VWejXsj9NehoRt8pb4jezgbnhyyzmNU4wiihVsg.dOvzkHswBEXNZFXrnkB72cncGsTTDTqFXImJCE-16Swg.PNG.agapeuni/img.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#NodeJS #Express #Eclipse #Nodeclipse #웹개발 #프로젝트설정 #프로그래밍 #코딩 #npm #ExpressGenerator #자바스크립트 #템플릿엔진 #소프트웨어개발 #애플리케이션생성기 #웹애플리케이션 #개발자 #코드예제 #npm설치 #프로젝트생성 #프락시설정 #express설치 #코딩배우기 #기술블로그 #웹디자인 #프론트엔드 #백엔드 #Express예제 #NodeJS프로젝트 #웹개발자 #자바스크립트배우기

![](https://postfiles.pstatic.net/MjAyMzA5MDFfMTI4/MDAxNjkzNTM5NzAyODAz.hFxK465X17vYjfpaUz1Px1OHeM0pzoKA1sRTwp_kAkog.jyvCc6-lBZfTtKBLynwbv41qkMhR01VrdefrEbQYMFIg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
