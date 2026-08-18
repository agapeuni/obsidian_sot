---
title: "2022-02-11 222645231638 Anaconda - Conda constructor 아나콘다 인스톨러 생성"
type: blog-archive
status: active
created: 2022-02-11
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222645231638&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 222645231638
published: "2022. 2. 11. 22:07"
body_hash: 721c3c56117268d8e6afc9407fa574329c6e5155b230b744a3e8a3fa8bf41f3d
visibility: private
rag: exclude
---
# 2022-02-11 222645231638 Anaconda - Conda constructor 아나콘다 인스톨러 생성

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222645231638&categoryNo=982
- 게시일: 2022. 2. 11. 22:07

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTk0/MDAxNzQ0NDQ1OTk4NTE3.B3BI96-pSHFajprTr1ktmKPfVWvMosfJb-tQKvpjzZEg.WdT1xDOGmZzyOrQKdlRC1Ha5ii95IfkXbkBWC_cxqC4g.PNG/%EC%95%84%EB%82%98%EC%BD%98%EB%8B%A4-001_\(2\).png?type=w80_blur)

​

1\. Conda constructor개요

conda constructor는 conda 패키지 구성을 위한 설치 프로그램을 생성하는 도구이다. 사용자가 제공한 사양을 사용하여 필요한 패키지로 구성된 아나콘다 설치 프로그램을 만들 수 있다. 필요한 종속성과 함께 제공한 사양을 포함하는 환경을 만는다. conda constructor를 사용하여 Anacoda 인스톨러를 직접 만들어 보고 설치해 보기로 하자. 윈도우용과 리눅스용을 만들 수 있는데 간단하게 리눅스용으로 빌드해 본다.

​

​

2\. 파일 다운로드

먼저 아래의 GitHub에서 관련 파일을 다운로드 한다.

<https://github.com/conda/constructor>

