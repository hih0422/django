
---
layout: post
title: Django Create Model
subtitle : django create model and connect DB
author: Seongmin Kim
comments : False
---

이전 포스팅에서는 새로운 app 생성 및 url, view, template 연결까지 알아보았습니다.
이어서 model을 생성하고 db를 연결해보겠습니다.

<br>

faq 앱 안의 models.py를 열어 아래와 같이 수정해줍니다.
{% highlight html %}
from django.db import models

# Create your models here.

class Post(models.Model):
    title = models.CharField(max_length=50)
    contents = models.TextField()
{% endhighlight %}

Post라는 class를 선언하여 그 안에 게시판에 등록할 title과 contents 필드를 만들어 줍니다.
여기서 title은 모델의 Char 형태, contents는 TextField 형태로 선언해 주었습니다.
기타 다른 형태도 많이 지원하니 찾아서 적용해보시는 것도 좋을 것 같습니다.

