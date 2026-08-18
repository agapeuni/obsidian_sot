---
title: "2014-07-21 220067224112 라즈베리 파이 - RPi Control Center (Raspcontrol)"
type: blog-archive
status: active
created: 2014-07-21
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=220067224112&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 220067224112
published: "2014. 7. 21. 18:34"
body_hash: f8283aa4a6269a45565ca127ac4494ff3cbd353118407940a62723112afe0a2f
visibility: private
rag: exclude
---
# 2014-07-21 220067224112 라즈베리 파이 - RPi Control Center (Raspcontrol)

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=220067224112&categoryNo=982
- 게시일: 2014. 7. 21. 18:34

## 본문

![](https://postfiles.pstatic.net/MjAyNTA5MjFfMTUx/MDAxNzU4NDM3NTkyMzI4.24TOcdCHCNx5q4IHPRpKx7qjfTyfEtEcNbeoQBYGU7Yg.Zz4QmVvO1LKSMM6HIcGXaCakA_wZlklSAhT593mfyosg.PNG/%EB%9D%BC%EC%A6%88%EB%B2%A0%EB%A6%AC-%ED%8C%8C%EC%9D%B4-001_\(8\).png?type=w80_blur)

**​**

**라즈베리 파이**(Raspberry Pi)에 모니터링 툴인 Raspcontrol 를 설치해 봅니다. 

Apache와 PHP, Git 에 대해서 어느정도 경험이 있는 것을 전제로 합니다.

​

먼저 파이(172.30.1.3)에 SSH 로 접속해서 로그인 합니다. 

/var/www 폴더로 이동한 뒤 Raspcontrol을 다운받습니다.

**$ cd /var/www**

**$ git clone**[**https://github.com/Bioshox/Raspcontrol.git**](https://github.com/Bioshox/Raspcontrol.git)**raspcontrol**

![](https://postfiles.pstatic.net/20150605_82/agapeuni_1433463351805HGd9E_PNG/20140718_231723.png?type=w80_blur)

그리고 나면 raspcontrol에 다음과 같이 파일들이 생성이 됩니다.

![](https://postfiles.pstatic.net/20150605_264/agapeuni_14334633680075YSKK_PNG/20140718_231729.png?type=w966)

​

다음의 명령으로 /etc/raspcontrol 폴더와 database.aptmnt 파일을 생성합니다.

**$ sudo mkdir /etc/raspcontrol**

**$ sudo nano /etc/raspcontrol/database.aptmnt**

![](https://postfiles.pstatic.net/20150605_62/agapeuni_1433463377949qYcHz_PNG/20140718_231932.png?type=w80_blur)

database.aptmnt 파일에는 화면과 같이 사용자ID와 비밀번호를 입력합니다.

**{**

**"user": "pi",**

**"password": "pi"**

**}**

![](https://postfiles.pstatic.net/20150605_49/agapeuni_1433463386627RJkCH_PNG/20140718_232238.png?type=w80_blur)

​

그리고 database.aptmnt 파일에 접근권한을 644로 설정하여 둡니다. 

![](https://postfiles.pstatic.net/20150605_256/agapeuni_1433463395353Ncr5r_PNG/20140718_232240.png?type=w80_blur)

웹 브라우저를 열고 [http://IP주소/raspcontrol/](http://%EB%9D%BC%EC%A6%88%EB%B2%A0%EB%A6%AC%ED%8C%8C%EC%9D%B4%EC%9D%98_IP_%EC%A3%BC%EC%86%8C/Raspcontrol/%EC%97%90%C2%A0%EC%A0%91%EC%86%8D%ED%95%A9%EB%8B%88%EB%8B%A4.%C2%A0%EB%9D%BC%EC%A6%88%EB%B2%A0%EB%A6%AC%C2%A0%ED%8C%8C%EC%9D%B4%EC%9D%98%C2%A0IP%C2%A0%EC%A3%BC%EC%86%8C%EB%8A%94%C2%A0ifconfig%C2%A0%EB%AA%85%EB%A0%B9%EC%9D%84%C2%A0%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC%C2%A0%ED%99%95%EC%9D%B8%ED%95%A0%C2%A0%EC%88%98%C2%A0%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4.)에 접속합니다. 라즈베리 파이의 IP 주소는 ifconfig 명령을 사용하여 확인할 수 있습니다. Raspcontrol 웹 페이지에 접속하면 라즈베리 파이의 시스템 정보와 리소스 사용량 등을 볼 수 있을 것입니다. 다만, Raspcontrol은 오래된 프로젝트로, 최신 라즈베리 파이 모델과 운영 체제 버전에서는 동작하지 않을 수도 있습니다. 

​

브라우저에서 파이로 다음과 같이 접속을 합니다. 먼저 입력해둔 사용자ID와 비밀번호를 입력합니다. 

![](https://postfiles.pstatic.net/20150605_276/agapeuni_1433463404538h1oru_PNG/20140718_232259.png?type=w80_blur)

첫 화면에는 아래와 같이 표시됩니다. 

![](https://postfiles.pstatic.net/20150605_256/agapeuni_14334634139729pEBQ_PNG/20140718_232547.png?type=w80_blur)

항목을 클릭하면 상세페이지로 이동합니다.

System, Uptime, RAM, CPU, Storage, Network 정보가 표시됩니다. 

![](https://postfiles.pstatic.net/20150605_115/agapeuni_14334634227492hByk_JPEG/20140718_232549.jpg?type=w80_blur)

디스크 정보도 표시됩니다. 

![](https://postfiles.pstatic.net/20150605_70/agapeuni_1433463431703l7Dj8_PNG/20140718_233434.png?type=w80_blur)

​

![](https://postfiles.pstatic.net/MjAyNjA2MTdfMjUy/MDAxNzgxNjI0NzY3NjI1.AXfH5g_3LU4D357Hb1mo8fXKnr1zMpmXHyyN6VQ-YIQg.FMBXh3VY95SqPKpZt9S_IMr5v4gTkwQ_zT0pFQpdx3cg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#라즈베리파이 #RaspberryPi #라즈베리파이모니터링 #Raspcontrol #라즈베리파이웹서버 #라즈베리파이Apache #라즈베리파이PHP #라즈베리파이Git #라즈베리파이SSH #라즈베리파이설치 #라즈베리파이활용 #라즈베리파이시스템관리 #라즈베리파이리소스모니터링 #라즈베리파이CPU #라즈베리파이RAM #라즈베리파이네트워크 #라즈베리파이스토리지 #라즈베리파이웹관리 #라즈베리파이튜토리얼 #라즈베리파이초보자 #라즈베리파이프로젝트 #라즈베리파이학습 #라즈베리파이교육 #라즈베리파이응용 #라즈베리파이리뷰 #라즈베리파이추천 #라즈베리파이IT #임베디드시스템 #STEM교육 #메이커프로젝트

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
