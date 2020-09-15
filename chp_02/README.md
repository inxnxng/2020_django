# 02장 장고 기초
참고 : https://wikidocs.net/73306

## URL과 뷰
* 장고의 urls.py 파일은 페이지 요청이 발생하면 가장 먼저 호출되는 파일로 URL과 뷰(views.py) 함수간의 매핑을 정의한다
* 장고에서 views.py를 뷰라고 부른다

\[../pybo/urls.py]
```python
from django.contrib import admin
from django.urls import path
from pybo import views              #pybo라는 라이브러리에서 가져와
urlpatterns = [
    path('admin/', admin.site.urls),
    path('pybo/', views.index),     #'pybo/'라는 path를 추가함
]
```
`pybo/`라는 URL이 요청되면 `views.index`를 호출하라는 매핑을 추가한 것이다.
여기서 `views.index`는 views.py라는 파일의 index함수를 의미한다

실제로 요청되는 URL은 `http://localhost:8000/pybo` 이지만 호스트명(localhost)과 포트(8000)가 생략된 URL인 `pybo/`로 매핑해야한다. 호스트명과 포트는 서버에 따라 바뀌기 때문

\[../pybo/views.py]
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("안녕하세요 pybo에 오셨습니다")
```
HttpResponse는 HTTP 요청에 대한 응답을 할 때 쓰는 장고 함수이다. index함수의 매개변수 `request`는 **장고 프레임워크에 의해 자동으로 전달되는 HTTP 요청 객체**이다.

![first_django](images/firstdjango.png)

### URL의 분리

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('pybo/', include('pybo.urls')),
]
```
`include`를 통해 `/pybo` 이하의 디렉토리가 추가되더라도 `pybo/urls.py`만 수정해주면 된다!

## 모델

장고는 모델(Model)을 이용하여 데이터베이스를 처리한다. without SQL 쿼리문

[django로 블로그 model 만들기](https://velog.io/@hidaehyunlee/Django-%EB%B8%94%EB%A1%9C%EA%B7%B8-model-%EB%A7%8C%EB%93%A4%EA%B8%B0)

[장고 ORM과 쿼리셋](https://tutorial.djangogirls.org/ko/django_orm/)

[ORM?](https://medium.com/@jsh901220/django%EC%99%80-cookiecutter-django-%EA%B0%84%EB%8B%A8-%EC%84%A4%EB%AA%85-898d063d38ff)
    -> 객체의 관게를 연결해주는 것으로 객체 지향적인 방법을 사용하여 데이터베이스의 데이터를 쉽게 조작할 수 있게 해준다

\[models.py]
```python
from django.db import models


class Question(models.Model):
    # 제목은 최대 200자
    # 글자수가 제한된 텍스트는 CharField
    subject = models.CharField(max_length=200)
    # 글자수를 제한할 수 없는 텍스트는 TextField
    content = models.TextField()
    create_date = models.DateTimeField()


class Answer(models.Model):
    # ForeignKey는 다른 모델과의 연결
    # on_delete=models.CASCADE는 이 답변과 연결된 질문이 삭제될 경우 답변도 삭제된다는 뜻
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    content = models.TextField()
    create_date = models.DateTimeField()

```
* `ForeignKe`y는 다른 모델과의 연결
* `on_delete=models.CASCADE`는 이 답변과 연결된 질문이 삭제될 경우 답변도 삭제된다는 뜻

[filter을 통해 개발하기; 공식 사이트](https://docs.djangoproject.com/en/3.0/topics/db/queries/)

### 실습해보기
* `연결모델명_set`(
    여기서는 answer_set) 은 질문 하나에 여러개의 답변이 가능할 것이므로 q.answer_set이 가능하지만 답변 하나에는 여러개의 질문이 있을 수 없으므로 question_set은 불가능하다. 대신 a.question은 가능