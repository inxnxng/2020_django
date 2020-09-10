# 1. django
참고 : [https://wikidocs.net/78004](https://wikidocs.net/78004)

- [1. django](#1-django)
  - [1.1. 관련 지식 쌓고 가기](#11-관련-지식-쌓고-가기)
    - [1.1.1. 프레임워크](#111-프레임워크)
    - [1.1.2. django의 장점](#112-django의-장점)
    - [1.1.3. 가상환경(virtualenv)](#113-가상환경virtualenv)
  - [1.2. django 시작하기](#12-django-시작하기)
    - [프로젝트 생성](#프로젝트-생성)

## 1.1. 관련 지식 쌓고 가기
[overview](https://www.djangoproject.com/start/overview/)
> The web framework for perfectionists with deadlines.

### 1.1.1. 프레임워크
* [웹 프레임워크](https://ko.wikipedia.org/wiki/%EC%9B%B9_%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC) (Web Framework)
    동적인 웹 페이지나, 웹 애플리케이션, 웹 서비스 개발 보조용으로 만들어지는 애플리케이션 프레임워크의 일종. 웹 페이지를 개발하는 과정을 쉽게 도와주는 것이 목적이며 통상 **데이터베이스 연동, 템플릿 형태의 표준, 세션 관리, 코드 재사용**의 기능을 포함하고 있다.

* [애플리케이션 프레임워크](https://ko.wikipedia.org/wiki/%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98_%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC) (Application Framework)
    소프트웨어 개발자가 응용 소프트웨어의 표준 구조를 구현하기 위해 사용하는 소프트웨어 프레임워크로 구성된다. **프로그래밍에서 특정 운영 체제를 위한 응용 프로그램 표준 구조를 구현하는 클래스와 라이브러리 모임**

* [소프트웨어 프레임워크](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC) (software framework)
    복잡한 문제를 해결하거나 서술하는 데 사용되는 기본 개념 구조. 뼈대, 골조, 프레임워크(framework)라고 함.

* [프레임워크](https://m.blog.naver.com/manddonara/119738492)
    애플리케이션 개발에 바탕이 되는 템플릿과 같은 역할을 하는 **클래스들과 인터페이스의 집합**

### 1.1.2. django의 장점
* 빨리 만들 수 있다 (Ridiculously fast)
    ```python
    def index(request):
        return HttpResponse("Hello World")
    ```
* 안전하다 (Reassuringly secure)
    정보보안의 issues
* 기능이 많다 (Fully loaded, Exceedingly scalable, Incredibly versatile)

### 1.1.3. 가상환경(virtualenv)
python 가상환경은 파이썬 프로젝트를 진핼할 때 독립적인 환경을 만들어줌 -> 서로 다른 버전의 파이썬과 라이브러리들에 대해 걱정할 필요 없음

* 가상환경으로 진입
    ```
    C:\venvs>cd C:\venvs\mysite\Scripts
    C:\venvs\mysite\Scripts> activate
    (mysite) C:\venvs\mysite\Scripts>
    ```
* 가상환경에서 벗어나려면 `deactivate`

장고는 하나의 project에 하나의 web site를 생성함 project 안에는 여러 개의 app이 존재함.

## 1.2. django 시작하기

### 프로젝트 생성
```
C:\Users\pahke>cd \
C:\>mkdir projects
C:\>cd projects
C:\projects>
```

루트 디렉터리를 생성하여 projects 디렉터리를 생성하고 다음과 같이 입력하여 django-admin을 통해 장고 프로젝트를 생성한다

```
(mysite) C:\projects\mysite>django-admin startproject config .
```
또는
```
(mysite) C:\projects> django-admin startproject mysite
```
여기서 결과로 다음과 같이 나타난다. `python manage.py runserver` 입력을 하면 장고서버가 실행되어 localhost를 통해 결과 웹 사이트를 확인할 수 있다.

```

...

Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```
