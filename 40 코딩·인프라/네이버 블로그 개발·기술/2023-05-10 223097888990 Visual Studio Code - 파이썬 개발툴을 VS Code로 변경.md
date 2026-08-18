---
title: "2023-05-10 223097888990 Visual Studio Code - 파이썬 개발툴을 VS Code로 변경"
type: blog-archive
status: active
created: 2023-05-10
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223097888990&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223097888990
published: "2023. 5. 10. 2:44"
body_hash: 92312e6577136c506ec5f9f4a5c914a8d0b481b54e63231f006d2e024689d306
visibility: private
rag: exclude
---
# 2023-05-10 223097888990 Visual Studio Code - 파이썬 개발툴을 VS Code로 변경

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223097888990&categoryNo=982
- 게시일: 2023. 5. 10. 2:44

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTlfMjQ4/MDAxNzQ1MDExODM5MzIz.rg-VZw4KxXXRPBY-PrOCBNa4Kun-9vi-y1hdL-BiyLYg.PW1dL_yLpyhPqdHkupKFJzJSptDoxAlt1OEA4ksQ8FAg.PNG/%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-001_\(4\).png?type=w80_blur)

​

1\. Thonny의 한계

파이썬 IDE로 그동안 Thonny를 사용했다. 라즈베리 파이에서 잘 사용하여 익숙해졌고 윈도우에서도 사용이 가능했다. 그러다가 실무에서 파이썬 프로젝트를 진행하면서 Thonny의 한계를 인지하고 Visual Studio Code로 갈아타게 되었다.

​

<https://blog.naver.com/agapeuni/222654800128>

[ ![](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fblogthumb.pstatic.net%2FMjAyMjAyMjJfNzQg%2FMDAxNjQ1NTE5MjI5OTkw.8--rHOIJ3d8tyOlOI60QyN7Dhvl7h_QcH-S0PH6FWKUg.8FqTEiWxfrDm5zitpVQOcfuE698n4hDiZ4JT6ZbBpW0g.PNG.agapeuni%2F1.png%3Ftype%3Dw2%22&type=ff500_300) ](https://blog.naver.com/agapeuni/222654800128) [ **파이썬(Python) 가볍고 편리한 Python IDE, Thonny** 1\. 개요 요즘 실무에서도 많이 사용하고 있는 Python을 준비하고자 시간이 나면 틈틈히 학습을 하고 있다.... blog.naver.com ](https://blog.naver.com/agapeuni/222654800128)

​

2\. Visual Studio Code 다운로드

Visual Studio Code 홈페이지에 접속하면 메인화면에 "Download for Windows"이 보인다. "Download for Windows"를 클릭하면 안정화된 버전의 Visual Studio Code 설치 파일을 내려받을 수 있지만 아래의 "Other platforms"을 클릭하면 다른 버전을 선택할 수 있다.

​

<https://code.visualstudio.com/>​

![](https://postfiles.pstatic.net/MjAyMzA1MTBfOTIg/MDAxNjgzNjUxMzM2MTYw.3DarY2mrG2i77yaAGBzs1pkpIdWkmE6behFkfVZ0gBcg.7FpBxSqh6Jx1J9VllFKfMU6-ekzgczSyJW0-ICDs20Ug.PNG.agapeuni/image.png?type=w80_blur)

​

아래의 주소에서 User Installer와 System Installer를 다운로드할 수 있다. x64는 64bit 버전이고 x86은 32bit 버전이다. User Installer는 현재 로그인된 사용자 계정에만 설치를 하고 System Installer는 전체 사용자가 사용할 수 있도록 설치를 한다. 

​

Windows 용 System Installer 64bit를 선택하여 설치 파일을 내려받았다.

<https://code.visualstudio.com/download>​

![](https://postfiles.pstatic.net/MjAyMzA1MTBfODkg/MDAxNjgzNjUxMzcwNzU4.Hq2MxMqtjerY6SXQHaf59U_OJrtqbMnBmz9r3L2dJbwg._nL-fb4Z1sqSQaLM93lIMcgwPOk5iEh8eTYy9TgNzNAg.PNG.agapeuni/image.png?type=w80_blur)

​

3\. Visual Studio Code 설치

내려받은 Visual Studio Code 설치 프로그램 "VSCodeSetup-x64-1.78.0" 파일을 관리자 권한으로 실행한다.

  * 시스템 인스톨러 : VSCodeSetup-x64-1.78.0

  * 사용자 인스톨러 : VSCodeUserSetup-x64-1.78.0

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTU0/MDAxNjgzNjUxNjgxNzI4.yMUjEy1eQKuWkXgLfLzeuwAvALaOlPFbUC7fWEAtnrgg.Y2olfiUL5iPhEyUy47wTIrljqsrqxejcAdQm2-_AJrEg.PNG.agapeuni/image.png?type=w80_blur)

​

"사용권 계약"화면에서 동의합니다를 선택하고 "다음" 버튼을 클릭한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfNzcg/MDAxNjgzNjUxNzA5NTgw.R0_575tlR2lOdS-QR_BtuW8MimxZKhNYMq9_o91IwzMg.Fj-FaUm73J9LcxLXLfPvUy5ShsWa6jyuXG8yENifHuwg.PNG.agapeuni/image.png?type=w80_blur)

​

"설치 위치 선택" 화면에서 경로는 "D:\dev\vscode"로 입력했다. 

현재 개발과 관련 프로그램은 D 드라이브에 설치하고 있다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTYz/MDAxNjgzNjUxNzg5NjMx.D_EQy4k3MjyXoSHeQhCWrSwHYxC8QpAlx6xQeQbD4Wog.NKsOcLdUFbw8iYyl1KmDiO8zfQvCFPsyXAoEVzZGu88g.PNG.agapeuni/image.png?type=w80_blur)

