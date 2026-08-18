---
title: "2021-03-08 222267880975 패키지 관리자 - PIP(Package Installer for Python)"
type: blog-archive
status: active
created: 2021-03-08
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222267880975&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 222267880975
published: "2021. 3. 8. 1:41"
body_hash: a1366472e9e4d03ea973c5765dd9f67ac9ef5742354bb30198431cb7060d4edc
visibility: private
rag: exclude
---
# 2021-03-08 222267880975 패키지 관리자 - PIP(Package Installer for Python)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222267880975&categoryNo=982
- 게시일: 2021. 3. 8. 1:41

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTk1/MDAxNzQ0NDQzNjE3Njcw.gOYMHdUOGtz5fiKiUe0IW1Ks_ZsKLyxF034DHwmCh0Mg.l5TqUJBIz_-qHRBKw3sP4lYs4GVRA1mYkwxui8MTowwg.PNG/%ED%8C%8C%EC%9D%B4%EC%8D%AC-001_\(2\).png?type=w80_blur)

​

1\. pip 개요

pip(Python Package Installer)는 파이썬 패키지 관리자로, 파이썬 패키지를 설치, 업그레이드, 제거하는 데 사용되는 명령 도구이다. pip를 사용하면 파이썬 패키지 생태계에서 수천 개의 패키지를 쉽게 관리할 수 있다. 이미 구현되어 있는 다양한 패키지를 쉽게 사용할 수 있다. Python 3.4 버전 이후부터는 기본적으로 pip가 포함되어 있다. 

​

​

2\. pip 버전 확인

먼저 pip 버전을 확인해 보자.

$ pip -V 또는 pip --version

