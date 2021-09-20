# Django05

### Authentication system

- Authentication(인증), Authorization(권한)

- accounts앱을 만들어서 유저 관리

#### 쿠키

- 서버는 비연결지향! 지속적 관계 유지를 위해 쿠키와 세션이 존재
- 서버가 사용자의 웹브라우저에 전송하는 작은 데이터 조각
- 상태가 있는 세션을 만들어줌
- application 에 cookies
- 사용목적
  - 세션관리 (로그인, 공지 안보기, 팝업체크)
  - 개인화 (사용자 선호, 테마)
  - 트래킹 (사용자 행동 기록 분석)

#### 세션

- 상태 유지시키는 것
- 세션 아이디를 쿠키에 저장
- ex) 로그인, 장바구니 등

1. 로그인
2. 로그인성공 (사이트에서 session id를 줌)
3. 다른 곳 클릭할때마다 서버에 session id와 함께 전달

#### Session in Django

- 장고 세션은 미들웨어를 통해 구현

#### Middleware

- http 요청과 응답 처리 중간에 작동하는 시스템
- http 요청 -> 미들웨어 -> url -> view
- 주로 데이터 관리, 애플리케이션 서비스, 메시징, 인증 및 API관리 담당

#### 로그인 사용자 접근 제한

- is_authenticated

```html
<!-- base.html --!>

{% if request.user.is_authenticated %}
	<h3> hello, {{ user }}</h3>
{% else %}
{% endif %}
```

```python
def login(request):
    if request.user.is_authenticated:
        return redirect('articles:index')
```

- login_required decorator



### 실사용

```python
# accounts/views.py
from django.shortcuts import redirect, render
from django.contrib.auth import login as auth_login
from django.contrib.auth import logout as auth_logout
from django.contrib.auth.forms import (
    AuthenticationForm, 
    UserCreationForm, 
    PasswordChangeForm
)
from django.views.decorators.http import require_http_methods, require_POST
from django.contrib.auth import update_session_auth_hash
from django.contrib.auth.decorators import login_required
from .forms import CustomUserChangeForm

# Create your views here.
@require_http_methods(['GET', 'POST'])
def login(request):
    if request.user.is_authenticated:
        return redirect('articles:index')

    if request.method == 'POST':
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            # 로그인 !
            auth_login(request, form.get_user())
            return redirect(request.GET.get('next') or 'articles:index')
    else:
        form = AuthenticationForm()
    context = {
        'form': form,
    }
    return render(request, 'accounts/login.html', context)


@require_POST
def logout(request):
    if request.user.is_authenticated:
        auth_logout(request)
    return redirect('articles:index')


@require_http_methods(['GET', 'POST'])
def signup(request):
    if request.user.is_authenticated:
        return redirect('articles:index')

    if request.method == 'POST':
        form = UserCreationForm(request.POST)
        if form.is_valid():
            user = form.save()
            auth_login(request, user)
            return redirect('articles:index')
    else:
        form = UserCreationForm()
    context = {
        'form': form,
    }
    return render(request, 'accounts/signup.html', context)


@require_POST
def delete(request):
    if request.user.is_authenticated:
        request.user.delete()
        auth_logout(request)
    return redirect('articles:index') 


@login_required
@require_http_methods(['GET', 'POST'])
def update(request):
    if request.method == 'POST':
        form = CustomUserChangeForm(request.POST, instance=request.user)
        if form.is_valid():
            form.save()
            return redirect('articles:index')
    else:
        form = CustomUserChangeForm(instance=request.user)
    context = {
        'form': form,
    }
    return render(request, 'accounts/update.html', context)


@login_required
@require_http_methods(['GET', 'POST'])
def change_password(request):
    if request.method == 'POST':
        form = PasswordChangeForm(request.user, request.POST)
        if form.is_valid():
            form.save()
            update_session_auth_hash(request, form.user)
            return redirect('articles:index')
    else:
        form = PasswordChangeForm(request.user)
    context = {
        'form': form,
    }
    return render(request, 'accounts/change_password.html', context)

```

```python
# accounts/forms.py
from django.contrib.auth.forms import UserChangeForm
from django.contrib.auth import get_user_model


class CustomUserChangeForm(UserChangeForm):

    class Meta:
        model = get_user_model()
        fields = ('email', 'first_name', 'last_name',)

```

```ht
{% extends 'base.html' %}

{% block content %}
  <h1>Login</h1>
  <form action="" method="POST">
    {% csrf_token %}
    {{ form.as_p }}
    <input type="submit">
  </form>
{% endblock content %}

```