​

"시작 메뉴 폴더 선택" 화면은 기본값을 그대로 하고 "다음"버튼을 클릭한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfODQg/MDAxNjgzNjUxODAwMDQ3.KSwYiyMQrS-eyGW1g7osktk10VERonYj2lw9-UbPPy8g.uh_sNTSNiIRefdEqcj-icJeiEFd9FYrut1R0qCMblYcg.PNG.agapeuni/image.png?type=w80_blur)

​

"추가 작업 선택"화면에서는 기본값 "PATH에 추가" 선택을 그대로 하고 "다음"버튼을 클릭한다.

PATH에 추가하면 cmd 창에서 code를 입력하면 VS Code가 실행된다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjQ3/MDAxNjgzNjUxODIyNjY2.EoCbLf1QlBYVDIobRSYfofipzl99owQmJ_Xy51qLY_8g.zoIvpZ8ZZAMQomkn2c5F2oU-inFKF5gMJFoQaDbQ27og.PNG.agapeuni/image.png?type=w80_blur)

​

"설치 준비 완료" 화면에서 "설치"버튼을 클릭하여 설치를 진행한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjA0/MDAxNjgzNjUxODQwMDU5.IFgUxesmDKt0Rt1Z3HEsKrHQB4GDBkPxF9fKirTv3rEg.jypEVFLxkgkrWpdvsQBHPKI5_3lqMC0d_D_jVRn9JNMg.PNG.agapeuni/image.png?type=w80_blur)

​

설치 진행

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTEz/MDAxNjgzNjUxODUwMzgw.8181S7J9lroAVfAZY0cKIJC9KQGo4fwppIAGDLE0B-kg.Ubn7vWZf5R9tPkfcsUH1tnWG1YAC3HNXU6m9UoK_YBkg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTIg/MDAxNjgzNjUxODU2MDgy.9QRyu2XFVBKhQnT--kK4imeeN6gvNeDmn0sH7wR6_BUg.QulNKXDHrbT9eYFsiJruSIM7YOdhkSaOon5CBVfkeAog.PNG.agapeuni/image.png?type=w80_blur)

​

설치가 완료되었다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjc5/MDAxNjgzNjUxODc0OTk4.ocqeLGWUcJfVoaTRV7QraU1EhXl48tLt8JBEUQ0EwB8g.51IxgfpLo0jG_8OSHlsuKp6822t65YXl8F8ZvxVawW8g.PNG.agapeuni/image.png?type=w80_blur)

​

​

4\. Visual Studio Code 실행

Visual Studio Code를 실행한 화면이다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjg5/MDAxNjgzNjUxOTI2Njgy.6gDCv00yNtah9uTyef-YSb73O4BfpQ_2j5l6fvHwrs0g.3laHxmGWWCKsOxEZT6cRyTs-T0G4A69IGivjuJQ4ZDog.PNG.agapeuni/image.png?type=w80_blur)

​

File 메뉴에서 Open Folder...를 선택한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTAz/MDAxNjgzNjUyMDAzNjE0.OgUQmuRC2vGtJzn6pRHdSU0iHDs4KsJaBMJYYPD8_dUg.cRDo_IeyJp870p31sUI7SpjSXMkQCxQdPk03z_vMWNIg.PNG.agapeuni/image.png?type=w80_blur)

​

D 드라이드에 개발과 관련된 프로그램과 소스코드를 관리하고 있다. 

