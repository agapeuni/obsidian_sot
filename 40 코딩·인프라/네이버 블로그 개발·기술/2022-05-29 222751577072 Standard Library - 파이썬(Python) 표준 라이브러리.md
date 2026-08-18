---
title: "2022-05-29 222751577072 Standard Library - 파이썬(Python) 표준 라이브러리"
type: blog-archive
status: active
created: 2022-05-29
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222751577072&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 222751577072
published: "2022. 5. 29. 23:45"
body_hash: 0775435dbfdd6f41493bd81c7c65c7b9d9450c6d83ae680ab2483da48ecd1339
visibility: private
rag: exclude
---
# 2022-05-29 222751577072 Standard Library - 파이썬(Python) 표준 라이브러리

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222751577072&categoryNo=982
- 게시일: 2022. 5. 29. 23:45

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMzUg/MDAxNzQ0NDQzOTAzMzU3.MQl2vBZlHHLent3DgUV4mx_SNUP_lq6AEY_A-m3OYTsg.4WidoeehRPtkQBrviCRk5Jq2-7e98bOaxKa6DfSn1KAg.PNG/%ED%8C%8C%EC%9D%B4%EC%8D%AC-001_\(5\).png?type=w80_blur)

​

1\. 파이썬 표준 라이브러리

파이썬은 기본적인 기능 외에도 프로그래밍에 필요한 표준 라이브러리(Standard Library)를 제공한다. 파이썬 표준 라이브러리는 파이썬 프로그래머들에게 다양한 작업을 쉽게 처리할 수 있는 도구와 모듈을 제공하여 프로그래밍 작업을 간편하게 만들어준다. 파이썬 표준 라이브러리는 잘 정리되어 있고 문서화도 잘 되어 있다. 다른 언어를 사용하다 파이썬으로 넘어온 개발자는 그 방대한 기능으로 인해 충격을 받기도 한다. 파이썬에서 제공하는 유용한 표준 라이브러리와 표준 라이브러리를 분류별로 정리해 본다.

​

파이썬 언어 레퍼런스와는 다르게 파이썬 표준 라이브러리는 실제 기능을 제공한다. 다양한 프로그래밍 작업에 대한 표준적인 해결책을 제공하는 파이썬으로 작성된 모듈과, 파일 I/O와 같은 시스템 기능에 액세스하는 내장 모듈로 이루어져 있다. 일부 모듈은 플랫폼 관련 사항을 추상화하여 파이썬 프로그램의 이식성을 향상시키도록 설계되었다. 윈도우용 파이썬 설치 프로그램에는 일반적으로 전체 표준 라이브러리와 추가 구성 요소가 포함되지만, 유닉스 기반 운영 체제에서는 패키지 도구를 사용하여 선택적 구성 요소를 설치해야 할 수 있다.

​

​

2\. 유용한 표준 라이브러리

아래는 자주 사용하는 유용한 표준 라이브러리이다.

  * argparse - 명령 인수를 분석한다.

  * calendar - 날짜에 관한 기능을 제공한다.

  * codecs - 인코딩과 디코딩 함수를 제공한다.

  * collections - 다양한 자료구조를 제공한다.

  * copy - 데이터 복사 기능을 제공한다.

  * csv - CSV 파일을 읽고 쓰는 기능을 제공한다.

  * datetime - 날짜, 시간에 대한 기능을 제공한다.

  * io - I/O 스트림 기능을 제공한다.

  * json - JSON 파일을 읽고 쓰는 기능을 제공한다.

  * logging - 로깅 기능을 제공한다.

  * os - OS에 관한 기능을 제공한다.

  * random - 난수 생성 함수를 제공한다.

  * re - 정규 표현식 기능을 제공한다.

  * urllib - URL을 처리하고 분석하는 기능을 제공한다.

  * uuid - UUID를 생성하는 기능을 제공한다.

​

3\. 표준 라이브러리 분류별 정리

**3.1 텍스트 처리 서비스**

string — 일반적인 문자열 연산

re — 정규식 연산

​

​

**3.2 바이너리 데이터 서비스**

struct — 패킹 된 바이너리 데이터로 바이트열을 해석

codecs — 코덱 레지스트리와 베이스 클래스

