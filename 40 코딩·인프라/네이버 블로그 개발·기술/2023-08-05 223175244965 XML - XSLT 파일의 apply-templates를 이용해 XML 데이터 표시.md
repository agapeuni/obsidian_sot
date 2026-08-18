---
title: "2023-08-05 223175244965 XML - XSLT 파일의 apply-templates를 이용해 XML 데이터 표시"
type: blog-archive
status: active
created: 2023-08-05
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223175244965&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 223175244965
published: "2023. 8. 5. 5:00"
body_hash: fb2ef973469686fc3f7b942ac62d9598731cf04663518739f314bead96230153
visibility: private
rag: exclude
---
# 2023-08-05 223175244965 XML - XSLT 파일의 apply-templates를 이용해 XML 데이터 표시

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=223175244965&categoryNo=982
- 게시일: 2023. 8. 5. 5:00

## 본문

![](https://postfiles.pstatic.net/MjAyNDA1MTJfNDEg/MDAxNzE1NDQxNzA3MTU1.O3_VCBQAvBCakBDl-kP4pLGgFXZRNKiFFG5fNx71VLQg.afwHOST0WN5pJ6xhls3w7Awx55aat0pm3RD2AGTmzjwg.PNG/XML-001_\(5\).png?type=w80_blur)

​

**1\. XML 문서**

XSLT 파일의 apply-templates를 이용하여 XML 문서의 내용을 조건에 따라 분기해서 표시해 보자.

​

아래의 XML 파일은 CD 목록을 관리하고 있고 cd_list_apply.xsl 파일을 스타일시트로 읽고 있다.

**파일 : cd_list_apply.xml**

<?xml version="1.0" encoding="ISO-8859-1"?> <?xml-stylesheet type="text/xsl" href="cd_list_applyi.xsl"?> <catalog> <cd> <title>Hide your heart</title> <artist>Bonnie Tyler</artist> <country>UK</country> <company>CBS Records</company> <price>9.90</price> <year>1988</year> </cd> <cd> <title>Greatest Hits</title> <artist>Dolly Parton</artist> <country>USA</country> <company>RCA</company> <price>9.90</price> <year>1982</year> </cd> <cd> <title>Still got the blues</title> <artist>Gary Moore</artist> <country>UK</country> <company>Virgin records</company> <price>10.20</price> <year>1990</year> </cd> <cd> <title>Maggie May</title> <artist>Rod Stewart</artist> <country>UK</country> <company>Pickwick</company> <price>8.50</price> <year>1990</year> </cd> <cd> <title>When a man loves a woman</title> <artist>Percy Sledge</artist> <country>USA</country> <company>Atlantic</company> <price>8.70</price> <year>1987</year> </cd> <cd> <title>For the good times</title> <artist>Kenny Rogers</artist> <country>UK</country> <company>Mucik Master</company> <price>8.70</price> <year>1995</year> </cd> <cd> <title>Tupelo Honey</title> <artist>Van Morrison</artist> <country>UK</country> <company>Polydor</company> <price>8.20</price> <year>1971</year> </cd> <cd> <title>Pavarotti Gala Concert</title> <artist>Luciano Pavarotti</artist> <country>UK</country> <company>DECCA</company> <price>9.90</price> <year>1991</year> </cd> <cd> <title>Picture book</title> <artist>Simply Red</artist> <country>EU</country> <company>Elektra</company> <price>7.20</price> <year>1985</year> </cd> <cd> <title>Unchain my heart</title> <artist>Joe Cocker</artist> <country>USA</country> <company>EMI</company> <price>8.20</price> <year>1987</year> </cd> </catalog>

​

**2\. XSLT 파일**

XSLT 파일을 보면 <body> 태그 안에**<****xsl:apply-templates****/ >**가 선언되어 있다.

<body>

<h2>My CD List</h2>

**<****xsl:apply-templates****/ >**

</body>

template에 대한 apply-templates는 아래와 같이 정의되어 있다.

**<****xsl:template****match** =_"cd"_**>**

<p>

**<****xsl:apply-templates****select** =_"title"_**/ >**

**<****xsl:apply-templates****select** =_"artist"_**/ >**

**<****xsl:apply-templates****select** =_"company"_**/ >**

**<****xsl:apply-templates****select** =_"price"_**/ >**

</p>

**< /****xsl:template****>**

그 아래에 각각에 template에 대하여 정의되어 있는 구조이다.

**<****xsl:template****match** =_"title"_**>**

**<****xsl:template****match** =_"artist"_**>**

**<****xsl:template****match** =_"company"_**>**

**<****xsl:template****match** =_"price"_**>**

​

XSLT 파일의 전체 코드는 아래와 같습니다.

**파일: cd_catalog_apply.xsl**

<?xml version="1.0" encoding="ISO-8859-1"?> <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"> <xsl:template match="/"> <html> <body> <h2>My CD List</h2> <xsl:apply-templates /> </body> </html> </xsl:template> <xsl:template match="cd"> <p> <xsl:apply-templates select="title" /> <xsl:apply-templates select="artist" /> <xsl:apply-templates select="company" /> <xsl:apply-templates select="price" /> </p> </xsl:template> <xsl:template match="title"> >>> >>> >>> >>> >>> >>> >>> >>> <br /> Title: <span style="color:#ff0000"> <xsl:value-of select="." /> </span> <br /> </xsl:template> <xsl:template match="artist"> Artist: <span style="color:#0000ff"> <xsl:value-of select="." /> </span> <br /> </xsl:template> <xsl:template match="company"> Company: <span style="color:#717171"> <xsl:value-of select="." /> </span> <br /> </xsl:template> <xsl:template match="price"> Price: <span style="color:#ff00ff"> <xsl:value-of select="." /> </span> <br /> <![CDATA[<<< <<< <<< <<< <<< <<< <<< <<< ]]> </xsl:template> </xsl:stylesheet>

​

**3\. 웹으로 확인**

XML 파일을 브라우저에서 열면 XSLT 파일이 적용되어 아래와 같이 표시된다.

![](https://postfiles.pstatic.net/MjAyMzA4MDVfMjEw/MDAxNjkxMTY1MjU1MjM0.W_Kr4u72nEPMoNdH9eq_cvPnEw0nYaElO0F1wDMYMCkg.dbBxSA-lYcUZj9nOY8pE_WHUwEvQEkMl1JyywXRyzWEg.PNG.agapeuni/img.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#XML #XSLT #XML문서 #CD목록 #데이터변환 #웹개발 #프론트엔드 #HTML #스타일시트 #데이터표현 #프로그래밍 #코딩 #웹디자인 #웹프로그래밍 #기술블로그 #소프트웨어개발 #디지털미디어 #컴퓨터과학 #정보기술 #개발자 #코드예제 #프로그래밍팁 #웹개발자 #XSLT적용 #CD리스트 #XML파서 #스타일링 #소스코드 #프로그래밍공부

![](https://postfiles.pstatic.net/MjAyMzA4MDVfNjMg/MDAxNjkxMTY0NjA2Mjk1.Lw9suJNQCYYi9QVOMBzljtiZd-PH6nIyNX1ZhyLlHdQg.5G5Tu7R18ktZge0JCsjh5gAej6h0tFxjg5wsICPiKuwg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w80_blur)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