![](https://postfiles.pstatic.net/MjAyMTAzMDhfNTYg/MDAxNjE1MTM0MzAwNDEz.-v_FBDqRxgmoROBHF5ei8g8qxMi4KYzZ8mWYaP0Tceog.HAvL_-9nVJ86D3Q6GQYD0e3BP1zN655EQUrIPrbj2qMg.PNG.agapeuni/image.png?type=w80_blur)

​

3\. 패키지 설치

다음의 명령어로 패키지를 설치한다. 

$ pip install <패키지명>

![](https://postfiles.pstatic.net/MjAyMTAzMDhfNiAg/MDAxNjE1MTM0MzE3Nzc5.lPD7CbLlhm_YbjDrdwTrz5VB4_lqE3t5ImXrILXnrFYg.JiSakWL9eNLbMhtcKKGiA-A-q39r92MPFjPGttqsGgsg.PNG.agapeuni/image.png?type=w80_blur)

​

설치시 다음과 같이 특정 버전을 지정할 수도 있다.

PackageName PackageName == 1.3 PackageName >=1.2,<2.0 PackageName~=1.4.2

​

4\. 패키지 정보

설치된 패키지에 관한 정보를 보려면 다음을 입력한다.

$ pip show <설치된 패키지명>

![](https://postfiles.pstatic.net/MjAyMTAzMDhfMjM3/MDAxNjE1MTM0MzM1MDAy.XoH8Jv1C6RSlvyeGMC8-gaRUOYMM9OBgfZB6AOtW0dgg.WChXlR_DZEoUeH63YsYHbNYOmDtlh8vKR_2S8LkVP8sg.PNG.agapeuni/image.png?type=w80_blur)

​

5\. 패키지 목록

대소 문자를 구분하지 않고 설치된 패키지를 목록으로 표시한다.

$ pip list

![](https://postfiles.pstatic.net/MjAyMTAzMDhfNjQg/MDAxNjE1MTM0MzU0NTAw.wTFxKf7MdCwYKCxVqUmfo_t43M9UgAJ3jtQAWq0TIw8g.8Acrsd8raAk9Ty38lHA5lY7e7gcJ8yXJAKIIQbFueRsg.PNG.agapeuni/image.png?type=w80_blur)

​

구식의 패키지와 사용 가능한 최신 버전을 나열합니다.

$ pip list --outdated

![](https://postfiles.pstatic.net/MjAyMTAzMDhfMjYw/MDAxNjE1MTM0Mzc2NDkx.jv7A43qLTdTuSDWBDetC2fnX3cQ4-KG0EuM062vXSj0g.iWrZaVFjUNmzdRNeNdbh6yZpvvhAwdXIFAH78JwSWrIg.PNG.agapeuni/image.png?type=w80_blur)

​

6\. 패키지 제거

패키지를 제거한다.

$ pip uninstall 설치된 패키지명

![](https://postfiles.pstatic.net/MjAyMTAzMDhfMjE0/MDAxNjE1MTM0NTU1MjQw.3Y_2mkQ-Y_reXjlR1Lhzog22x_McDkEw4BeZluuL16Qg.V0sQctEnTP6gBrEH4p3soJgukRcbcuCpX2v1dSmGj-Mg.PNG.agapeuni/image.png?type=w80_blur)

​

7\. requirements.txt 파일

설치된 패키지를 요구사항 파일로 출력한다.

$ pip freeze > requirements.txt

​

요구사항 파일을 기준으로 설치할 때는 다음과 같이 입력한다.

$ pip install -r requirements.txt

![](https://postfiles.pstatic.net/MjAyMTAzMDhfMTE4/MDAxNjE1MTM0ODQ4OTI2.PclqSeUL2TTho8-5m5AstqayHLVbcd7Hp6aK0E3yswMg.v5rwNT1_wwTQCcREeM-PSEQcCOrnaTeA_nglErzCjRcg.PNG.agapeuni/image.png?type=w80_blur)

​

8\. pip 설정정보 확인

pip 설정정보를 확인하는 명령어이다. 설정정보를 표시힌다. 

$ pip config list

![](https://postfiles.pstatic.net/MjAyMTAzMDhfMzcg/MDAxNjE1MTM1MDc3MTE5.eMNOHbZhWlm2r-KFVhgyDMyJPWooI9aWZ1fKH7tQkiYg.Gdh0m2eIqcwQGwxG68NdLhuA0Aep0mn4_CITYz_cdYog.PNG.agapeuni/image.png?type=w80_blur)

​

9\. pip 설정정보 상세확인

pip 설정정보를 상세하게 확인하는 명령어이다. global, site, user 설정파일의 위치와 설정된 값이 표시된다. 

$ pip config debug

![](https://postfiles.pstatic.net/MjAyMTAzMDhfOTcg/MDAxNjE1MTM1MTU3MjQ1.bznPmD9cxjiRARmwjaKwqGxIM6Dyb8cqBenYO2AwVIwg.C1QvqtsE3gBO1oUmlTCTnYrpfNZYPh_c5gYzszL1LT4g.PNG.agapeuni/image.png?type=w80_blur)

global : 시스템 전체 

site : 현재 환경 

user : 사용자

​

​

10\. 참조 URL

보다 자세한 내용은 아래의 URL을 참고한다.

<https://pypi.org/project/pip/>

[ ![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fpypi.org%2Fstatic%2Fimages%2Ftwitter.90915068.jpg%22&type=ff120) ](https://pypi.org/project/pip/) [ **pip** The PyPA recommended tool for installing Python packages. pypi.org ](https://pypi.org/project/pip/)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#pip #파이썬패키지관리자 #파이썬설치 #패키지관리 #pip사용법 #파이썬프로그래밍 #pip설치 #패키지설치 #pip명령어 #requirements파일 #파이썬패키지업데이트 #파이썬패키지제거 #파이썬환경설정 #pip버전확인 #파이썬개발 #파이썬패키지업데이트방법 #pip설정확인 #pip설정정보 #파이썬개발환경 #piplist #pipfreeze #파이썬패키지리스트 #파이썬패키지버전 #파이썬패키지정보 #pipconfig #파이썬패키지다운로드 #파이썬설치방법 #pipguide #파이썬초보 #파이썬패키지문제해결 #pypi

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
