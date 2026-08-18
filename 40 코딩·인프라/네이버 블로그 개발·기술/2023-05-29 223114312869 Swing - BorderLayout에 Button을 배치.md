---
title: "2023-05-29 223114312869 Swing - BorderLayout에 Button을 배치"
type: blog-archive
status: active
created: 2023-05-29
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223114312869&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223114312869
published: "2023. 5. 29. 5:18"
body_hash: 718a635530a9d6bd3a9b4e1a943a0aaa94512b3dc8f46fddca02d4849ee32a27
visibility: private
rag: exclude
---
# 2023-05-29 223114312869 Swing - BorderLayout에 Button을 배치

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223114312869&categoryNo=982
- 게시일: 2023. 5. 29. 5:18

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTdfNzMg/MDAxNzQ0ODE4MzEzMTgw.c9gT-dN3_oiVzH0ohesqPnlsVv702bqADIp37SmJXxsg.2kPA4PWv7ZoYRRLRAyixWR8PWNzCSk4KqgGw_WVMe9Ag.PNG/Java-001_\(20\).png?type=w80_blur)

​

**1\. 개요**

Swing의 BorderLayout은 컨테이너의 레이아웃 매니저 중 하나이다. BorderLayout은 컨테이너를 동, 서, 남, 북, 중앙의 다섯4 개의 영역으로 나누어 컴포넌트를 배치한다. BorderLayout을 사용하여 컴포넌트를 배치할 때, 각 영역은 다음과 같은 특징을 가지고 있다.

​

1) 중앙(Center) 

중앙 영역은 컨테이너의 중앙에 위치하며, 다른 영역보다 우선순위가 높다. 주로 크기가 가변적인 컴포넌트인 경우에 사용된다. 중앙에 배치된 컴포넌트는 컨테이너의 사용 가능한 모든 공간을 차지하게 된다.

​

2) 북(North)

북쪽 영역은 컨테이너의 위쪽에 위치하며, 주로 제목, 로고 또는 메뉴 바 등과 같은 상단 영역에 배치되는 컴포넌트에 사용된다. 북쪽에 배치된 컴포넌트는 가로로 전체 너비를 차지하며, 세로 크기는 내용에 따라 결정된다.

​

3) 남(South)

남쪽 영역은 컨테이너의 아래쪽에 위치하며, 주로 상태 표시줄 또는 버튼과 같은 하단 영역에 배치되는 컴포넌트에 사용된다. 남쪽에 배치된 컴포넌트도 북쪽과 마찬가지로 가로로 전체 너비를 차지하며, 세로 크기는 내용에 따라 결정된다.

​

4) 서(West)

서쪽 영역은 컨테이너의 왼쪽에 위치하며, 주로 메뉴나 내비게이션 패널과 같은 좌측 영역에 배치되는 컴포넌트에 사용된다. 서쪽에 배치된 컴포넌트는 세로로 전체 높이를 차지하며, 가로 크기는 내용에 따라 결정된다.

​

5) 동(East)

동쪽 영역은 컨테이너의 오른쪽에 위치하며, 주로 광고나 사이드바와 같은 우측 영역에 배치되는 컴포넌트에 사용된다. 동쪽에 배치된 컴포넌트도 서쪽과 마찬가지로 세로로 전체 높이를 차지하며, 가로 크기는 내용에 따라 결정된다.

​

**2\. 예제**

아래는 BorderLayout을 사용한 예시 코드다. JFrame에 BorderLayout을 설정하고, 다섯 개의 JLabel을 각각의 영역에 배치한다. 프레임을 실행하면 각 영역에 해당하는 레이블이 표시된다.

​

파일 : BorderLayoutExample.java

