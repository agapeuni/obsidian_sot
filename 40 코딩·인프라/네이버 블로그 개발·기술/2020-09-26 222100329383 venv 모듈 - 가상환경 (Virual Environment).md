---
title: "2020-09-26 222100329383 venv 모듈 - 가상환경 (Virual Environment)"
type: blog-archive
status: active
created: 2020-09-26
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222100329383&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 222100329383
published: "2020. 9. 26. 17:29"
body_hash: 823c39532c3da5de59636a9543a28b66496e521fd1dac3cc3afee9a6ba49b065
visibility: private
rag: exclude
---
# 2020-09-26 222100329383 venv 모듈 - 가상환경 (Virual Environment)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222100329383&categoryNo=982
- 게시일: 2020. 9. 26. 17:29

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMjA5/MDAxNzQ0NDQzMjkxMTY5.P9MOVYa3B7ss7l2y_TEyFdBpSxe41ROBeF9auHIXunQg.uWghcjQfzw0QdCaG494F2Z4TSRGY_yc8wo8ONx9-gbAg.PNG/%ED%8C%8C%EC%9D%B4%EC%8D%AC-001_\(1\).png?type=w80_blur)

​

1\. 패키지 충돌

Python 애플리케이션을 개발할 때 외부 라이브러리나 특정 버전의 라이브러리를 파이썬 패키지 관리자 도구인 pip로 설치한다. 설치되는 라이브러리는 기본적으로 Python 설치 폴더의 "LIb/site-packages" 안에 저장되는데 동일한 컴퓨터 환경에서 여러 개의 Python 프로젝트를 진행하게 되면 모듈 간 충돌이 발생할 수 있다.

​

가상환경을 사용하지 않고 하나의 글로벌 환경으로 모듈을 설치하면 한 곳에 관리되는 편리함은 있지만 프로젝트를 진행할 때 사용하려는 모듈의 버전 충돌이 발생하여 문제가 발생한다. 그리고 해당 프로젝트에서 참조하고 있는 라이브러리만 관리하고 싶어도 하나의 환경에 포함되어 있어 별도로 나누기도 어려워진다.

​

2\. 가상환경

파이썬에서는 이러한 문제점을 해결하기 위해 가상 환경(Virtual Environment)이라는 독립된 작업 공간을 만들어 관리한다. Python 프로젝트를 진행할 때 프로젝트별로 가상 환경을 만들어 관리하면 격리된 작업환경을 갖게 되어 충돌을 방지한다. 프로젝트 간의 라이브러리 종속적인 문제도 해결된다. 가상 환경을 사용하면 완전하게 독립된 작업 공간을 갖추게 된다.

