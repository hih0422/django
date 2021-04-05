---
layout: post
title: Django Create App
subtitle : django create app
author: Seongmin Kim
comments : False
---

이전 포스팅에서 django 프로젝트를 생성하고 서버를 돌려 django의 기본 화면을 띄우는데 까지 진행하였습니다.
이번 포스팅에서는 첫 화면을 띄우는데 까지 진행하겠습니다.
django 프로젝트 내부에는 여러개의 app이 존재합니다. app은 각 기능별로 구현된다고 생각하시면 될 것 같습니다.
제 프로젝트는 django를 활용하여 bootstrap을 연결하고 소셜 로그인, 게시판 메뉴등 웹페이지에서 기본적으로 사용되는 기능들을 구현할 것 입니다.

<br>

<h1> 1. APP 생성 </h1>

먼저 app을 하나 생성해 줍니다. 게시판 기능을 구현하기 위한 app을 생성하도록 하겠습니다.

{% highlight html %}
python manage.py startapp faq
{% endhighlight %}

명령어를 입력 하면 faq라는 디렉토리가 생성된 것을 확인하실 수 있습니다.
<br>

![Create app](/django/assets/img/create_app.PNG)

<br>

위와 같이 생성되었다면 이제부터 기능 별 구현은 app을 생성한 디렉토리 내에서,
전체적인 설정은 myproject 내에서 구현한다고 생각하시면 될 것 입니다.

<br>

<h1> 2. url 및 view </h1>
urls.py 의 설정은 브라우저에 입력한 주소의 경로를 연결해주는 설정 파일입니다.
먼저 전체 설정을 한다고 했던 myproject안의 urls.py 파일을 열어줍니다.

해당 설정파일에서 아래 부분을 추가해줍니다.
{% highlight html %}
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('faq.urls'))
]
{% endhighlight %}

http://127.0.0.1:8000/ 로 들어왔을때 faq 앱의 urls.py 파일을 참조한다는 내용입니다. 

<br>
위의 url 입력을 마치셨다면, 생성해 두었던 faq 디렉토리에 방금전 수정했던 myproject 디렉토리의 urls.py 파일을 복사하여 붙여넣습니다.

faq 앱의 urls.py 내용은 아래와 같이 수정합니다.

{% highlight html %}
from django.urls import path
from . import views

urlpatterns = [
    path('faq', views.index),
]
{% endhighlight %}

여기서는 faq 경로로 들어오는 요청을 화면을 보여주기 위한 views로 연결해 줍니다.
views.index는 views.py 파일의 index 함수를 호출합니다.


<br>
faq 폴더 안에 있는 views.py로 이동하셔서 아래처럼 수정해줍니다.
우리는 views 안에서 요청된 데이터(request를 사용해 받는)의 가공, 모델과의 연결 등 데이터에 관련된 작업들을 진행 할 것입니다.
{% highlight html %}
from django.shortcuts import render
from django.http import HttpResponse

# Create your views here.

def index(request):
    return HttpResponse("faq screen")
{% endhighlight %}

index 함수가 호출되어 HttpResponse을 return 해주어 바로 화면에 faq screen을 보여주지만, return은 redirect를 해 줄 수도 있고, 여러가지 형태가 존재합니다.

<br>

여기까지 진행하였으면, http://127.0.0.1:8000/faq 화면에 faq screen 이라는 문자가 찍히는것을 확인 하실 수 있습니다.
확인이 되셨다면
views.py의 index 함수를 아래처럼 변경합니다.

{% highlight html %}
def index(request):
    return render(request, 'faq.html')
{% endhighlight %}

index로 들어온 요청을 faq.html로 연결해주는 내용입니다.
faq.html의 경로는 faq app아래 templates라는 폴더를 만들어 주시고 그 안에 faq.html을 생성해줍니다.

<br>

django의 앱 생성 및 url, view에 관해 간단하게 살펴보았습니다.

다음 포스팅에는 모델 생성 및 DB 연결을 진행해 보도록 하겠습니다.
