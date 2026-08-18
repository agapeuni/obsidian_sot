---
title: "2022-02-06 222640669547 장고(Django) - URL 매핑부터 View, Template까지"
type: blog-archive
status: active
created: 2022-02-06
updated: 2026-08-12
tags:
  - 개발·기술
  - naver-blog/archive
source: "https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222640669547&categoryNo=982"
source_blog: agapeuni
source_category: 982
log_no: 222640669547
published: "2022. 2. 6. 23:59"
body_hash: 609391e78a8801b87f6a85bdf567bed0380a720332168bb95573cd0d7006f553
visibility: private
rag: exclude
---
# 2022-02-06 222640669547 장고(Django) - URL 매핑부터 View, Template까지

- 원문: https://blog.naver.com/PostView.naver?blogId=agapeuni&logNo=222640669547&categoryNo=982
- 게시일: 2022. 2. 6. 23:59

## 본문

![](https://postfiles.pstatic.net/MjAyNTA0MTJfMTU5/MDAxNzQ0NDQ3MzgzODk4.beRyKctUXbLb4q4wdJBe2VdmLDS3qVtG8ntmizrp-Gsg.9JkZN63o3wHSYwuJ9NmgUob3zDUdtXPknsHpZo2e9Pog.PNG/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC-001_\(1\).png?type=w80_blur)

​

​

1\. 장고 개요

파이썬(Python)에서 가장 많이 사용하는 웹 프레임워크는 장고(Django)와 플라스크(Flask)이다. 크고 복잡한 업무 기반의 웹 프로젝트를 구현할 때는 장고(Django)가 좋고, 단위 기능의 서비스나 REST API 구현, 그리고 간단한 웹 프로젝트를 구현할 때는 플라스크(Flask)가 좋다.

​

장고(Django)는 Full Stack Framework로 지원하는 기능이 많다. ORM(Objeck Relational Mapping)기능이 내장되어 있고 Template 엔진도 제공한다. 웹 서비스를 구현하는데 있어서 필요한 것은 다 제공해 주고 있다고 봐도 된다. 반면 플라스크(Flask)는 Micro Framework로 심플하고 상당히 가볍고 심플하다. 확장 가능성이 높아 REST API 서비스를 만들거나 인증과 권한 및 OAuth를 구현하기에 편리하다.

​

장고와 플라스크는 많이 알려진 파이썬 웹 프레임워크이다. 장고에 관해 정리를 해보았다. 

![](https://postfiles.pstatic.net/MjAyMjAyMDZfNDQg/MDAxNjQ0MTU5NDE1NTk3.UI2Q-U_1jys58WcbkwKGE-CcYvO6_CfrjgiRTmNWeWcg.lC8U2TfLTgjJULICQVY83LSmSOx5FwMVnSrWyYXbqwEg.JPEG.agapeuni/1.jpg?type=w80_blur)

[이미지 출처] https://binaryinformatics.com/

​

2\. 장고(Django) 기능 요소

장고(Django) 웹 프레임워크를 사용하여 웹 프로그래밍을 할 때 구성하는 기능 요소 스택은 다음과 같다.

1\. 웹 클라이언트인 브라우저와 웹서버간의 요청과 응답

2\. Nginx는 웹 서버로 적정 파일을 서비스 (html, cs, js, image)

3\. 웹 서버와 uWSGI 간 소켓 통신

4\. uWSGI에서 동적인 어플리케이션을 처리

5\. Python 어플리케이션과 통신

6\. 데이터베이스와 ORM 연계

![](https://postfiles.pstatic.net/MjAyMjAyMDZfMjk2/MDAxNjQ0MTU5NDI1ODk5.Sk-7FcZmb62B3tJenYat91s8UISo6f5Q5UvpJk3JPa8g.HzVspcML95ISTKcIZCNb_KZasf2u2jgIFB4pb2IhJIcg.PNG.agapeuni/2.png?type=w80_blur)

[이미지 출처] <https://www.vndeveloper.com/>

​

Nginx(엔진엑스) : 웹 서비스를 위해 정말 필요한 기능인 웹 서버, 리버스 프록시 및 메일 프록시 기능을 제공

WSGI(Web Server Gateway Interface) : 웹 애플리케이션(파이썬)이 웹 서버와 통신하기 위한 인터페이스

​

​

​

3\. 플라스크(Flask) 기능 요소 스택

플라스크(Flask) 웹 프레임워크를 사용하여 웹 프로그래밍을 할 때 구성하는 것도 장고(Django)로 구성하는 것과 크게 다르지 않다.

![](https://postfiles.pstatic.net/MjAyMjAyMDZfMTE2/MDAxNjQ0MTU5NDMwNTg3.oF7NrdPRNrCrF6UpxfW2YdxbXxlu9qJTVWsd_Lwjmwsg.QkYq3qwT8jtBpMqJv-vSouWxVYXbsR2RidLXBzdf1sYg.PNG.agapeuni/3.png?type=w80_blur)

[이미지 출처] <https://eksyam.com/>

​

![](https://postfiles.pstatic.net/MjAyMjAyMDZfMTg0/MDAxNjQ0MTU5NDc0MTkx.k3nhAo3s5EWupRNo1q3dxp-J77l15dSUXCsacFEJIaEg.fS3oFbQIsrxypPDn3N_dTA0j0PVhxdkXEsq7Xo9hkTcg.PNG.agapeuni/4.png?type=w80_blur)

​

​

4\. 장고(Django) 코딩

장고(Django)는 요청 URL을 urlpatterns으로 적절한 View와 매핑하고 각각의 View(로직)에서 Template(화면 UI)을 지정하는 과정이 직관적이다. 실제 코딩도 "URL -> View -> Template" 순의 흐름으로 진행하는 것도 좋아 보인다.

from django.urls import path from polls import views app_name = 'polls' urlpatterns = [ path('', views.index, name='index'), path('<int:question_id>/', views.detail, name='detail'), path('<int:question_id>/results/', views.results, name='results'), path('<int:question_id>/vote/', views.vote, name='vote'), ]

​

from django.shortcuts import get_object_or_404, render from django.http import HttpResponseRedirect from django.urls import reverse from polls.models import Choice, Question def index(request): latest_question_list = Question.objects.all().order_by('-pub_date')[:5] context = {'latest_question_list': latest_question_list} return render(request, 'polls/index.html', context) def detail(request, question_id): question = get_object_or_404(Question, pk=question_id) return render(request, 'polls/detail.html', {'question': question}) def results(request, question_id): question = get_object_or_404(Question, pk=question_id) return render(request, 'polls/results.html', {'question': question})

​

<h1>{{ question.question_text }}</h1> {% if error_message %}<p><strong>{{ error_message }}</strong></p>{% endif %} <form action="{% url 'polls:vote' question.id %}" method="post"> {% csrf_token %} {% for choice in question.choice_set.all %} <input type="radio" name="choice" id="choice{{ forloop.counter }}" value="{{ choice.id }}" /> <label for="choice{{ forloop.counter }}">{{ choice.choice_text }}</label><br /> {% endfor %} <input type="submit" value="Vote" /> </form>

​

![](https://postfiles.pstatic.net/MjAyMjAyMDZfNCAg/MDAxNjQ0MTU5NDgyNzQw.CysIqx5UUVCI4AzR9aazf4EUix4_FN73pk1kc6kUqD4g.zbMu0y4kgxnLy13R2rBGQmk5ZBFY-BcbZXyfNh72PiQg.PNG.agapeuni/5.png?type=w80_blur)

​

​

![](https://postfiles.pstatic.net/MjAyNjA1MjRfMTkw/MDAxNzc5NjE2MDUxNTU3.gRdnv_P7S3FnhnNsQpBSyqmWFPl74Lp76KD6HCozerEg.xxFmn3g6bTUbMKKh8IJ2zsEr-KhIzG8ciXJSyny78X4g.PNG/%EC%A3%BC%ED%95%9C%EA%B8%B8.png?type=w966)

#Django #Flask #파이썬 #Python #웹프레임워크 #프로그래밍 #웹개발 #FullStackFramework #MicroFramework #ORM #장고코딩 #플라스크코딩 #웹서비스 #RESTAPI #uWSGI #Nginx #WSGI #웹서버 #템플릿엔진 #URL매핑 #장고View #플라스크View #데이터베이스연동 #OAuth #웹애플리케이션 #코딩튜토리얼 #프로그래밍언어 #백엔드개발 #웹사이트개발 #서버통신 #프론트엔드개발 #API #파이썬개발 #소프트웨어개발 #웹기술

![](https://blogfiles.pstatic.net/MjAyMzA3MDJfMzYg/MDAxNjg4MjI4MzIyMDgz.gC5i2c3XjZ6Z_QATcegyzH-dc3ysEAViB07dirwlPjMg.PvLO2rGeMsRZpHU3lbYFV6BIs7Nc2s6B6z79nHVma1kg.PNG.agapeuni/%ED%95%98%EB%8B%A8_365_%ED%95%9C%EA%B1%B8%EC%9D%8C%EC%94%A9-%EA%BE%B8%EC%A4%80%ED%95%98%EA%B2%8C.png?type=w1)

_다른 곳에 이용하실 때에는 출처를 밝혀 주세요._

_공감과 이웃추가는 좋은 글을 쓰는데 힘이 됩니다._
