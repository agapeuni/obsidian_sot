---
title: "2023-04-14 223074841359 데비안 설치 - VMware Workstation Pro 에서 Debian 설치"
type: blog-archive
status: active
created: 2023-04-14
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223074841359&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223074841359
published: "2023. 4. 14. 20:34"
body_hash: f8b60e1baea46bbcf5e81ae1b77eaffe62a09db9b5a197dd85c7e748e999f2fe
visibility: private
rag: exclude
---
# 2023-04-14 223074841359 데비안 설치 - VMware Workstation Pro 에서 Debian 설치

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223074841359&categoryNo=982
- 게시일: 2023. 4. 14. 20:34

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTBfMTQ4/MDAxNzQ0MjIzNzYwMDIz.-jJaiClVL-q6OXh4PiGA8yxX0SheV98OU_RiNie10aAg.pxFXP8lQDfwFH3WZAvNZqXIJXXv4reouGloW_ciBPLcg.PNG/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-001_\(2\).png?type=w80_blur)

​

1\. Debian 다운로드

Debian 홈페이지를 방문했는데 처음엔 디자인 퀄리티가 낮아서 해적 사이트인 줄 알았다. 

가만히 살펴보니 공식페이지가 맞다.

​

<https://www.debian.org/>

[ **데비안 -- 범용 운영체제** 커뮤니티 데비안은 사람들의 커뮤니티입니다! DC22 Group Photo Mini DebConf Regensburg 2021 Screenshot Calamares Installer 데비안은 스위스 군용 칼 같습니다 사람들이 데비안과 함께 재미있게 지냅니다 사람들 우리는 누구이며, 어떤 일을 하는가 철학 우리는 왜 데비안을 하며, 어떻게 하는가 참여 및 기여 참여하는 방법! 더 많은 정보... 데비안 커뮤니티에 대한 추가 정보 운영체제 데비안은 완전한 자유 운영체제입니다! 다운로드 왜 데비안인가 무엇이 데비안을 특별하게 만드는가 사용... www.debian.org ](https://www.debian.org/)

​

안심하고 Debian 설치파일을 다운로드했다.

파일 : debian-10.7.0-amd64-netinst.iso

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjgz/MDAxNjgxNDcxODg1MDg5.IWAVxRf1AnF66tc1xOkqCXoK3RB-Y0W8_xm-lDN2AQ8g.fSRjD6IBzVWd1AblDlGUIbgSBPFIUiZddngMzuaTJoIg.PNG.agapeuni/img.png?type=w80_blur)

​

2\. VMware 설정

VMware Workstation Pro 16에서 New Virtual Machine 메뉴를 선택하여 Wizard를 실행한다.

Typical (remommended) 선택을 그대로 두고 Next 버튼을 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjY0/MDAxNjgxNDcxODkzNDI2.9yx9X9UIcTt0eDgudGtVILdjSqJD4GMp9yjl2r8Q6Kog.82PeEE4ZQqRBts7nvX-qPyUcmdmGB5YLrMOnbXHyiyQg.PNG.agapeuni/img.png?type=w80_blur)

​

다운로드한 설치 파일 "debian-10.7.0-amd64-netinst.iso"를 선택하고 Next 버튼을 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjk4/MDAxNjgxNDcxODk3MzI3.glYiN_Ers8973uNotu0EbDhfd9Rt_E19kxVN3YbLOrwg.L7vd1UqpG6Tm_n0UKpNEkeUjD93Yq2cDRMfRAWHJ9b8g.PNG.agapeuni/img.png?type=w80_blur)

​

Location을 선택하고 Next 버튼을 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTEz/MDAxNjgxNDcxOTAxMjM2.DBkC0pGaP7f9MpbiQsoi6gv0W3oI0DEB48cm8uyHbucg.mIK1OkPc_DE7r6nFcsPEfNdVPxxnqG2aFyGyFgAnDwAg.PNG.agapeuni/img.png?type=w80_blur)

​

