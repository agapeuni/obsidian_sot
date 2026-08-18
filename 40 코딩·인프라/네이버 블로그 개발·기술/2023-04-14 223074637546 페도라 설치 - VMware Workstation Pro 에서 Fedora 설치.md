---
title: "2023-04-14 223074637546 페도라 설치 - VMware Workstation Pro 에서 Fedora 설치"
type: blog-archive
status: active
created: 2023-04-14
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223074637546&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223074637546
published: "2023. 4. 14. 18:05"
body_hash: f70ecf3608b6f608ff5592e55fd6151a5d536ea7911b6133af61cb014e1743ab
visibility: private
rag: exclude
---
# 2023-04-14 223074637546 페도라 설치 - VMware Workstation Pro 에서 Fedora 설치

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223074637546&categoryNo=982
- 게시일: 2023. 4. 14. 18:05

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfMTQ4/MDAxNzQ0MjIzMzg1NTM3.F27YBiT1EGxr9g408-7gWpVv0m4eqHRPiCdMf51KIicg.SxHXvZ989IYpzHVfzBm8GDHVoj9F1rP43Aymg3KMb2gg.PNG/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-001_\(1\).png?type=w80_blur)

​

1\. 개요

현재 수행 중인 과제는 리눅스 환경에서 인스톨러를 개발하는 일이다. 소프트웨어 환경 테스트가 필요해서 VMware에 Fedora를 설치해 본다.

​

​

2\. VMware Workstation Pro 설치

아래의 주소에서 VMware Workstation 16 Pro를 다운로드하여 설치한다. 별도의 등록 없이 30일간 평가판으로 사용할 수 있다.

<https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html>

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjk5/MDAxNjgxNDYyOTczNTI1.A6WhaNlyQ0KCMkPY3kYMEl9nqL7AyNwxQfvA-Nnme9Eg.jEAoJUaawwaOrakp3LuJlAZ1-T40BVP7vDKqb1mUGtcg.PNG.agapeuni/img.png?type=w80_blur)

​

VMware Workstation Pro 설치

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjg2/MDAxNjgxNDYyOTgyNjIy.a4NpkawsMpDbXF7A90BiVD6baV3cG5_ZJusXPyDHLhsg.OG18TpBD6ENgE8Wei3p346s6erFt1RZJ2AHldBUi7o0g.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNjEg/MDAxNjgxNDYyOTg2NzYz.IKRNkOKLKWJiC0xjPjfVI_1fntcvoh6hFMF49sZ7jjgg.jjB4qtgPY3HxbGCCyKBqBJMA8K-Aq06WZ_ZHIYmV1fYg.PNG.agapeuni/img.png?type=w80_blur)

​

평가판으로 잠시 사용할 거라 다음의 설정은 둘 다 해제하였다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjU2/MDAxNjgxNDYyOTk0NjYy.n5oVPzQ-0w4dIVlI7Rtda8g4LVKCb2-R-4AVbGXwqVsg.Nz-_xoUphK34zT1fPnvCH6cI9Ag2x4rDresD4tO8F3Qg.PNG.agapeuni/img.png?type=w80_blur)

​

​

3\. Fedora Server 다운로드

Fedora 리눅스 사이트로 이동하여 Fedora Server를 다운로드한다.

<https://getfedora.org/ko/>

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTkg/MDAxNjgxNDYzMDAzODk5.ZnGQ5jfTXAwUKQp8LqaXDaOJ_TbNW86c2fzjTIAdbdog.W8ZFywLnRJnCxWuWfMXd8VftPWJFAYtJEG3wxekflpsg.PNG.agapeuni/img.png?type=w80_blur)

​

"Fedora 33 Server 다운로드" 페이지에서 "Fedora 33: x86_64용 기본 ISO 이미지"를 클릭하여 ISO 파일을 다운로드한다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNzMg/MDAxNjgxNDYzMDA4NDY3.V094lktjug9d2Qd9CU7v6RRRZPcNDpewqe77GazQox4g.yAkuvKBhCn5qDJmdH7QSeV7TIJtAVq1DJ1ggjFzvptYg.PNG.agapeuni/img.png?type=w80_blur)