​

​

**3.3 데이터형**

datetime — 기본 날짜와 시간 형

calendar — 일반 달력 관련 함수

collections — 컨테이너 데이터형

array — 효율적인 숫자 배열

types — 동적 형 생성과 내장형 이름

copy — 얕은 복사와 깊은 복사 연산

pprint — 예쁜 데이터 인쇄기

enum — 열거형 지원

​

​

**3.4 숫자와 수학 모듈**

numbers — 숫자 추상 베이스 클래스

math — 수학 함수

decimal — 십진 고정 소수점 및 부동 소수점 산술

random — 의사 난수 생성

statistics — 수학 통계 함수

​

​

**3.5 함수형 프로그래밍 모듈**

itertools — 효율적인 루핑을 위한 이터레이터를 만드는 함수

functools — 고차 함수와 콜러블 객체에 대한 연산

operator — 함수로서의 표준 연산자

​

​

**3.6 파일과 디렉터리 액세스**

pathlib — 객체 지향 파일 시스템 경로

os.path — 일반적인 경로명 조작

glob — 유닉스 스타일 경로명 패턴 확장

shutil — 고수준 파일 연산

​

​

**3.7 데이터 지속성**

pickle — 파이썬 객체 직렬화

sqlite3 — SQLite 데이터베이스용 DB-API 2.0 인터페이스

​

​

**3.8 데이터 압축 및 보관**

zlib — gzip 과 호환되는 압축

gzip — gzip 파일 지원

bz2 — bzip2 압축 지원

zipfile — ZIP 아카이브 작업

tarfile — tar 아카이브 파일 읽기와 쓰기

​

​

**3.9 파일 형식**

csv — CSV 파일 읽기와 쓰기

json — JSON 인코더와 디코더

​

​

**3.10 암호화 서비스**

hashlib — 보안 해시와 메시지 요약

​

​

**3.11 일반 운영 체제 서비스**

os — 기타 운영 체제 인터페이스

io — 스트림 작업을 위한 핵심 도구

time — 시간 액세스와 변환

argparse — 명령행 옵션, 인자와 부속 명령을 위한 파서

logging — 파이썬 로깅 시설

​

​

**3.12 동시 실행**

threading — 스레드 기반 병렬 처리

multiprocessing — 프로세스 기반 병렬 처리

​

​

**3.13 네트워킹과 프로세스 간 통신**

asyncio — 비동기 I/O

socket — 저수준 네트워킹 인터페이스

ssl — 소켓 객체용 TLS/SSL 래퍼

signal — 비동기 이벤트에 대한 처리기 설정

mmap — 메모리 맵 파일 지원

​

​

**3.14 인터넷 데이터 처리**

email — 전자 메일과 MIME 처리 패키지

base64 — Base16, Base32, Base64, Base85 데이터 인코딩

​

​

**3.15 구조화된 마크업 처리 도구**

html — 하이퍼텍스트 마크업 언어 지원

​

​

**3.16 XML 처리 모듈**

xml.dom — 문서 객체 모델 API

xml.sax — SAX2 구문 분석기 지원

​

​

**3.17 인터넷 프로토콜과 지원**

urllib — URL 처리 모듈

urllib.request — URL을 열기 위한 확장 가능한 라이브러리

urllib.response — urllib가 사용하는 응답 클래스

http — HTTP 모듈

http.client — HTTP 프로토콜 클라이언트

ftplib — FTP 프로토콜 클라이언트

uuid — RFC 4122 에 따른 UUID 객체

http.server — HTTP 서버

http.cookies — HTTP 상태 관리

http.cookiejar — HTTP 클라이언트를 위한 쿠키 처리

​

​

**3.18 멀티미디어 서비스**

wave — WAV 파일 읽고 쓰기

colorsys — 색 체계 간의 변환

​

​

**3.19 국제화**

gettext — 다국어 국제화 서비스

locale — 국제화 서비스

​

​

**3.20 프로그램 프레임워크**

turtle — 터틀 그래픽

cmd — 줄 지향 명령 인터프리터 지원

​

​

**3.21 개발 도구**

pydoc — 설명서 생성과 온라인 도움말 시스템

doctest — 대화형 파이썬 예제 테스트