Maximum disk size (GB)는 20으로 하고 Split virtual disk into multiple files를 선택하고 Next 버튼을 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTc2/MDAxNjgxNDcxOTA4MDQx.Lqq-n_qcFJ77h-9CwghfcstQEC5gRptQSP53myAH1HQg.Cnf3v_tLAdEQEk36Yxjc2OOhYFVVpqWO8a3-Clapfo4g.PNG.agapeuni/img.png?type=w80_blur)

​

Hardware에서 USB Controller, Sound Card, Print는 사용하지 않으므로 선택하여 Remove 버튼으로 제거.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTA5/MDAxNjgxNDcxOTExODI1.uid-iESt9iDC-i5dK2cRliiTNGqvXoNuk2g4Hhaq0YYg.R-IEaYlKoa3U0PkJ-xv4caqmLnnzL-QGQGrgjNDpTrYg.PNG.agapeuni/img.png?type=w80_blur)

​

불필요한 Device를 제거하고 남겨진 Device 목록.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNTcg/MDAxNjgxNDcxOTE2MTgy.ce1XCM6z0nFiRBt-vLxdmKW4pfcg2Uw9c6cStcYVFzAg.m05tmBlXNW8F-C3Agw-Ugqp_LugX6Tr2L6PbIT7uTbQg.PNG.agapeuni/img.png?type=w80_blur)

​

3\. Debian 설치

설치는 Graphical install을 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjc1/MDAxNjgxNDcxOTIwMjU0.ZC8bgMwhiwazQmPEjWzb4Jw8ohIze-PsFzUgHjnxi9Ig.QzVf9k22l9Mto5f2_LQqOVSQ_3O7NaT4dvbONn2Qai4g.PNG.agapeuni/img.png?type=w80_blur)

​

설치 언어는 "Korean - 한국어"를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfOTMg/MDAxNjgxNDcxOTI0MTgz.AnQFR5O0rB56R3DTsPp0cZ84mcrPYuCgPjaQ2rmaROkg.HrCJp1DqnLa4YX_BLsQfINCBt3owFvEk6lrVUGrW4Kcg.PNG.agapeuni/img.png?type=w80_blur)

​

위치는 국가나 지역을 말하며 "대한민국"을 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTcg/MDAxNjgxNDcxOTI4NTg5.MaV77n5E1eXw2Fz5LNxOZlJVT0StBW_r5pYae5leOg0g.z50X1n_1EooZTyBc85M7RcEDRVpuGfexjVAkwWELS2wg.PNG.agapeuni/img.png?type=w80_blur)

​

키보드 설정은 "한국어"를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjE4/MDAxNjgxNDcxOTMyOTI2.rO0yRfqKDrkjYLBprvaF482--9tdQx01RYhhV7wyYr8g.12vIcNyq8sLOUoR-INWxc4CDPxSAvkRA-_PE-9jNNVUg.PNG.agapeuni/img.png?type=w80_blur)

​

CD에서 설치할 프로그램 읽어들이기.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTMy/MDAxNjgxNDcxOTM2Njkx.0pWVlDdISQkug07SPxsVvd7zNgWv4uU32b6p71-oa4gg.pFCgX7soKBqWFNN-sIPPqqsyDGJVIsmsYXR4dOHUMPsg.PNG.agapeuni/img.png?type=w80_blur)

​

네트워크 설정은 자동진행.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjk2/MDAxNjgxNDcxOTQyODAy.79rDorrTa3m-MeyPLR_Ny4VmLi31u-ngSxoYYDeQ8tog.CFa1711o36cZzGvxrD_ENsNPXBEk0xKsa30BtOlXMFQg.PNG.agapeuni/img.png?type=w80_blur)

​

호스트 이름을 입력. 기본값 "debian"을 그대로 두고 "계속"버튼 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjkx/MDAxNjgxNDcxOTQ3ODk2.r2XbZa7IhClA77LS-0iKFslDY_n6WsSWiosbNFrkvG0g.MzJEbSe4LgKPm8r1-VKpxgX0hfuRv8lzVb-UG48epA0g.PNG.agapeuni/img.png?type=w80_blur)

​

