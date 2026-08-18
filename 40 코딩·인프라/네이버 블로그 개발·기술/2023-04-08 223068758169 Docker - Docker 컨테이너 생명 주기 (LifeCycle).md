---
title: "2023-04-08 223068758169 Docker - Docker 컨테이너 생명 주기 (LifeCycle)"
type: blog-archive
status: active
created: 2023-04-08
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223068758169&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223068758169
published: "2023. 4. 8. 19:16"
body_hash: ff41536151c24ef4ed6b7c305a60def3454fa9da3ba5b5dd8a353c5a73a891b2
visibility: private
rag: exclude
---
# 2023-04-08 223068758169 Docker - Docker 컨테이너 생명 주기 (LifeCycle)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223068758169&categoryNo=982
- 게시일: 2023. 4. 8. 19:16

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTlfMjA1/MDAxNzQ1MDExNDI5NDM2.N9KZCRENOTUfGIor8hgz2cWU5YXSrA2lmZNO3EVm5VMg.OVH05qitGpRCQvy8ihUX47lodkFB-9bmobGP_GeIVy0g.PNG/%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-001_\(7\).png?type=w80_blur)

​

도커 커맨드를 사용하여 컨테이너의 생명 주기를 확인해 보자.

​

1\. Docker 이미지 다운로드

원격의 저장소에서 이미지를 다운로드한다.

> docker pull centos:7

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMTEy/MDAxNjgwOTQ3NDA5MTUz.ZFBNu1y-cCIblAAMQRKv6GbjSoKQBp4yrEr03HUyB1Yg.bKHlcactbtbqrIwerGqyt4z2pMx2X_MTp91RVkUIY-kg.PNG.agapeuni/image.png?type=w80_blur)

​

2\. Docker 컨테이너 실행

다음의 명령어로 Docker를 사용하여 CentOS 7 이미지를 실행하고 인터랙티브한 쉘 세션을 제공한다.

> docker run -it --name test centos:7 bash

​

이 명령을 실행하면 Docker는 CentOS 7 이미지로 컨테이너를 생성한 후 해당 컨테이너에 대해 bash 쉘을 실행한다. 사용자는 이 쉘을 통해 컨테이너 내부에 접속하여 작업을 수행할 수 있다.

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMTY0/MDAxNjgwOTQ3NDg3MDE2.EV-KWHd3dok65Rv5zX3bUkORfpCZcOdy3uGGgi9LSgYg.7xOrK6GlGZhZl_SxLqfm_UYATHrxXe-tvb7Kj-tli38g.PNG.agapeuni/image.png?type=w80_blur)

​

여기서 각 옵션의 의미는 다음과 같다.

**> docker run -it --name test centos:7 bash**

docker run |  Docker 컨테이너를 실행하는 명령어  
---|---  
-it |  이 옵션은 터미널에 대한 상호 작용(interactive)을 가능하게 하고, 유지(persistent)한다.`-i`는 표준 입력(stdin)을 유지하고 `-t`는 tty(터미널)를 할당한다.  
\--name test |  실행 중인 컨테이너에 `test`라는 이름을 정의한다.이를 통해 해당 컨테이너를 나중에 식별하고 관리할 수 있다.  
centos:7 |  실행할 이미지의 이름과 버전을 지정. 여기서는 CentOS 7 이미지를 사용.  
bash |  컨테이너 내에서 실행할 명령어를 지정. bash 쉘을 실행하여 사용자가 컨테이너 내부에서 명령어를 실행하고 상호작용할 수 있도록 한다.  
  
​

3\. Docker 컨테이너 정지

다른 터미널에서 실행 중인 컨테이너를 정지시킨다.

> docker stop <컨테이너 ID or 컨테이너명>

> docker kill <컨테이너 ID or 컨테이너명>

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMTk1/MDAxNjgwOTQ3NjY2Njc0.CouZiPFs2TTfcpO2rM6MZB34zUXQGfeGom3KNiBXY-kg.3wFHftZp5QnAlv2F-2ckhqcthpKmBOpZ00H8icNtKZIg.PNG.agapeuni/image.png?type=w80_blur)

​

