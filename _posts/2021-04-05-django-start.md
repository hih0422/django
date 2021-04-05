---
layout: post
title: Django start
subtitle : django settings
author: Seongmin Kim
comments : False
---

Django는 Python 기반의 웹 프레임워크입니다. 브라우저로 부터 받는 HTTP Request에 대한 정보를 토대로 다음에 필요한 데이터를 불러와 작업을 수행합니다.
그 다음으로 웹 어플리케이션은 브라우저에 Response를 반환하는데 주로 동적 HTML 페이지를 생성합니다.

![Basic django Logo](/assets/img/basic-django.png)

<br>

{% highlight html %}
 장고는 이 구조를 "모델 뷰 템플릿(MVT)" 아키텍쳐라 칭합니다.
{% endhighlight %}

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