도메인 이름이나 인터넷 주소를 입력. 없으면 공백으로 두고서 "계속" 버튼 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTI1/MDAxNjgxNDcxOTUxNzk3.Gg_SeHATdO_1Dwyj9io8p6TcMAaJy2ikORccbEllX20g.a-ld5lCHla3WOow2bZgfz2lseE_Unk_3mpjnB5Xox_4g.PNG.agapeuni/img.png?type=w80_blur)

​

시스템 관리자인 root 암호를 입력. 기억하기 쉽게 입력.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfOSAg/MDAxNjgxNDcxOTU1ODY4.Ec32Mvac2jAPN7kraDHJGo4IWNwOnoG8frFLkd2rRQAg.nsRu2OT85zOF6zqNsX_aWCsex0JQGHlYVLNxtsIIsoQg.PNG.agapeuni/img.png?type=w80_blur)

​

일반 사용자의 이름을 입력.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNjkg/MDAxNjgxNDcxOTYwMTE5.unLL_YpP1vQ0_Opzdxj4XL0VbUbWHuWDo2KVe8OhRRkg.i1hq6-EwhSfio-lB361CSrot9uZriEaKrVuhtghKDOQg.PNG.agapeuni/img.png?type=w80_blur)

​

사용자 계정(ID)을 소문자로 입력.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTkw/MDAxNjgxNDcxOTY0MDUy.VuAuxDNRCrHj2z0TGjdAvHOBtyarGL2qdULL7-I0LlMg.vY85P9SujFKizecVt3Hc0oAFDmuR4k3m2zxmYpPy-Dkg.PNG.agapeuni/img.png?type=w80_blur)

​

사용자 계정의 암호 입력. 기억하기 쉬운 암호를 입력.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTc4/MDAxNjgxNDcxOTY3NzAw.nBat4edTLmKrejP93k2ipNnYXKrhTfoMYdOAQEfAgycg.0AFpBVRANAtLwImxAnd0-lx93HdVSBqNo9t5DMolg-cg.PNG.agapeuni/img.png?type=w80_blur)

​

디스크 파티션 위치를 설정.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfNjYg/MDAxNjgxNDcxOTcxNjUy.YVKJkyCdfRw0rBdzagXO2xVHlpH2IDwEgxNz-MRf81Eg.-_w9ybCIEBIqUbviPgVc4rwWUhE8YHyYIiNQT6s2pzcg.PNG.agapeuni/img.png?type=w80_blur)

​

LVM 설정을 하면 디스크의 다양한 유연성을 제공함.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjE4/MDAxNjgxNDcxOTc0ODg0.PLykJ3_9mZfJTDCeJtRhev-6J4TVUfWtgaZyN-7218Qg.RnblIaZezQLRZGhUfXITsBS5MUE3i3-gvvfMoij30hYg.PNG.agapeuni/img.png?type=w80_blur)

​

파티션 할 디스크를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTYz/MDAxNjgxNDcxOTc4MTgx.m_1UJpnB3UZKBCVxCJjYd_XbRRLLRTqa-O42V4ROfRYg.1lUTaUhL---0EqVZChM6rIt9NFwt5XbIU7FRpXUzwnMg.PNG.agapeuni/img.png?type=w80_blur)

​

/home, /var, /tmp 파티션을 분리하지 않으면 모두 한 파티션에 설치.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTMw/MDAxNjgxNDcxOTgxNDcz.bPDA2GeJHXa_jkHRpDKESJrGwOrKuvzxXWcKSTju7Gkg.r7QVfxtp8AigRdsiqQNAsI-zrUWRXhMboVgVRMBSE5Yg.PNG.agapeuni/img.png?type=w80_blur)

​

LVM 설정을 결정.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjA5/MDAxNjgxNDcxOTg0NzMz.8gFpDsLcFY7wgZZhKOTgv1TU4coNIYgbxJVuVvm87-Ug.rXS9WKiTkfFirXNAoGMRAoBl8DEqeWmRBRlwVXeFq3Mg.PNG.agapeuni/img.png?type=w80_blur)

​

