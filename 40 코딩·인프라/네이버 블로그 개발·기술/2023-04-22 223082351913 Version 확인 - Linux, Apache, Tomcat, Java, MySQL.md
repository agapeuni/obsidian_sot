---
title: "2023-04-22 223082351913 Version 확인 - Linux, Apache, Tomcat, Java, MySQL"
type: blog-archive
status: active
created: 2023-04-22
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223082351913&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223082351913
published: "2023. 4. 22. 19:51"
body_hash: 002802d741e7214ac7a9a9e05cf3a9c20e80da64ed329349be5b4d8db15517a6
visibility: private
rag: exclude
---
# 2023-04-22 223082351913 Version 확인 - Linux, Apache, Tomcat, Java, MySQL

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223082351913&categoryNo=982
- 게시일: 2023. 4. 22. 19:51

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfMTc4/MDAxNzQ0MjIzODYzMzQy.807zC_Z7tGwAsXV_hXrGUi5Vjyv0wnDBrgPnY2KBcjog.jS_mM8-f5mTQyPq_eNHqXl7LllAtz9up5TWcPv5NmIwg.PNG/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-001_\(3\).png?type=w80_blur)

​

1\. 프로그램 버전

리눅스에서 개발하다 보면 사용하고 있는 프로그램의 버전을 확인해야 할 때가 종종 있다. 

다음과 같이 Linux, Apache, Tomcat, Java, MySQL 순서로 버전 확인하는 방법을 정리해 본다.

![](https://postfiles.pstatic.net/MjAyMzA0MjJfMjA5/MDAxNjgyMTYwNDMzNjQx.Rs2eL9oXFFP0l32anBlhWzoPN0mHGEi8nST04hljCrMg.u54j2HWz2GdvRzmNJ-uVQKKDtIuXYONT_eLsdTFj4Ekg.PNG.agapeuni/img.png?type=w80_blur)

[이미지 출처] <https://www.geeksforgeeks.org/introduction-semantic-versioning/>

​

​

2\. 리눅스(Linux) 버전 확인

아래와 같이 명령어를 입력하면 현재 사용 중인 리눅스 버전을 확인.

> uname -a

또는

> cat /etc/issue

​

​

3 아파치(Apache) 버전 확인

아래와 같이 명령어를 입력하면 현재 사용 중인 Apache의 버전을 확인.

> cd [Apache Path]

> cd bin

> ./httpd -v 

​

​

4\. 톰캣(Tomcat) 버전 확인

아래와 같이 명령어를 입력하면 현재 사용 중인 Tomcat 버전을 확인.

> cd [Tomcat Path]

> cd bin

> ./catalina.sh version 

​

5\. 자바(Java) 버전 확인

아래와 같이 명령어를 입력하면 현재 사용 중인 JAVA 버전을 확인.

> java -version 

​

​

6\. MySQL 버전 확인

아래와 같이 명령어를 입력하면 현재 사용 중인 MySQL 버전을 확인.

> mysql -V

​

SQL 쿼리로 확인할 수도 있다.

> SELECT VERSION()

​

​

7\. 윈도우(Windows) 버전 확인

Win 키와 R을 입력하면 실행 창에 열린다. 실행 창에서 winver를 입력하면 Windows의 버전을 확인할 수 있다.

![](https://postfiles.pstatic.net/MjAyMzA0MjJfMjA4/MDAxNjgyMTYwNTI5MTcw.dpZYXi9UNmRr-H92yj_BUHkZBnk80_XFdk0vpvkSr1gg.qCiEEDe6BmryLTttboMtzID9leO2cx3d97JTOC5V0Xsg.PNG.agapeuni/img.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA0MjJfNTkg/MDAxNjgyMTYwNTMzMzAz.VmxfaGAbmlkaludBpUDtIUFnbaaDwvPwmrNKZMzvy9Qg.r43yCXFTsTcrbylq41AisyHtiaHy98_nvasCAjkQjQsg.PNG.agapeuni/img.png?type=w80_blur)

​

명령창에서 systeminfo를 입력한다.

> systeminfo

![](https://postfiles.pstatic.net/MjAyMzA0MjJfMTMy/MDAxNjgyMTYwNTQxMDI4.0kmrNhFcukEHi87aifflIlPPHqHWfXufycBFtK1rPJsg.5dIFJX84s-Hvei4lWBmfN56F0hEcVzLu0U68jO1D5mcg.PNG.agapeuni/img.png?type=w80_blur)

​

명령창에서 ver를 입력한다.

> ver

C:\WINDOWS\system32>ver Microsoft Windows [Version 10.0.19044.2486]

​

![](https://blogfiles.pstatic.net/MjAyNjA2MTdfMTI4/MDAxNzgxNjIzNzc1NzA1.2QYwsPb7SzsAzNxbABqntGpXAscgNcqLRqQrRj6RQL0g.sS1rzJuq4-3ERN9qM8z69dPB5Y6mWd4F-WOitRfYhhEg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w1)

#리눅스 #Linux버전확인 #Apache버전확인 #Tomcat버전확인 #Java버전확인 #MySQL버전확인 #프로그램버전 #버전확인방법 #서버관리 #명령어 #LinuxCommands #시스템관리 #운영체제 #소프트웨어버전 #LinuxVersion #서버운영 #MySQL #SQL쿼리 #윈도우버전확인 #윈도우 #Windows버전 #SystemInfo #ver #WindowsCommands #서버개발 #서버배포 #개발환경 #DevOps #IT #프로그래밍

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
