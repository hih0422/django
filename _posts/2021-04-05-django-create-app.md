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

먼저 app을 하나 생성해 줍니다. 게시판 기능을 구현하기 위한 app을 생성하도록 하겠습니다.

{% highlight html %}
python manage.py startapp faq
{% endhighlight %}

명령어를 입력 하면 faq라는 디렉토리가 생성된 것을 확인하실 수 있습니다.
![Basic django Logo](/django/assets/img/create_app.PNG)
<br>

디테일한 내용은 추후 포스트에서 다루고 장고 Setting을 시작하겠습니다.

<br>

먼저, Python이 설치되어 있다는 가정하에 시작하겠습니다.
Python 3.x 이상을 사용해주세요.

{% highlight html %}
pip3 install django // 장고설치

장고 설치 완료후 설치가 잘 되었는지 확인
# Linux/macOS X
python3 -m django --version
 2.0

# Windows
py -3 -m django --version
 2.0
{% endhighlight %}

<br>

설치가 잘 되었다면 django를 시작할 프로젝트 경로에서 입력해주세요.
{% highlight html %}
django-admin startproject myproject
{% endhighlight %}

여기까지 완료 하였으면 myproject라는 장고 프로젝트가 생성되고 프로젝트 안에 아래처럼 경로가 생성되었을 것입니다.
{% highlight html %}
myproject
 - myproject
  -- __init__.py
  -- asgi.py
  -- settings.py
  -- urls.py
  -- wsgi.py
 - manage.py
{% endhighlight %}

정상적으로 설치된것이 확인되었으면 manage.py가 있는 경로에서

{% highlight html %}
$ python manage.py runserver
Watching for file changes with StatReloader
[05/Apr/2021 14:38:18] "GET / HTTP/1.1" 200 16351
[05/Apr/2021 14:38:18] "GET /static/admin/css/fonts.css HTTP/1.1" 200 423
[05/Apr/2021 14:38:18] "GET /static/admin/fonts/Roboto-Regular-webfont.woff HTTP/1.1" 304 0
[05/Apr/2021 14:38:18] "GET /static/admin/fonts/Roboto-Bold-webfont.woff HTTP/1.1" 304 0
[05/Apr/2021 14:38:18] "GET /static/admin/fonts/Roboto-Light-webfont.woff HTTP/1.1" 304 0
{% endhighlight %}

가 나오면 정상적으로 django 서버가 실행된 것입니다.
http://127.0.0.1:8000 으로 접속하시면 정상적으로 설치되었다는 문구와 함께 django 기본 페이지가 뜨는것을 확인하실 수 있습니다.
