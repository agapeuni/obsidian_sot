---
title: "2023-07-22 223163151786 InetSocketAddress - Java로 원격 서버 포트 열려있는지 확인"
type: blog-archive
status: active
created: 2023-07-22
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223163151786&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223163151786
published: "2023. 7. 22. 13:32"
body_hash: 88f2758b618e53ecec5c4a9e1387f6f69ce2f2f7ad1b38505f3b51dc1f114b4f
visibility: private
rag: exclude
---
# 2023-07-22 223163151786 InetSocketAddress - Java로 원격 서버 포트 열려있는지 확인

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223163151786&categoryNo=982
- 게시일: 2023. 7. 22. 13:32

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTdfMTg2/MDAxNzQ0ODE3MzIwOTQw.KP3h3A4cLeItJXC0jKthJSJPwz3X6YKDEhJj-Io3V-Ig.fC1RpSn4SBMzs_cbjbFPWcTuLE_XgVlN8M37Ers8Cxsg.PNG/Java-001_\(12\).png?type=w80_blur)

​

**1\. 개요**

프로젝트 진행 중에 원격 컴퓨터에 포트를 일일히 확인할 일이 있었다. 명령 프로프트 창에서 명령어로 확인할 수도 있다. 하지만 확인해야 하는 컴퓨터가 15대 정도라 매번 확인하는 것이 귀찮아 간단한 Java 클래스를 만들었다.

​

**2\. 코드**

IP 주소는 집에서 사용하고 있는 컴퓨터의 IP를 입력했고 포트는 잘 알려진 포트 일부를 넣었다.

import java.io.IOException; import java.net.InetSocketAddress; import java.net.Socket; import java.net.UnknownHostException; public class RemotePortCheck { @SuppressWarnings("resource") public static void main(String[] args) throws UnknownHostException, IOException { // IP 주소를 입력 String[] ipArray = { "192.168.45.165", "192.168.45.184"}; // 포트번호를 입력 int[] portArray = { 80, 8000, 8080, 3306 }; InetSocketAddress socketAddress = null; for (int i = 0; i < ipArray.length; i++) { System.out.println("\n" + ipArray[i]); for (int j = 0; j < portArray.length; j++) { try { socketAddress = new InetSocketAddress(ipArray[i], portArray[j]); new Socket().connect(socketAddress, 3000); System.out.println(ipArray[i] + ":" + portArray[j] + "\tOK"); } catch (Exception e) { System.out.println(ipArray[i] + ":" + portArray[j] + "\tNG"); } } } } }

**실행 결과**

IP 주소가 192.168.45.165 장비에서는 8080 포크가 열려있고 192.168.45.184 장비는 3306 포트가 열려있다. 8080은 웹 서비스를 추측해 볼 수 있고 3306은 MySQL/MariaDB가 사용하는 포트이다.

192.168.45.165 192.168.45.165:80 NG 192.168.45.165:8000 NG 192.168.45.165:8080 OK 192.168.45.165:3306 NG 192.168.45.184 192.168.45.184:80 NG 192.168.45.184:8000 NG 192.168.45.184:8080 NG 192.168.45.184:3306 OK

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#자바 #Java #원격포트확인 #포트체크 #네트워크 #Socket #InetSocketAddress #프로그래밍 #자바코드 #IP주소 #포트번호 #소프트웨어개발 #네트워크프로그래밍 #명령어실행 #프로젝트관리 #코드예제 #개발자블로그 #자바학습 #원격접속 #서버관리 #네트워크보안 #MySQL #웹서비스 #네트워크모니터링 #자바개발 #자바프로그래밍 #포트스캔 #명령프롬프트 #개발도구 #코드공유

![](https://postfiles.pstatic.net/MjAyMzA3MjJfNzIg/MDAxNjg5OTk5Njk5MTk3.fb_rDfzwIvoQa5fd1xDIespA_c2r5rSDz4_JIzcLO9cg.wCIurfxWP5_JC8Kulq8i0DIqYLgMzTTOBlHd7wxTGVsg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