파티션으로 사용할 볼륨 그룹의 크기 설정. "max"로 입력하면 최대 크기 설정.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjky/MDAxNjgxNDcxOTg4MDc1.mxEPwNGr30Dt4ljDf-wbiOSomawU3t4FibfEGzj9zFUg.l0SeYmfRMiC2eORvZVLC8cCd9jBHhdk777MRnxBDW_sg.PNG.agapeuni/img.png?type=w80_blur)

​

디스크에 쓰기. "예"를 선택

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTUz/MDAxNjgxNDcxOTkyNTA4.m4lHxbgljsTEdwf_QIlV2l7tU16Ak-seY8RlCnNTm_gg.KlRTSv0jVuNpWFUB4nB6nQJ3Fc4QtPIHKwcnQXuwc_Qg.PNG.agapeuni/img.png?type=w80_blur)

​

기본 시스템이 디스크에 설치.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTMy/MDAxNjgxNDcxOTk1NjM0.7WHSUuXbuW5eC2aLnHUJzf7yYsnTQNoBvgbYotUt3pog.Ljo92X00nKMkmP2wiY36XEgMarPvhU4SmVs9RMc1KQgg.PNG.agapeuni/img.png?type=w80_blur)

​

그냥 "아니요"를 선택.

CD나 DVD에서 소프트웨어를 추가하려면 "예"를 선택하면 된다.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjMz/MDAxNjgxNDcxOTk5MjM0.aHI2MFKkVFrEdabd40Bm8wm0lm5i_IHMPODX4DCocN8g.qADJM3a2rNKqpf5MM0sWu-4aewlXsB5liwOLg0U_rZ4g.PNG.agapeuni/img.png?type=w80_blur)

​

미러사이트 국가 설정. "대한민국"을 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjkz/MDAxNjgxNDcyMDAyNzY3.MVg4RHU1qjSo1OuPHEvPoU9pV8JwvAxeS2QNhmxsvBUg.3X1GFXI25ppmgl4Keew8vUNUqjGLlLZDD7SMjl71bYAg.PNG.agapeuni/img.png?type=w80_blur)

​

미러사이트를 설정. "deb.debian.org"를 선택

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjgz/MDAxNjgxNDcyMDA2ODgx.McXkZ3e6QJj3ucUkPsTRu2AmCQGf9o7J7Am6nIUNyH4g.2E2uRFpkPddEMrWGjDC9H1asx2Y4D8vGwnHn2klWXZUg.PNG.agapeuni/img.png?type=w80_blur)

​

HTTP 프록시 정보 입력. 없거나 잘 모르면 빈칸으로 "계속" 버튼 클릭.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjQ3/MDAxNjgxNDcyMDExNjMw.i4OKXyYqX_haK_tQhpHVG6V0hC6MY4M7buCjn_QSID0g.I5xvZAkt3-N-JTZXtMWwroboaCxzxzjazM9Zpsva-bIg.PNG.agapeuni/img.png?type=w80_blur)

​

프로그램 설치 진행.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjg1/MDAxNjgxNDcyMDE3MjQ0.hHTCI85c_Ibre-Fn2LKOC213XP8UpDhXmToSkSVkpbIg.xQ0FgTTWU0J-QJ-6r0FMUuN7GUnUEkzu3karzTMwYoQg.PNG.agapeuni/img.png?type=w80_blur)

​

패키지에 대한 통계를 제출할지 결정. "아니요"를 선택

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTYw/MDAxNjgxNDcyMDIwNzU2.W5vr3Cd7ydThvt28KSC10HRPavpYPeVmrO9IE6S4P2Ag.N-oQpQnLNlSZnjeNCuvqxTCcqnQPzuT0GUN6U-StJ-Ag.PNG.agapeuni/img.png?type=w80_blur)

​

데스크톱 환경과 표준 시스템 유틸리티를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjEx/MDAxNjgxNDcyMDI2NDMy.pMX0mHJ-osO9AgnL_3TDkWQCL8fYR34XjyHGEDVy800g.A5SHJf1BDjGQQoreHQSCshTIERrL726qaa44t7tfTcYg.PNG.agapeuni/img.png?type=w80_blur)

​

