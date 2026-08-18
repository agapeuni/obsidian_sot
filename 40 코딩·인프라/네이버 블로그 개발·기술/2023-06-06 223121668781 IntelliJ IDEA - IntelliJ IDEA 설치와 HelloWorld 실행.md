---
title: "2023-06-06 223121668781 IntelliJ IDEA - IntelliJ IDEA 설치와 HelloWorld 실행"
type: blog-archive
status: active
created: 2023-06-06
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223121668781&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223121668781
published: "2023. 6. 6. 16:26"
body_hash: 8aab6847cfeccbe2284f3408d3623cfa86c32e3d26bc18c59a544f8f62df3ea2
visibility: private
rag: exclude
---
# 2023-06-06 223121668781 IntelliJ IDEA - IntelliJ IDEA 설치와 HelloWorld 실행

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223121668781&categoryNo=982
- 게시일: 2023. 6. 6. 16:26

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTlfMTIy/MDAxNzQ1MDE0Mjk0NDY0.iFJZFmKZnokddwbXJ6jWlw0WyT8NvEG-EHpDj79RSAYg.Jm153ggcyWAN5hJCJPwAYnRGPQIEm5Jus-EYSMLx4ZEg.PNG/%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-001_\(11\).png?type=w80_blur)

​

1\. IntelliJ IDEA 개요

IntelliJ IDEA는 JetBrains사가 개발한 자바를 비롯한 다양한 프로그래밍 언어를 지원하는 통합 개발 환경(IDE)이다. 개발자들이 소프트웨어 개발을 더욱 효율적이고 생산적으로 수행할 수 있도록 돕는 도구다.

​

IntelliJ IDEA는 강력한 코드 편집기 기능을 제공하며, 코드 완성, 자동 서식 지원, 리팩토링 등을 포함한 다양한 코드 작성 도구를 제공한다. 또한, 강력한 디버깅 기능과 단위 테스트 도구를 제공하여 개발자가 코드를 테스트하고 디버깅하는 과정을 지원한다.

​

IntelliJ IDEA는 자바뿐만 아니라 Kotlin, Groovy, Scala 등 JVM 기반 언어를 지원하며, HTML, CSS, JavaScript 등 프론트엔드 기술과 XML, JSON 등 다양한 파일 형식을 지원한다.

​

​

2\. IntelliJ IDEA 설치

아래의 URL에서 IntelliJ IDEA Community Edition 버전을 다운로드할 수 있다.

<https://www.jetbrains.com/ko-kr/idea/download/#section=windows>

[ ![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fresources.jetbrains.com%2Fstorage%2Fproducts%2Fintellij-idea%2Fimg%2Fmeta%2Fpreview.png%22&type=ff500_300) ](https://www.jetbrains.com/ko-kr/idea/download/#section=windows) [ **최고의 Java 및 Kotlin IDE인 IntelliJ IDEA를 다운로드하세요** Windows, macOS 또는 Linux용 최신 버전의 IntelliJ IDEA를 다운로드하세요. www.jetbrains.com ](https://www.jetbrains.com/ko-kr/idea/download/#section=windows)

​

IntelliJ IDEA Community Edition 버전은 오픈 소스여서 무료로 사용이 가능하다.

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjk3/MDAxNjg2MDMyODg4NjA5.EoeSIXLESsMOq3F-bDeFAkRCrd11w3Zdo6B-w5Llzcog.tWngTZzJH1vfZ9LjlCC3K-MVYpmd8qjmqLHhgZ0zTV4g.PNG.agapeuni/image.png?type=w80_blur)

​

다운로드한 "ideaIC-2023.1.2.exe" 인스톨러를 실행하여 설치한다.

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMTQ3/MDAxNjg2MDMzNTcyNjc0.HJubU7VemL8amKFHsTVt2OtiRDq4j4raB1zqhe-_dhgg.PHeEiX2YnnavyjlWWp_FZ4QakvMXecH7etxMUTLHZXQg.PNG.agapeuni/image.png?type=w80_blur)

​

"Next >"를 클릭하여 설치를 진행한다.

Destination Folder를 다음과 같이 변경했다.

기본경로 : C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2023.1.2

설치경로 : D:\dev\IntelliJ

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjUz/MDAxNjg2MDMzNjIwNjUw.9CQX0zXS0cPu6UOwh5zE3i-6zTEREk77CY-xHNYVqqAg.tMVgCahimwR0JsTGEkQ6nnmfOQHLCO3yfqm-LstWDsUg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjM1/MDAxNjg2MDMzNzU5OTY3.RQ_ZQnVNCgabf3XkUpVPlzHwinST9fOhkryYiSADtbcg.EmHxcKGoXaqNtRDhnaB42J5ufZL0cwTNi5lufhkGYKIg.PNG.agapeuni/image.png?type=w80_blur)

​

자주 사용할 IDE는 아니라서 아무것도 선택하지 않고 "Next >"를 클릭한다.