import java.awt.BorderLayout; import javax.swing.JFrame; import javax.swing.JLabel; public class BorderLayoutExample { public static void main(String[] args) { JFrame frame = new JFrame("BorderLayout Example"); frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); frame.setLayout(new BorderLayout()); JLabel label1 = new JLabel("북"); JLabel label2 = new JLabel("남"); JLabel label3 = new JLabel("중앙"); JLabel label4 = new JLabel("서"); JLabel label5 = new JLabel("동"); frame.add(label1, BorderLayout.NORTH); frame.add(label2, BorderLayout.SOUTH); frame.add(label3, BorderLayout.CENTER); frame.add(label4, BorderLayout.WEST); frame.add(label5, BorderLayout.EAST); frame.pack(); frame.setVisible(true); } }

**실행 화면**

동서남북과 중앙에 잘 표시되었다.

![](https://postfiles.pstatic.net/MjAyMzA1MjlfMTk1/MDAxNjg1MzA0OTcyNjg0.Gmf7-3RLoqKNt22Fhl-tEbAWH2kJ01UTR95S0m20QTQg.1UADkqQAYDe9LE4tSV-69ASFfLSCEmfrvRCWJbMreiIg.PNG.agapeuni/image.png?type=w80_blur)

​

**3.****BorderLayout을 구현하고 Button을 추가**

Swing으로 BorderLayout을 구현하고 Button을 추가해 보자. BorderLayout 동서북에 버튼을 두고 남은 Label을 그리고 중앙은 TextArea를 두었다. 버튼을 클릭하면 어디에 클릭했는지 Label에 표시되고 Center에는 내용이 쌓인다.

​

파일 : BorderLayoutButton.java

import java.awt.BorderLayout; import java.awt.event.ActionEvent; import java.awt.event.ActionListener; import javax.swing.JButton; import javax.swing.JFrame; import javax.swing.JLabel; import javax.swing.JTextArea; public class BorderLayoutButton { private JFrame frame; private JButton btnNorth; private JButton btnEast; private JButton btnWest; private JLabel lblSouth; private JTextArea txaCenter; public BorderLayoutButton() { frame = new JFrame("성벽"); btnNorth = new JButton("북쪽 성벽"); btnEast = new JButton("동쪽 성벽"); btnWest = new JButton("서쪽 성벽"); txaCenter = new JTextArea("진영"); lblSouth = new JLabel("보고", JLabel.CENTER); } public void launchFrame() { btnNorth.addActionListener(new ButtonHandler()); btnEast.addActionListener(new ButtonHandler()); btnWest.addActionListener(new ButtonHandler()); frame.add(btnNorth, BorderLayout.NORTH); frame.add(btnEast, BorderLayout.EAST); frame.add(btnWest, BorderLayout.WEST); frame.add(txaCenter, BorderLayout.CENTER); frame.add(lblSouth, BorderLayout.SOUTH); frame.setSize(400, 300); frame.setVisible(true); } public class ButtonHandler implements ActionListener { public void actionPerformed(ActionEvent e) { lblSouth.setText(e.getActionCommand() + " 공격"); txaCenter.setText(txaCenter.getText() + "\n" + e.getActionCommand() + " 공격"); } } public static void main(String[] args) { new BorderLayoutButton().launchFrame(); } }

**실행 화면**

![](https://postfiles.pstatic.net/MjAyMzA1MjlfMjgy/MDAxNjg1MzM1ODI0NTc4.60QK_0yosNF1ER7jimD_w85D5_m5EWpT2N-TLHHPEHcg.X1ctMWCiB7uaVAdg3moiRd6qs_0CIQAH7jbVu7bgd_wg.PNG.agapeuni/image.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Swing #JavaSwing #BorderLayout #GUI프로그래밍 #자바개발 #컴포넌트배치 #JFrame #JavaDevelopment #프로그래밍 #AWT #이벤트처리 #버튼클릭 #Swing예제 #자바코드 #사용자인터페이스 #프론트엔드 #Label #TextArea #Java기초 #Java학습 #BorderLayoutExample #BorderLayoutButton #JButton #Swing컴포넌트 #소프트웨어개발 #GUI #프로그래밍블로그 #Java프로그래밍 #코드샘플 #프로그래밍예제 #소프트웨어엔지니어

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