![](https://postfiles.pstatic.net/MjAyMDA5MjZfNSAg/MDAxNjAxMTA4MjMwMDQ2.6gOvFh8-TJ2uEEGWRyi08poKZb8IKTX0PTq69DStpYcg.RRRYKNb_8IekGkHGvBp0XZR9UlGVRmcus4Ek-YtP6xUg.PNG.agapeuni/image.png?type=w80_blur)

[이미지 출처] <https://hackersandslackers.com/python-virtualenv-virtualenvwrapper/>

​

3\. 가상환경 생성

그럼 Python에 기본 모듈로 포함되어 있는 venv 명령을 사용하여 가상환경을 생성해 보자. 명령 프롬프트(Windows) 또는 터미널(Linux/macOS)을 열고, 가상 환경을 생성할 디렉터리로 이동한 다음 venv 모듈을 사용하여 가상 환경을 생성한다. 참고로 venv 모듈은 Python 3.3 이상부터 사용 가능하다.

​

아래의 명령으로 D 드라이브 아래에 "Z_PyWork"라는 이름으로 가상환경이 만들어진다.

**python -m venv 가상환경 이름(폴더명)**

![](https://postfiles.pstatic.net/MjAyMDA5MjZfMjkz/MDAxNjAxMTA4MDMzNzY4.52XVsLLsZ0WCz1CcsNg-IKqABYWGY5ng39Y-md1A0QYg.hsFKF1O_7MedcdXSyuXzFy9TYlTB9srL_nuye_HGsEYg.PNG.agapeuni/image.png?type=w80_blur)

​

python -m venv Z_PyWork를 실행하여 가상 환경을 생성하면 아래와 같이 구성된다.

Z_PyWork는 가상 환경이 이름이다. 가상 환경의 이름은 원하는 대로 설정할 수 있다.

![](https://postfiles.pstatic.net/MjAyMDA5MjZfMTcg/MDAxNjAxMTA4MTM3OTc4.tegGNuJTb-DPsWetRuFjCoy9_tUj6kR48LrB6ltzUh0g.Lk_BhW98P-T0lfTIQMw9VSM2fcC0tAWfVj13Xh6B-Xog.PNG.agapeuni/image.png?type=w80_blur)

​

D:\Z_PyWork\Scripts 폴더를 보면 

Python 인터프리터와 가상 환경을 activate/deactivate 하는 명령어도 포함되어 있다.

![](https://postfiles.pstatic.net/MjAyMDA5MjZfNiAg/MDAxNjAxMTA4MTUyNjMw.2DMDHIFTcHPuK9K5DhRTNtG4MmcEDfEtBAD2-citiOIg.g3DX8A_glPABhobeo6m-leNv3oXrPWqAafTHuscJhxIg.PNG.agapeuni/image.png?type=w80_blur)

​

​

4\. 가상환경 활성화

가상환경을 활성화하기 위해 다음의 명령어를 입력한다.

> Scripts\activate 

> 가상환경이름\Scripts\activate

![](https://postfiles.pstatic.net/MjAyMDA5MjZfNzQg/MDAxNjAxMTA4NDMzMDI4.kzCoRBe8LzTpdQS7WDQAyaCRkhIZ14mZSGCVUTGIDQwg.YtLiP7qNZFa7NsM43RLKDx1gnp2sMqbiO132btC_LK0g.PNG.agapeuni/image.png?type=w80_blur)

​

폴더 이름을 자세히 보면 앞쪽에 Z_PyWork라는 이름이 괄호로 표시되어 있다.

가상 환경이 활성화되면 프롬프트 앞에 활성화된 가상 환경의 이름을 표시한다.

![](https://postfiles.pstatic.net/MjAyMDA5MjZfMjAx/MDAxNjAxMTA4NDQwNTcy.RqWFavSAlnB2hVq_azUGhfOIEJBRIKX4D75vzDlcSnQg.WU7Haj_R0cnthRpsK0BPIts4fF9mRGpVp2bICsPSJqsg.PNG.agapeuni/image.png?type=w80_blur)

​

가상 환경에서 pip list라고 입력하면 pip와 setuptools만 설치되어 있고 pip 버전도 아직 최신이 아니다.

![](https://postfiles.pstatic.net/MjAyMDA5MjZfNjIg/MDAxNjAxMTA4NjE1MjM5.sAE4RMLdnvozzBEkoOC4pf8CUAE61gc9j4S5NH46SUgg.Y-JXH6gSmR9WtZ3zt7owrDCbLaCOuZ4jdFnCQTl-AyUg.PNG.agapeuni/image.png?type=w80_blur)

가상 환경이 활성화된 상태에서 필요한 패키지를 설치하거나 파이썬 스크립트를 실행할 수 있다. 

해당 가상 환경에만 패키지가 설치되며 다른 환경과 격리된다.

​

​

5\. pip 업그레이드 

다음의 명령어로 pip를 업그레이드한다.

python.exe -m pip install --upgrade pip

![](https://postfiles.pstatic.net/MjAyMDA5MjZfMTA0/MDAxNjAxMTA4NzI1MTU1.0DrKRMBqrfnKskI_6L39XkbfklmKmHziAhZCT77YZkkg.ITN8degkRG0dAmQrs2OBtDsefNjbk5Fh1PikjMIcNQsg.PNG.agapeuni/image.png?type=w80_blur)

​

​

6\. 가상환경 비활성화

가상 환경을 더 이상 사용하지 않고 중지하려면 가상 환경을 비활성화하면 된다.

그러면 폴더 이름 앞에 있었던 (Z_PyWork)라는 가상 환경 이름이 사라진다.

​

다음의 명령어를 입력하여 가상 환경을 비활성화한다.

> deactivate

> Scripts\deactivate

![](https://postfiles.pstatic.net/MjAyMDA5MjZfMTc5/MDAxNjAxMTA4ODUzMDI1.tAuL39RrvwVsp4Xc2Iv0dRy_Y4PuXiO5v8PWp2U7eoUg.A7Kw6BkHvx79CZshyyWVPJQjId1P2XyQ1DYNOUaW-NQg.PNG.agapeuni/image.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#파이썬 #가상환경 #패키지충돌 #pip #pythonvenv #프로그래밍 #소프트웨어개발 #개발환경 #코드관리 #개발자 #프로젝트관리 #모듈 #라이브러리 #환경설정 #가상환경설정 #Python패키지 #pip업그레이드 #프로그래밍팁 #파이썬개발 #코딩 #프로젝트별가상환경 #가상환경활성화 #개발도구 #파이썬기초 #환경구성 #개발자도구 #스크립트 #파이썬모듈 #Python개발

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
