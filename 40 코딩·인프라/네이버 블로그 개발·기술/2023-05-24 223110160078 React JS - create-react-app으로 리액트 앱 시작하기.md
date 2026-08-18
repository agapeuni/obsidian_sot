---
title: "2023-05-24 223110160078 React JS - create-react-app으로 리액트 앱 시작하기"
type: blog-archive
status: active
created: 2023-05-24
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223110160078&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223110160078
published: "2023. 5. 24. 2:40"
body_hash: d3566895fd4dfecc218b50ddf68628cc4ae3102bc0598a6ff4a4aa156066d10a
visibility: private
rag: exclude
---
# 2023-05-24 223110160078 React JS - create-react-app으로 리액트 앱 시작하기

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223110160078&categoryNo=982
- 게시일: 2023. 5. 24. 2:40

## 본문

![](https://postfiles.pstatic.net/MjAyNDA1MTFfMTYz/MDAxNzE1NDE3NTcwNjE4.MqMavGKybvD2_nzyUpCULHjQsOVQ-UlirTT3HES49tEg.HJcMETAJj-DSh3BYIXSeb4jkXUHmEIxqWyKg9p4DPMYg.PNG/React-001_\(1\).png?type=w80_blur)

​

**1\. HTML 페이지에서 React 시작하기**

React를 빠르게 배우는 방법 중에 하나는 HTML 파일에 React 코드를 직접 작성하면서 동작을 확인하는 것이다.

​

참고로 React.JS V18.0.0 버전을 사용했다. 

  * <https://unpkg.com/react@18/umd/react.development.js>

  * <https://unpkg.com/react-dom@18/umd/react-dom.development.js>

​

1.1 HTML 코드

파일 : button_event.html

<!DOCTYPE html> <html> <head> <meta charset="UTF-8"> <title>Hello, World</title> </head> <body> <h2>버튼을 클릭하면 "Hello, World"가 표시된다.</h2> <div id="container"></div> <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script> <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script> <script src="button_event.js"></script> </body> </html>

1.2 JavaScript 코드

HelloButton 클래스를 정의했다. 

hello 상태가 true 이면 'Hello, World'를 리턴한다.

​

파일 : button_event.js

'use strict'; const e = React.createElement; class HelloButton extends React.Component { constructor(props) { super(props); this.state = { hello: false }; } render() { if (this.state.hello) { return 'Hello, World'; } return e( 'button', { onClick: () => this.setState({ hello: true }) }, 'Hello' ); } } const container = document.querySelector('#container'); const root = ReactDOM.createRoot(container); root.render(e(HelloButton));

실행 화면

![](https://postfiles.pstatic.net/MjAyMzA1MjRfMjA3/MDAxNjg0ODYyNTg1MTEx.0qLT1FfqrlgbnekpvCf8n20s9_txEvHTSP3-2MoM1hcg.ln72e61A_nDlxvGB-87aVyK82L09yqmXdOGlVGLBu-Qg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MjRfMTQ5/MDAxNjg0ODYyNTg4ODQw.nz3_r_gJMtkoUzCnKasB2KIeTmTSg3z_CB1X-82GAKUg.7MjoNXrrTEQnXWFToCbOPLpTdll2wa_jMMKrOnAUZy0g.PNG.agapeuni/image.png?type=w80_blur)

​

**2\. create-react-app으로 React 시작하기**

로컬에 node 18.16.0이 설치되어 있고 다음의 명령어로 react app을 생성한다.

> npx create-react-app my-app

![](https://postfiles.pstatic.net/MjAyMzA1MjRfNDIg/MDAxNjg0ODU5OTY1MDY0.DVSkggQQSVIfjFWtiMlmr9u4XzvprA_qThuEpzhHTqMg.vgsCzUGVw90yKUl9CLoae5tYwTVax75I8KnUzLPGqVEg.PNG.agapeuni/image.png?type=w80_blur)

​

![](https://postfiles.pstatic.net/MjAyMzA1MjRfNDMg/MDAxNjg0ODU5OTc2ODA1.MKCvlBYvXAjJzsNoT1b8N5vlPP0nOqo2Hqim77vjlSgg.FtVhGefz32r7-yQa4xZ2GSCrLIuV3mwmThZ6lNM_JA0g.PNG.agapeuni/image.png?type=w80_blur)

​

생성된 폴더로 이동해서 React App을 실행한다.

> cd my-app

> npm start

![](https://postfiles.pstatic.net/MjAyMzA1MjRfMjIz/MDAxNjg0ODYwMDI0ODIy.u6MsE2aXxePqLAtnDWT7-O4E-ujI1_IxgfiwQh9yRhMg.-3NWNB_fNh9Rzy1HhRqWis7g4USKq31-ShfNqD_BA10g.PNG.agapeuni/image.png?type=w80_blur)

​

실행 화면

![](https://postfiles.pstatic.net/MjAyMzA1MjRfNTUg/MDAxNjg0ODYwMDM5NTg4.OZE1ZoVkr1g_34kEMirnbFfJ2cBdVWvATbwVApdENMEg.ldYNA7GT35Z-T0pmUnWpIDbnb9xlSAX64Nvv94eOBL4g.PNG.agapeuni/image.png?type=w80_blur)

​

​

create-react-app을 실행하면 React 애플리케이션이 만들어지며 다음과 같은 코드가 포함된다.

![](https://postfiles.pstatic.net/MjAyMzA1MjRfMjcg/MDAxNjg0ODYyMzUwMjU1.0d5MEU1QftiF3Lt4CXh8cQwAfrgRH3G_gpxjdALJ18Ag.SAUvrfsbNDVNRjF7bbbMZOIdI2p5dX0xtduWztnYUMsg.PNG.agapeuni/image.png?type=w80_blur)

​

다음과 같이 Hello.js를 만들고 index.js에 추가해 보자.

​

파일 : Hello.js

import './Hello.css'; function Hello() { return ( <div className="Hello"> Hello, World </div> ); } export default Hello; 

​

파일 : Hello.css

.Hello { font-size: calc(10px + 2vmin); text-align: center; color: white; background-color: #10a162; }

​

파일 : index.js

import React from 'react'; import ReactDOM from 'react-dom/client'; import './index.css'; import App from './App'; import Hello from './Hello'; import reportWebVitals from './reportWebVitals'; const root = ReactDOM.createRoot(document.getElementById('root')); root.render( <React.StrictMode> <App /> <Hello /> </React.StrictMode> ); // If you want to start measuring performance in your app, pass a function // to log results (for example: reportWebVitals(console.log)) // or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals reportWebVitals();

실행 화면

![](https://postfiles.pstatic.net/MjAyMzA1MjRfNTYg/MDAxNjg0ODYzMzg0NTc4.Z-N09ClDir2w4z3YKJgr-SHFl_Pl7d5eFjYBgoCNDtYg.YwnAppm6mwMSIEbj9dPtfSbT6d_eP5Rqw5J3sfUi6w4g.PNG.agapeuni/image.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#React #HTML #JavaScript #createReactApp #ReactComponent #상태관리 #이벤트처리 #버튼클릭 #프론트엔드 #UI개발 #ReactJS #React18 #HelloWorld #웹개발 #ReactDOM #애플리케이션 #CSS #모듈화 #로컬개발환경 #npm #프로젝트생성 #코드예제 #프로그래밍 #개발자 #JavaScript라이브러리 #ReactHooks #효율적코드 #웹애플리케이션 #React로시작하기 #React기초 #자바스크립트

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