4\. Docker 컨테이너 재기동

정지 상태인 컨테이너를 재기동한다.

> docker start [옵션] <컨테이너 ID or 컨테이너명>

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMTkz/MDAxNjgwOTQ3NzIwNzc4.7X9enBFT-Wiud3x7mcalm0rW5QT5Stf4F8htq-ypLCog.CS80NTkR1kQWOMOhmV8Pnc-cpv2Tm6cGY7LVS5lSqmgg.PNG.agapeuni/image.png?type=w80_blur)

​

​

5\. Docker 컨테이너 커밋

도커 컨테이너를 실행하고 패키지를 업데이트했다. 패키지를 모두 업데이트 하는데 수분의 시간이 걸린다.

> docker run -it centos:7 bash 

# yum update -y

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMjY4/MDAxNjgwOTQ3ODY5OTg5.oc85OzLvNTaiMMJ40C1g0kMlQknp361vLiX8LaWw6ccg.MvXCR2akgqa6VldK9VRnQ1wf0O0dQy0LcpO7DGVUkPIg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMTEz/MDAxNjgwOTQ3ODgxMzI1.7wth896uJDzlO2xs4NuOzcyzs3rruG0yoiUo9TQE3Agg.y671ulafylG-Cz9_Fh70cHY0nSaCS5k2bdBwGNCzVWog.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyNDAyMTdfODMg/MDAxNzA4MTIxMzA3ODI0.ualqxO2dC1aUHEqBQ0n8HagmIXz9CWiVGzcoyX6QsbUg.krV7ujjPBJA3z-L93-YSGyh869NRiz8cKB7YHc0UblIg.PNG.agapeuni/image.png?type=w80_blur)

​

패키지 업데이트를 마친 현재 컨테이너를 이미지로 만든다.

> docker commit test centos:7-up

​

내려 받은 이미지와 생성한 이미지의 용량을 확인.

> docker images centos

​

도커 이미지를 다운로드했을 때는 용량이 204MB였다.

도커 이미지를 컨테이너로 실행하고 나서 패키지 업데이트 한 컨테이너를 이미지로 만들고 나니 용량이 546MB가 되었다.

​

​

6\. 원격 저장소에 보관

로컬의 이미지에 원격 저장소의 이름을 지정한다.

> docker tag centos:7-up agapeuni/centos:7-up

​

생성한 이미지를 원격 저장소에 저장한다.

> docker push agapeuni/centos:7-up

> docker push agapeuni/centos:7-up The push refers to repository [docker.io/agapeuni/centos] 6910a1121602: Pushed 174f56854903: Mounted from library/centos 7-up: digest: sha256:2b4a513a189089fe6b83eeb410fee20aecc854a57825e2cf88f8d8a8a2c16f36 size: 736 

​

도커 허브에 등록이 되었다.

![](https://postfiles.pstatic.net/MjAyMzA0MDhfMTIx/MDAxNjgwOTQ4OTQ5OTM2.EdpJh2mYt2U14Ji-icliSeejir0_Nr5zZ1vrdOCw2YUg.sxO3vJqOIDU6VLMfWX4rGVm6IVb-7cdcu0JPgyjpr08g.PNG.agapeuni/image.png?type=w80_blur)

​

7\. 컨테이너 제거

컨테이너를 삭제한다.

> docker rm <컨테이너 ID or 컨테이너명>

​

​

8\. 이미지 제거

이미지를 삭제한다.

> docker rmi <이미지 ID>

​

Docker Desktop에서 Delete 하는 게 좀 더 편리하다.

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Docker #도커 #컨테이너 #Docker명령어 #Docker이미지 #CentOS #DockerRun #DockerPull #DockerStop #DockerKill #DockerStart #DockerCommit #DockerPush #DockerHub #DockerRemove #도커이미지관리 #Docker컨테이너실행 #Docker커밋 #Docker저장소 #DockerLifecycle #Docker초보 #Docker기초 #도커컨테이너관리 #Docker삭제 #Docker업데이트 #도커이미지업로드 #DockerDesktop #Docker실행방법 #Docker환경설정 #컨테이너라이프사이클 #Docker용량관리

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