![](https://postfiles.pstatic.net/MjAyMzA2MDZfODIg/MDAxNjg2MDMzNzY5MjU2.pKlzXw-txqOh_YXt_I77ClQj0Ma_jbGMwnLbSzCx1cgg.Rep2ThDGwkIkwI6DpJ8VzZRJd0aLSN6TAAab5QFDB4Ug.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjE3/MDAxNjg2MDMzODIxNzEw.tXJSn6O4rnxDI2US5fjSGAXwBst14PetzEU1Curab8cg.kN5vK9akKhfQt5s5r9StW5hZhVWq46Qbi0gNHZW2_ygg.PNG.agapeuni/image.png?type=w80_blur)

​

설치가 완료되어 바로 실행하도록 "Run IntelliJ IDEA Community Edition"을 체크했다.

![](https://postfiles.pstatic.net/MjAyMzA2MDZfNzkg/MDAxNjg2MDMzOTQyNTY2.NH4s7Xxh61ASt2vTVxxbUWYjZCeXPLJQ6vtUbAdorhUg.i2fSEYC5kOJG3PZFI_iinJYnDQQANnbp0QAC6Z2v4cEg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjkw/MDAxNjg2MDM0MzA4NjAx.YOWgTZG2BFbFjIuPEHlOymMd5JZd7Nd8hyk_OxBuNo8g.QidS_0ZxDiPqo6UfQydGQ33xXJNiWOWnA2ICGSgOYgUg.PNG.agapeuni/image.png?type=w80_blur)

​

​

3\. IntelliJ IDEA 실행

첫 실행시 한번 표시된다. User Agreement를 확인하고 Data는 보내지 않는 것으로 선택했다. 

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjc1/MDAxNjg2MDM0NDI4MTgz.w2fKgQJN8wzyZB92pTTZJ2Obk9KKjeOsITXiTg-2Tk4g.wL5HauK98oJ52Hw2i34v7QVXUxyOoAg-OWlcsHIUCvYg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMTEg/MDAxNjg2MDM0NDQ3NzQ2.4LZkUsm3N7wDyRKVT5A2iU04BHXTiyD5fJ6FzlBFvRYg.KDDifVaG8CzRR0XCKjw8y_XqUBVv8-thJJyq04em_pog.PNG.agapeuni/image.png?type=w80_blur)

​

그럼 HelloWorld 프로젝트를 생성해 보자.

New Project를 선택

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjk5/MDAxNjg2MDM0NTg1MTM1.8v88CGB_KbIZobP3rEig4JRCETUFKegOFXtFqGUXcZIg.w_bUJ8G5CZIVYIHC_pk3kLn7T2yWzf6HAvfhJEWNv4Qg.PNG.agapeuni/image.png?type=w80_blur)

​

프로젝트 정보는 다음과 같이 입력/선택하고 생성하였다.

﻿이름 : HelloWorld 위치 : D:\dev\IntelliJ\workspace 언어 : Java 빌드 : Maven JDK : Oracle OpenJDK 17 Add sample code 선택 

![](https://postfiles.pstatic.net/MjAyMzA2MDZfODkg/MDAxNjg2MDM1OTQ1Nzky.ODC7-tiAUld7iQufk4QZgbd-d3z5KX1UxkeEgh8JsTAg.D42uDap4jIWvorQ6gEPLMOk8mQgr_s0yKBXKoeVMOnwg.PNG.agapeuni/image.png?type=w80_blur)

​

File - Settings 메뉴를 선택해서 Settinsg 창을 연다.

테마는 Darcula가 너무 어두워 IntelliJ Light로 변경하고, 폰트는 프로그래밍 할 때 눈에 익숙한 나눔고딕코딩 폰트로 변경한다. 

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjUy/MDAxNjg2MDM4MjkwODk0.gifVGwoEdS-qYT4C_jpFsK88zbvuBPH7VuFbKGnbuj4g.yeDdKj2vdeei-gGWp53bia2FyuvioOa_vTpKTgb_7x8g.PNG.agapeuni/image.png?type=w80_blur)

​

자동으로 생성된 Main 클래스를 바로 실행(Shift + F10)을 해본다. 

다른 개발자는 IntelliJ가 좋다고 해서 한번 설치해 보았는데 이클립스에 너무 길들여져 있어 하나씩 적응해 나가야 한다.

![](https://postfiles.pstatic.net/MjAyMzA2MDZfMjUw/MDAxNjg2MDM4NDUyNjU5.c6XVOzGNL8TROrDm4Si_DefPDijuspLUr1P-ODCm4XMg.r_UZpqG2Jhym_p1ZXwKOIYYzcAzJgGnGKcRSUenL4Z8g.PNG.agapeuni/image.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#인텔리제이 #IntelliJIDEA #JetBrains #자바개발 #Kotlin개발 #통합개발환경 #IDE #코드편집기 #코드완성 #리팩토링 #디버깅 #단위테스트 #JVM기반언어 #Scala #Groovy #프론트엔드개발 #HTML #CSS #JavaScript #XML #JSON #IntelliJ설치 #커뮤니티에디션 #무료IDE #Maven프로젝트 #OpenJDK #다크테마 #라이트테마 #나눔고딕코딩 #헬로월드프로젝트 #코드작성 #소프트웨어개발

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_​_

 _공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