선택한 프로그램 설치 진행.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfODMg/MDAxNjgxNDcyMDMwMTEz.tkau0TFOdZrueqe8F1InNb6R335JF1u7JN97Vo3MG0kg.sth83lQvg5S0JZ9WxCGZ3c-nhSEkX0z4q17ev1esitEg.PNG.agapeuni/img.png?type=w80_blur)

​

하드 디스크에 GRUB 부트로더 설치. "예"를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjcx/MDAxNjgxNDcyMDMzNjAw.rcV-lD_jDgLFPkKEG3SV_5vDnQKAtp9f3p4y8ishENEg.aG3_-BnfW6LGuq8mZ8O-GSTGL0GlXvQO9rRogSsYNWYg.PNG.agapeuni/img.png?type=w80_blur)

​

부트로더를 설치할 장치를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjk3/MDAxNjgxNDcyMDM3MzE0.w4WWf9YXC3aNCz5er6ARZGjODbRkRIFn5LWBoSpJYrkg.pavTBsqgQwihu04Jmly52p1C-7dW33vSzCfyUmKXlZcg.PNG.agapeuni/img.png?type=w80_blur)

​

설치 마치기. 재시작하여 데이안 시스템으로 부팅.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjg2/MDAxNjgxNDcyMDQxMDA5.cou7E3XmjIwedujGvDfhVOgoTV8qkA9zOSOFKEeB3G8g.QrdNtT4O2wVkzd_S53EUdofDAS9Ha1jX5640hw5dZPog.PNG.agapeuni/img.png?type=w80_blur)

​

​

4\. Debian 실행

Debian 부트 화면. "Debian GNU/Linux"를 선택.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjQ0/MDAxNjgxNDcyMDQ1NDY3.Pa4-ZP0eqfI56MWs3iU44MpKiKL4jUm-EB5TTEdajJAg._KBMdqz56l3Bi-FjFAUVbsfn1A1Vk5yNmOS5PdAUqYcg.PNG.agapeuni/img.png?type=w80_blur)

​

사용자 로그인.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMTE2/MDAxNjgxNDcyMDQ4OTAz.mNA0cFUB5TSdeMA-SGDdP6n-AoR488tDMaQwIm7gTz4g.53iHfCwzfZPirC_6rDhPXFglIIRBemoSbNV5rY_tocQg.PNG.agapeuni/img.png?type=w80_blur)

​

데비안 화면.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfMjkw/MDAxNjgxNDcyMDUyNDc0.nQMpp4XIs6MRYCCJsR6SUk-AtRllzJ-yyGv9w6hLOwkg.36Phs0BeGPJCtNpIepiVGXiTUBVpvr9nUF1iuIM7UNsg.PNG.agapeuni/img.png?type=w80_blur)

​

설치되어 있는 파이썬 버전 확인.

![](https://postfiles.pstatic.net/MjAyMzA0MTRfODUg/MDAxNjgxNDcyMDU2ODIy.GTtsUc0wG1hovqMJ0gGPHVOlheL8v0iUG1Jf4SLD_rcg.jsIkjMG_O4nqLm2TIy_OMYhWj9vYYS6hj3Jun-toojkg.PNG.agapeuni/img.png?type=w80_blur)

​

​

![](https://blogfiles.pstatic.net/MjAyNjA2MTdfMTI4/MDAxNzgxNjIzNzc1NzA1.2QYwsPb7SzsAzNxbABqntGpXAscgNcqLRqQrRj6RQL0g.sS1rzJuq4-3ERN9qM8z69dPB5Y6mWd4F-WOitRfYhhEg.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w1)

#Debian #리눅스 #Debian다운로드 #VMware #가상머신 #Debian설치 #Korean #한국어설치 #디스크파티션 #LVM #부트로더설치 #GNU #오픈소스 #서버운영체제 #소프트웨어설치 #명령어 #리눅스명령어 #리눅스환경 #LinuxInstallation #데스크탑환경 #미러사이트 #DebianCommunity #가상화 #시스템관리 #리눅스기초 #Debian사용법 #Debian부팅 #파이썬 #Debian운영체제 #커뮤니티Debian

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
