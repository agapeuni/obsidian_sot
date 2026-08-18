---
title: "2018-10-22 221382248382 BCM2835 오류해결 - Unable to determine hardware version"
type: blog-archive
status: active
created: 2018-10-22
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=221382248382&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 221382248382
published: "2018. 10. 22. 3:24"
body_hash: 1a4398d8c76a27fd91942af8e5cd6ebc6fe3be3165a255556eae552c7b250e32
visibility: private
rag: exclude
---
# 2018-10-22 221382248382 BCM2835 오류해결 - Unable to determine hardware version

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=221382248382&categoryNo=982
- 게시일: 2018. 10. 22. 3:24

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MDdfOTAg/MDAxNzQ0MDI5MjE0NTM2.H3GKpx7jZ_cqJIzQ5Cm6TkNNwLnNR2oazFsb4fRQ8fQg.T0LvZfUeJvCg0lntPFPLjsBKrUosx7OhJBd6p374NWsg.PNG/Pi-Software-001_\(15\).png?type=w80_blur)

​

Pi4J 로고 아래의 문구가 **"라즈베리 파이를 위한 Java 입출력 라이브러리"** 로 변경이 되었습니다.

![](https://postfiles.pstatic.net/MjAxODEwMjBfMTEg/MDAxNTQwMDA1OTk1NTQ5.tLuxz5_smwvvzEr1J9ULFR2XOW4uhk7DMXG8Bqw33wMg.B7Y6k-vo6p8BvtoHbADhYbr3y3hywZQyihGXWUn5Skkg.PNG.agapeuni/pi4j-header.png?type=w80_blur)

​

참고로 이전의 문구는 "**라즈베리 파이에 자바를 연결하기** " 였습니다.

![](https://postfiles.pstatic.net/MjAxODEwMjBfMTk5/MDAxNTQwMDA2MTIyNzM0.Lazij5b6WjFzRxlEzqEublVpzvrxCfTJbB_Uj-rUDKcg.PYayKOMfJKoo0EO_qxffPBM8SJvDloI298iQGYc40l0g.JPEG.agapeuni/pi4j-header-small3_%281%29.jpg?type=w80_blur)

​

​

새롭게 라즈비안을 설치하고 쉬운 설치로 아래와 같이 Pi4J를 설치하였습니다. 설치를 완료하고 Pi4J 버전을 확인해 보면 1.1로 표시됩니다.

​

**$ curl -s get.pi4j.com | sudo bash**(Pi4J 쉬운 설치)

**$ pi4j -v**(Pi4J 버전 확인)

**pi@raspberrypi:~ $****curl -s get.pi4j.com | sudo bash** ====================================================INSTALLING Pi4J GPG PUBLIC KEY====================================================% Total % Received % Xferd Average Speed Time Time Time CurrentDload Upload Total Spent Left Speed100 1761 100 1761 0 0 2831 0 --:--:-- --:--:-- --:--:-- 2872OK====================================================ADDING Pi4J APT REPOSITORY====================================================\--2018-10-21 13:49:46-- [_http://get.pi4j.com/pi4j.list_](http://get.pi4j.com/pi4j.list) Resolving get.pi4j.com (get.pi4j.com)... 52.216.20.10Connecting to get.pi4j.com (get.pi4j.com)|52.216.20.10|:80... connected.HTTP request sent, awaiting response... 200 OKLength: 42 [application/octet-stream]Saving to: ‘/etc/apt/sources.list.d/pi4j.list’​/etc/apt/sources.list.d/pi4j. 100%[=========================>] 42 --.-KB/s in 0s​2018-10-21 13:49:47 (488 KB/s) - ‘/etc/apt/sources.list.d/pi4j.list’ saved [42/42]​====================================================UPDATING APT REPOSITORIES====================================================Ign:1 [_http://repository.pi4j.com_](http://repository.pi4j.com/) wheezy InReleaseGet:2 [_http://repository.pi4j.com_](http://repository.pi4j.com/) wheezy Release [1,778 B]Get:3 [_http://repository.pi4j.com_](http://repository.pi4j.com/) wheezy Release.gpg [514 B]Get:4 [_http://repository.pi4j.com_](http://repository.pi4j.com/) wheezy/rpi armhf Packages [379 B]Fetched 2,671 B in 5s (481 B/s)Reading package lists... Done====================================================INSTALLING Pi4J====================================================Reading package lists... DoneBuilding dependency treeReading state information... DoneThe following NEW packages will be installed:pi4j0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.Need to get 1,394 kB of archives.After this operation, 2,122 kB of additional disk space will be used.Get:1 [_http://repository.pi4j.com_](http://repository.pi4j.com/) wheezy/rpi armhf pi4j all 1.1 [1,394 kB]Fetched 1,394 kB in 2s (594 kB/s)Selecting previously unselected package pi4j.(Reading database ... 115960 files and directories currently installed.)Preparing to unpack .../apt/archives/pi4j_1.1_all.deb ...Unpacking pi4j (1.1) ...Setting up pi4j (1.1) ...====================================================Pi4J INSTALLATION COMPLETE====================================================​The Pi4J JAR files are located at:/opt/pi4j/lib​Example Java programs are located at:/opt/pi4j/examples​You can compile the examples using this script:sudo /opt/pi4j/examples/build​Please see [_http://www.pi4j.com_](http://www.pi4j.com/) for more information.​pi@raspberrypi:~ $**pi@raspberrypi:~ $****pi4j -v** \--------------------------------------------THE Pi4J PROJECT\--------------------------------------------VERSION : 1.1TIMESTAMP : 2016-07-26 05:46:05\--------------------------------------------pi@raspberrypi:~ $​  
---  
  
​

![](https://postfiles.pstatic.net/MjAyMjA0MjVfODkg/MDAxNjUwODQ3OTExNjc1.BjLfTdtW_O58zN6jUxCZyV2njnvY4FNUUWOyGKc6A30g.p81m6oE-rmRQck0QuPVDbyVIPxy325M4feN_UBjWogAg.JPEG.agapeuni/pi4j-overview.jpg?type=w80_blur)

[이미지 출처] <https://pi4j.com/>

​

Pi4J 워밍업 차원에서 아래의 예제 코드를 복사하여 컴파일을 하고 실행을 하였습니다. 컴파일은 성공적으로 되어 .class 파일이 생성되었지만 실행을 하니 "hardware version" 에 대핸 메시지가 표시되고 실행이 되지 않았습니다.

​

**$ pi4j -c ControlGpioExample.java**(Pi4J로 소스코드 컴파일)

**$ sudo pi4j ControlGpioExample**(Pi4J로 클래스파일 실행)

**pi@raspberrypi:~ $****pi4j -c ControlGpioExample.java** \--------------------------------------------Pi4J - Compiling: ControlGpioExample.java\--------------------------------------------\+ javac -classpath '.:classes:*:classes:/opt/pi4j/lib/*' -d . ControlGpioExample.javapi@raspberrypi:~ $ lltotal 52-rw-r--r-- 1 pi pi 1720 Oct 21 13:52 ControlGpioExample.class-rw-r--r-- 1 pi pi 1983 Oct 21 13:52 ControlGpioExample.javapi@raspberrypi:~ $**pi@raspberrypi:~ $****sudo pi4j ControlGpioExample** \+ java -classpath '.:classes:*:classes:/opt/pi4j/lib/*' ControlGpioExample<\--Pi4J--> GPIO Control Example ... started.Unable to determine hardware version. I see: Hardware : BCM2835, \- expecting BCM2708 or BCM2709.If this is a genuine Raspberry Pi then please report thisto projects@drogon.net. If this is not a Raspberry Pi then youare on your own as wiringPi is designed to support theRaspberry Pi ONLY.  
---  
  
​

CPU정보를 확인해보고 관련 내용을 인터넷을 찾아보니 Pi4J 버전을 1.2로 업그레이드 하면 해결이 된다고 합니다.

Pi4J를 업그레이드를 하고 다시 실행하니 정상적으로 실행이 되었습니다.

​

**$ cat /proc/cpuinfo**(CPU 정보확인)

**$ wget**[**http://get.pi4j.com/download/pi4j-1.2-SNAPSHOT.deb**](http://get.pi4j.com/download/pi4j-1.2-SNAPSHOT.deb)****(Pi4J 1.2 다운로드)

**$ sudo dpkg -i pi4j-1.2-SNAPSHOT.deb**(Pi4J 1.2 설치)

**$ sudo pi4j ControlGpioExample**(Pi4J로 클래스파일 실행)

**pi@raspberrypi:~ $****cat /proc/cpuinfo** processor : 0model name : ARMv6-compatible processor rev 7 (v6l)BogoMIPS : 697.95Features : half thumb fastmult vfp edsp java tlsCPU implementer : 0x41CPU architecture: 7CPU variant : 0x0CPU part : 0xb76CPU revision : 7​Hardware : BCM2835Revision : 000eSerial : 00000000b8037badpi@raspberrypi:~ $**pi@raspberrypi:~ $****wget**[**http://get.pi4j.com/download/pi4j-1.2-SNAPSHOT.deb**](http://get.pi4j.com/download/pi4j-1.2-SNAPSHOT.deb) \--2018-10-21 13:55:08-\- <http://get.pi4j.com/download/pi4j-1.2-SNAPSHOT.deb>Resolving get.pi4j.com (get.pi4j.com)... 54.231.112.186Connecting to get.pi4j.com (get.pi4j.com)|54.231.112.186|:80... connected.HTTP request sent, awaiting response... 200 OKLength: 1702174 (1.6M) [application/octet-stream]Saving to: ‘pi4j-1.2-SNAPSHOT.deb’​pi4j-1.2-SNAPSHOT.deb 100%[===============>] 1.62M 1.08MB/s in 1.5s​2018-10-21 13:55:10 (1.08 MB/s) - ‘pi4j-1.2-SNAPSHOT.deb’ saved [1702174/1702174]​pi@raspberrypi:~ $**pi@raspberrypi:~ $****sudo dpkg -i pi4j-1.2-SNAPSHOT.deb**(Reading database ... 116099 files and directories currently installed.)Preparing to unpack pi4j-1.2-SNAPSHOT.deb ...Unpacking pi4j (1.2~SNAPSHOT) over (1.1) ...upgradeSetting up pi4j (1.2~SNAPSHOT) ...pi@raspberrypi:~ $**pi@raspberrypi:~ $****sudo pi4j ControlGpioExample** \+ java -classpath '.:classes:*:classes:/opt/pi4j/lib/*' ControlGpioExample<\--Pi4J--> GPIO Control Example ... started.\--> GPIO state should be: ON\--> GPIO state should be: OFF\--> GPIO state should be: ON\--> GPIO state should be: OFF\--> GPIO state should be: ON for only 1 secondExiting ControlGpioExamplepi@raspberrypi:~ $   
---  
  
​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Pi4J #라즈베리파이 #자바라이브러리 #라즈베리안 #Pi4J설치 #쉬운설치 #Java입출력 #라즈베리파이자바 #자바제어 #GPIO #Pi4J버전 #자바제어라이브러리 #라즈베리파이제어 #하드웨어제어 #Pi4J1.1 #Pi4J1.2 #라즈베리파이프로젝트 #Pi4J업그레이드 #라즈베리파이활용 #자바예제 #하드웨어제어라이브러리 #Pi4J설치법 #라즈베리파이시작 #라즈베리파이개발 #자바개발환경 #자바예제코드 #Pi4JControlGpio #Pi4J제어 #GPIO입출력 #라즈베리파이개발 #Pi4J설치문제 #라즈베리파이기초 #자바기초

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
