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

