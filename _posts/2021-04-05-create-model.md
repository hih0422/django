---
layout: post
title: Django Create Model
subtitle : django create model and connect Database
author: Seongmin Kim
comments : False
---

이전 포스팅에서는 새로운 app 생성 및 url, view, template 연결까지 알아보았습니다.
이어서 model을 생성하고 db를 연결해보겠습니다.

<br>

<h1> 1. Model 생성 및 Migration </h1>

faq 앱 안의 models.py를 열어 아래와 같이 수정해줍니다.
{% highlight html %}
from django.db import models

# Create your models here.

class Post(models.Model):
    title = models.CharField(max_length=50)
    contents = models.TextField()

    # 게시글 제목을 title로 보여줌
    def __str__(self):
        return self.title
{% endhighlight %}

Post라는 class를 선언하여 그 안에 게시판에 등록할 title과 contents 필드를 만들어 줍니다.
여기서 title은 모델의 Char 형태, contents는 TextField 형태로 선언해 주었습니다.
기타 다른 형태도 많이 지원하니 찾아서 적용해보시는 것도 좋을 것 같습니다.

<br>

여기까지 완료 되셨다면 모델을 migrate 해주셔야 합니다.
{% highlight html %}
python manage.py makemigrations faq
python manage.py migrate
{% endhighlight %}

위 명령어를 치시면 모델이 생성되는 것을 확인 하실 수 있습니다.

<br>

<h1> 2. Admin을 통한 model 접근 </h1>

django에서는 admin을 통한 데이터 CRUD가 가능합니다. 그렇게 하기 위해서는 몇가지 추가가 필요합니다.

faq앱의 admin.py을 열어줍니다.
Post 모델을 import하여 admin site에 등록하여줍니다.
{% highlight html %}
from django.contrib import admin
from .models import Post

# Register your models here.

admin.site.register(Post)
{% endhighlight %}

<br>

이제 admin site에 접속을 해야 하는데, 먼저 admin 계정을 만들어줘야합니다.
{% highlight html %}
python manage.py createsuperuser
{% endhighlight %}

해당 명령어를 입력후 super user로 사용할 계정을 만들어줍니다.
그리고 http://127.0.0.1:8000/admin 에 접속하셔서 만드신 super user 계정으로 로그인하시면
화면에 Posts라고 적힌 부분을 확인하실 수 있습니다.
그 옆에 Add 버튼을 누르면 Model에 생성해 주었던 title 과 contents를 추가할 수 있게 되어있습니다.
몇개 정도 추가를 해주시고 이제 추가한 내용을 페이지에 출력해 보겠습니다.

<br>

faq 앱의 views.py로 이동합니다.
기존에 적어두었던 index 함수를 아래와 같이 변경합니다.

{% highlight html %}
from django.shortcuts import render
from django.http import HttpResponse
from .models import Post

# Create your views here.

def index(request):

    ## Post 모델의 모든 object를 가져온다
    post = Post.objects.all()

    ## faq.html에 가져온 post object를 json 형태로 넘겨준다
    return render(request, 'faq.html', {'post':post})
{% endhighlight %}

<br>


그리고 faq.html로 이동하여 아래와 같이 적어줍니다.

{% highlight html %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h1>게시판페이지</h1>
    <table>
        {% for list in post %}
            <ul>
                <li>{{ list.title }}</li>
                <li>{{ list.contents }}</li>
            </ul>
        {% endfor %}
    </table>
</body>
</html>
{% endhighlight %}

이제 admon에서 등록했던 title과 contents 내용이 화면에 출력되는 것을 확인하실 수 있습니다.