unittest — 단위 테스트 프레임워크

test — 파이썬 용 회귀 테스트 패키지

​

​

**3.22 디버깅과 프로파일링**

bdb — 디버거 프레임워크

pdb — 파이썬 디버거

timeit — 작은 코드 조각의 실행 시간 측정

trace — 파이썬 문장 실행 추적

​

​

**3.23 소프트웨어 패키징 및 배포**

distutils — 파이썬 모듈 빌드와 설치

venv — 가상 환경 생성

​

​

**3.24 파이썬 실행시간 서비스**

sys — 시스템 특정 파라미터와 함수

sysconfig — 파이썬의 구성 정보에 접근하기

builtins — 내장 객체

atexit — 종료 처리기

gc — 가비지 수거기 인터페이스

​

​

**3.25 사용자 정의 파이썬 인터프리터**

code — 인터프리터 베이스 클래스

codeop — 파이썬 코드 컴파일

​

​

**3.26 모듈 임포트 하기**

zipimport — Zip 저장소에서 모듈 임포트

pkgutil — 패키지 확장 유틸리티

importlib — import의 구현

​

​

**3.27 파이썬 언어 서비스**

token — 파이썬 구문 분석 트리에 사용되는 상수

keyword — 파이썬 키워드 검사

tokenize — 파이썬 소스를 위한 토크나이저

pickletools — 피클 개발자를 위한 도구

​

​

**3.28 MS 윈도우 특정 서비스**

msvcrt — MS VC++ 런타임의 유용한 루틴

winreg — 윈도우 레지스트리 액세스

winsound — 윈도우용 소리 재생 인터페이스

​

​

**3.29 유닉스 특정 서비스**

posix — 가장 일반적인 POSIX 시스템 호출

pwd — 암호 데이터베이스

tty — 터미널 제어 함수

resource — 자원 사용 정보

syslog — 유닉스 syslog 라이브러리 루틴

​

**​**

4\. 참조 URL

보다 자세한 내용은 아래의 URL을 참고한다.

<https://docs.python.org/ko/3/library/index.html>

[ **파이썬 표준 라이브러리 — Python 3.10.4 문서** 파이썬 표준 라이브러리 파이썬 언어 레퍼런스 는 파이썬 언어의 정확한 문법과 의미를 설명하고 있지만, 이 라이브러리 레퍼런스 설명서는 파이썬과 함께 배포되는 표준 라이브러리를 설명합니다. 또한, 파이썬 배포판에 일반적으로 포함되어있는 선택적 구성 요소 중 일부를 설명합니다. 파이썬의 표준 라이브러리는 매우 광범위하며, 아래 나열된 긴 목차에 표시된 대로 다양한 기능을 제공합니다. 라이브러리에는 일상적인 프로그래밍에서 발생하는 많은 문제에 대한 표준적인 해결책을 제공하는 파이썬으로 작성된 모듈뿐만 아니라, 파일 I/O와 같은 시스템 ... docs.python.org ](https://docs.python.org/ko/3/library/index.html)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#파이썬표준라이브러리 #PythonStandardLibrary #프로그래밍도구 #파이썬모듈 #파이썬프로그래밍 #데이터처리라이브러리 #파일처리모듈 #파이썬라이브러리활용 #프로그래밍강의자료 #파이썬입문 #프로그래밍팁 #파이썬레퍼런스 #파이썬학습 #코딩효율성 #데이터분석모듈 #파이썬시작하기 #프로그래밍도구활용 #파이썬개발환경 #Python기본모듈 #프로그래밍입문자 #파이썬활용사례 #파이썬문서 #파이썬디버깅 #프로그래밍테스트 #파이썬암호화 #파이썬네트워크모듈 #웹개발도구 #파이썬데이터베이스 #파이썬시간관리 #파이썬코딩 #파이썬프레임워크

![](https://blogfiles.pstatic.net/MjAyMzA3MjBfMjMg/MDAxNjg5Nzg4NzcwMTM4._j8gbp8P26ywYg6c3eW9z83qALj9mITIKhMeb3Ut-Jgg.l4wB86sVmo4qWHZfBlBu2PTLIX3_a-XvLXyqTUmw-vAg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