python 폴더 아래에 있는 mykanban을 선택했다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTIw/MDAxNjgzNjUyMDU0MDUx.cs-3zskqQYL0RJotDcCKP6C8mJQePipY63D22tgznB0g.cVJfo9Tw-GAG16tPoloNa8B3nan8I73k041SJPA9rtcg.PNG.agapeuni/image.png?type=w80_blur)

​

5\. Extension 설치

무료로 설치 가능한 Extension들을 보고 Thonny에서 VS Code로 옮기기로 결정했다.

Python, Error Lens, Rainbow CSV, vscode-icons, ... 등 필요한 Extension을 설치한다. 

​

**1) Python Extension**

파이썬 개발 시 기본으로 설치해야 한다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjUz/MDAxNjgzNjUzMDg4MDY3.axiHYJMbf4MIR6Zu6ifc1_fa_SEFfidZhHow7_8ajaQg.HWzm-GIdOw6Fy7LTE26PMa-SXI5fZJs16Sb90pLncRkg.PNG.agapeuni/image.png?type=w80_blur)

​

**2) Error Lens**

코드에 에러가 있으면 해당 줄에 표시해 준다. 일반적인 코드 오류는 실행하기 전에 확인 가능하다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMTM3/MDAxNjgzNjUzODIxODUx.M0eBHx3T13y3JYpH76-Lf1iKEybv8spTPyB61mNfrAwg.f1J6xCzKhNOzo4UI0zFLSgMpGHnmKVPS37vLZgtZvRwg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjQg/MDAxNjgzNjUzOTMyOTEx.azTIHt5YhsSVqSuh3if5HMUPm1JQFvIcgOELO0UrL98g.4SIMPU90JjNVLbq1nIs58gnNS-ghK0nabLEkh66FoBIg.PNG.agapeuni/image.png?type=w80_blur)

​

**3) indent-rainbow**

인덴테이션(indentation)을 색상으로 구분해 준 는 멋진 익스텐션이다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjEw/MDAxNjgzNjUzMzk0NDI0.5vs4_BTshyXobXbGCL_6htLTYMkkZqiGPi_pQdnskNog.z8J42SaZBUox3TlAkqyFjafmruypJS9Hia4_MvqlVBQg.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTBfNTUg/MDAxNjgzNjUzNDYxMjY5.kVdS1e2diOMxUcO7dClQNGIPahZsy0nGsPdxXNeoY-Mg.LcZZ86p-kczRg2SPAgssQbS_4dYuOGOJW8tar2zLcVgg.PNG.agapeuni/image.png?type=w80_blur)

​

**4) Rainbow CSV Extension**

CVS 파일의 데이터를 색상으로 구분해 주어 칼럼을 구분하기 좋다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfNDEg/MDAxNjgzNjUzMTA4MTk5.kDtE7yvUY3Qf6kPHpV8Fzu8eev_9a6mctBx8PjzGzYog.DrsC-lMAfeEaeXTOgZxZnFN6Lw4PziZHLanUXuIGQD0g.PNG.agapeuni/image.png?type=w80_blur)

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjQy/MDAxNjgzNjUzMTM0MTU0.8vrKt2OJ0pRbsvaN9ZNxmL_lL_Jc5DVTt4wBuPY2H1Ig.rM6L-W5aDvzonrvniTBpl9aRpPYMAhxCRlaxnAP5uT8g.PNG.agapeuni/image.png?type=w80_blur)

​

**5) vscode-icons**

좌측에 Explorer를 보면 파일 앞에 아이콘이 있어 눈에 식별이 잘 된다.

![](https://postfiles.pstatic.net/MjAyMzA1MTBfMjQx/MDAxNjgzNjUzMjc3OTY0.eHIAxBq1PPoCJQ1kXzZrNk3j67eMlG4YbTJsBXkdzzIg.32C6FmP2taVwE136VH9KUk8Le59LOluCJCwP4YnHBVAg.PNG.agapeuni/image.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Python #파이썬 #Thonny #VisualStudioCode #파이썬IDE #VSCode설치 #VSCode다운로드 #PythonExtension #ErrorLens #indentRainbow #RainbowCSV #vscodeIcons #Python개발 #파이썬환경설정 #VSCode환경설정 #Thonny한계 #VSCode장점 #코드에디터 #파이썬프로젝트 #PythonErrorLens #PythonRainbowCSV #PythonVSCodeIcons #VSCode설치가이드 #파이썬코딩 #개발환경 #IDE비교 #Thonny대VSCode #파이썬확장팩 #코드인덴트 #코드관리 #파이썬학습

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
