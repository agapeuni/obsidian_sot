---
title: "2023-05-13 223101084899 우분투 오류 - Waiting for cache lock Could not get lock"
type: blog-archive
status: active
created: 2023-05-13
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223101084899&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223101084899
published: "2023. 5. 13. 15:51"
body_hash: 5f199d50c8db7bb0b48e43f86c200bd0df4ebf947635ef1e28306e2c3dab062f
visibility: private
rag: exclude
---
# 2023-05-13 223101084899 우분투 오류 - Waiting for cache lock Could not get lock

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223101084899&categoryNo=982
- 게시일: 2023. 5. 13. 15:51

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfMTI5/MDAxNzQ0MjI0MzUzMjY1.V5CSxtBpoPZgWUNZ0iiGVc29VhnUVOimus45y-PmTVAg.h27jBPHsqT4xXxN1JhhGrEN7uIYp8Csh8cRwAVrhy74g.PNG/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-001_\(8\).png?type=w80_blur)

​

1\. 문제(Problem)

우분투에서 OpenJDK를 설치하려고 다음의 명령을 실행했다. 

$ sudo apt install openjdk-18-jre-headless

​

그런데 아래의 오류가 반복된다.

"Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend." 

oneway:~$ sudo apt install openjdk-18-jre-headless Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr) Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 7381 (unattended-upgr)... 20s

​

2\. 원인(Cause)

구글링 해보니 lock 파일이 있으면 우분투 패키지 업데이트를 막는다고 한다.

/var/lib/dpkg/lock 파일이 생겨 패키지 및 인덱스 정보를 업데이트하지 못하는 현상이다.

![](https://postfiles.pstatic.net/MjAyMzA1MTNfMTY2/MDAxNjgzOTU5NjUxNzg3.1q5PU5M8i3nYBLpTnwYdM35-Hsj_hAchsQ0K9kOAzjcg.nNcjBnzt-jbNJmaA67jZEyFWMSodL2BC1C0Rkmwbpugg.PNG.agapeuni/img.png?type=w80_blur)

​

3\. 해결(Solution)

잠긴 캐시 파일을 삭제하면 된다.

다음의 명령을 순차적으로 실행한다.

$ sudo rm /var/lib/apt/lists/lock $ sudo rm /var/cache/apt/archives/lock $ sudo rm /var/lib/dpkg/lock* $ sudo dpkg --configure -a $ sudo apt update

​

![](https://postfiles.pstatic.net/MjAyNjA2MTdfMTI4/MDAxNzgxNjIzNzc1NzA1.2QYwsPb7SzsAzNxbABqntGpXAscgNcqLRqQrRj6RQL0g.sS1rzJuq4-3ERN9qM8z69dPB5Y6mWd4F-WOitRfYhhEg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w80_blur)

#우분투 #OpenJDK #apt #패키지관리 #잠금문제 #캐시잠금 #리눅스오류 #시스템관리 #Linux #문제해결 #APT잠금 #리눅스명령어 #패키지설치 #명령줄 #시스템유지보수 #우분투문제 #apt업데이트 #우분투팁 #소프트웨어설치 #리눅스해결법 #개발자 #프로그래밍 #LinuxTips #오픈소스 #프로그래밍문제 #리눅스기초 #시스템관리자 #DevOps #소프트웨어개발 #LinuxTroubleshooting #우분투튜토리얼

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