​

4\. Fedora Server 설치

VMware Workstation을 실행하여 새로운 가상환경을 만든다. 

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMzMg/MDAxNjgxNDYzMDEyMDY1.LzkWQ5F5EsXaUqdMaqcE7MoTKocM1XhkdxBZChHU2zMg.wug9B_SAXlSK9vq3QeADcK41a4ltOI7U3NAXS00s4eog.PNG.agapeuni/img.png?type=w80_blur)

​

다운로드한 Fedora-Server-dvd-x86_64-33-1.2.iso를 선택한다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTk3/MDAxNjgxNDYzMDE2MTU1.99OTArZfuhkH-d1cElJ_M-WxO0VdDnePvRlasBlQ89kg.AdqM_RdPXp6RSl5tDe7N0QKgVarGojDy3wCAGk2sNF4g.PNG.agapeuni/img.png?type=w80_blur)

​

설정을 마치고 나면 Feroda 33 설치가 진행된다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjM5/MDAxNjgxNDYzMDIwNzQz.Ug6NoumyVIP5GWJxP9DFfYNnGca021s3uJgt1-9hcqEg.Oq3f2YqAtdQsOt4VuhyTqE1AuWur8sPeTLPKwu3XKycg.PNG.agapeuni/img.png?type=w80_blur)

​

이전 버전과 화면 분위기가 많이 변했다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjk0/MDAxNjgxNDYzMDI0MzIz.RQLbV68Xw2Pw-4Wptq3PAIg14xbYFnXq5769JVz7DWgg._z79Bo47TfIuufKyOABThniiJz4Layx5OeSNEa2LGOEg.PNG.agapeuni/img.png?type=w80_blur)

​

몇 가지 리눅스 명령어를 입력해 보았다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTcy/MDAxNjgxNDYzMDI4NDM5.l6O1ewEGYph3VMXVx9SFkBN-E8zEWRv08gvYBYaxWSsg.06RdksVXmN1uJyuUwGG6TkSuqtoIq5BMQg4pyJdSq-Qg.PNG.agapeuni/img.png?type=w80_blur)

​

​

5\. 웹 콘솔

웹 브라우저에서 웹 콘솔로 접속하면 서버의 상태를 모니터링할 수 있고 웹 터미널로 접속할 수도 있어 편리하다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNzIg/MDAxNjgxNDYzMDMyNzY3.-wWejs5SKI0Pow8AnjXGiB2Iwwuf6dP4SMokKgdxGXgg.-TAN_9XEv3BdHfqEL5GXGRV6CBi1GL4IyE7VHS8esRog.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTA2/MDAxNjgxNDYzMDQwMDE5.9q3kEyvgq7RHo8eNCXtVK7FrZczCmkDV66PXqO0Rv1cg.WPpWZeA0i8NrFMj_RGYBSYzzy7HK7qMX3l4LAVQC4qsg.PNG.agapeuni/img.png?type=w80_blur)

​

​

![](https://blogfiles.pstatic.net/MjAyNjA2MTdfMTI4/MDAxNzgxNjIzNzc1NzA1.2QYwsPb7SzsAzNxbABqntGpXAscgNcqLRqQrRj6RQL0g.sS1rzJuq4-3ERN9qM8z69dPB5Y6mWd4F-WOitRfYhhEg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w1)

#리눅스환경 #인스톨러개발 #VMware #VMwareWorkstation #Fedora #Fedora서버 #가상환경설정 #가상머신 #리눅스설치 #소프트웨어테스트 #VMware설치 #Fedora다운로드 #ISO파일 #리눅스명령어 #웹콘솔 #서버모니터링 #웹터미널 #리눅스가상화 #리눅스서버 #Fedora33 #리눅스프로젝트 #소프트웨어개발 #리눅스팁 #VMware사용법 #가상환경개발 #Fedora설치과정 #리눅스테스트 #VMware평가판 #소프트웨어환경 #가상머신설정

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