[ ![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fopengraph.githubassets.com%2F00ecb297c67269e5cfe7e5dedcc0db2e4a1c7612df234a56296f1c47e71310de%2Fconda%2Fconstructor%22&type=ff500_300) ](https://github.com/conda/constructor) [ **GitHub - conda/constructor: tool for creating installers from conda packages** tool for creating installers from conda packages. Contribute to conda/constructor development by creating an account on GitHub. github.com ](https://github.com/conda/constructor)

​

다운로드하여 옮겨도 되고 리눅스 콘솔에서 다음의 명령어로 각각의 파일을 바로 다운로드 할 수 있다.

$ wget <https://raw.githubusercontent.com/conda/constructor/master/examples/maxiconda/EULA.txt>

$ wget <https://raw.githubusercontent.com/conda/constructor/master/examples/maxiconda/README.md>

$ wget <https://raw.githubusercontent.com/conda/constructor/master/examples/maxiconda/construct.yaml>

​

​

이제 인스톨러 생성에 필요한 파일이 모두 준비되었다.

![](https://postfiles.pstatic.net/MjAyMjAyMTFfMTM5/MDAxNjQ0NTg0NTk3ODgw.bffV34AFQlAMEU5zWL9PbCzO8cYkgPta3qShsJXx3A0g.-fkvxG-vsRlYn5b9DJS_WM3JADZygVqj08SWpgCMxywg.PNG.agapeuni/img1.daumcdn.png?type=w80_blur)

​

3\. construct.yaml

construct.yaml 파일을 직접 작성하기 보다 examples에 올려진 파일을 기준으로 편집한다.

​

<https://github.com/conda/constructor/tree/master/examples/maxiconda>

![](https://postfiles.pstatic.net/MjAyMjAyMTFfMTI1/MDAxNjQ0NTg0NTgwNTU1.A97KvwkQQHCainsWz0248iifhfnsUyGW0daEMXI090Qg.lC24uiFTuzE3CX7_b5KlyoDA8-zsgdZD6uQn7tF-GgUg.PNG.agapeuni/1.png?type=w80_blur)

​

constructor는 construct.yaml 파일을 기준으로 인스톨러를 생성한다. 해당 인스톨러로 설치하면 필요한 패키지를 초기에 구성할 수 있다. anaconda 설치 과정이 끝나는 시점에 실행할 명령어나 pip 명령어로 추가하여 설치할 패키지가 있으면 post_install.sh에 기술하면 된다.

name: Installer_Linux version: 1.0.0 install_in_dependency_order: True channels: \- http://repo.anaconda.com/pkgs/main/ specs: \- python 3.7.9 \- conda \- numpy \- scipy \- pandas \- matplotlib license_file: EULA.txt #post_install: post_install.sh

4\. 인스톨러 생성

이제 인스톨러를 생성해 보자. 생성되는 프로그램은 아나콘다 설치 프로그램과 유사하지만 파일크기는 훨씬 작다.

​

$ constructor .

![](https://postfiles.pstatic.net/MjAyMjAyMTFfMTQz/MDAxNjQ0NTg0NjEwNzk2.l75KUirL6FogBXrBatNegix6U2-w1czcSmI1uWTpMoUg.JlORp7A0e2j8vAGlKG8aj354-7D0it8gPUbOJux7I_gg.PNG.agapeuni/img1.daumcdn.png?type=w80_blur)

오류 없이 성공적으로 생성이 되면 "Installer_Linux-1.0.0-Linux-x86_64.sh" 파일이 만들어 진다.

​

​

5\. 인스톨러 설치

생성된 설치 프로그램으로 사용자정의 아나콘다 환경을 구성할 수 있다. 그럼 만들어진 인스톨러로 리눅스에 신규로 설치를 진행해 보자.

$ sh Installer_Linux-1.0.0-Linux-x86_64.sh

![](https://postfiles.pstatic.net/MjAyMjAyMTFfNzIg/MDAxNjQ0NTg0NjMyMjUy.YkVBIJwe66oRqUG3nJwUB-qZN7jnsXUIv_pJaqaZ2NEg.2gJYGwK7FxsjUey2N1cRYHt-imKd4UL50PyhFmJqGccg.PNG.agapeuni/1.png?type=w80_blur)

​

위와 같은 화면이 표시되면 ENTER를 입력하여 설치를 진행한다. 라이센스를 읽고 수락하면 yes를 입력한다.

설치할 경로는 디폴트 설정값을 두고 ENTER를 입력한다. 다른 폴더에 설치를 하려면 경로를 입력하면 된다.

![](https://postfiles.pstatic.net/MjAyMjAyMTFfNDIg/MDAxNjQ0NTg0NjM2MDgz.47hCK2bNXbsZlDZZBGiJKJqdyQ7YIJnQqXzi-Dp9_YQg.1NsODF4gm1eSaUflZ9dXXEQVJD2QbuXwuJe3pJhI2ksg.PNG.agapeuni/2.png?type=w80_blur)

​

패키지 설치를 한 뒤에 conda 초기설정을 물어본다. yes를 입력하면 터미널을 시작할 때 자동으로 (base) 콘다환경에서 시작한다.

![](https://postfiles.pstatic.net/MjAyMjAyMTFfMjY1/MDAxNjQ0NTg0NjQwNTgx.W_YFn3QbOlbpAnUQ_XjejOExMFWBcl8UMY_rF8aqrvMg.uc8w1cVMCAAA2_GoF5h2g4YDxk68g4GtpJ8FfN_FnOsg.PNG.agapeuni/3.png?type=w80_blur)

​

6\. 다운로드 정리표

운영체제별(Windows, Linux, MacOSX) 아나콘다 인스톨러를 받을 수 있다.

<https://repo.anaconda.com/archive/>

[ **Index of /** Filename Size Last Modified MD5 .winzip/ - <directory> Anaconda-1.4.0-Linux-x86.sh 220.5M 2013-03-09 16:46:53 d5826bb10bb25d2f03639f841ef2f65f Anaconda-1.4.0-Linux-x86_64.sh 286.9M 2013-03-09 16:46:38 9be0e7340f0cd2d2cbd5acbe8e988f45 Anaconda-1.4.0-MacOSX-x86_64.sh 156.4M 2013-03-09 16:46:57 db877... repo.anaconda.com ](https://repo.anaconda.com/archive/)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Anaconda #CondaConstructor #아나콘다 #데이터분석 #Python #파이썬 #머신러닝 #딥러닝 #리눅스 #윈도우 #MacOS #데이터과학 #인스톨러생성 #커스텀환경 #constructyaml #데이터분석환경 #conda #콘다 #numpy #scipy #pandas #matplotlib #Python환경설정 #conda환경 #리눅스설치 #아나콘다설치 #GitHub #Python패키지 #데이터분석도구 #환경설정 #아나콘다다운로드 #파이썬패키지

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
