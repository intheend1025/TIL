# Django04

### Managing static files

#### static files

- 응답할 때 별도 처리 없이 내용을 그대로 보여주면 되는 파일 (이미지, 자바스크립트, CSS)
- `django.contrib.staticfiles`가 INSTALLED_APPS에 포함되어 있는지 확인 (보통 포함되어있음)
- `STATIC_URL` 정의
- 템플릿에서 `{% load static %}` 선언 후 `<img src="{% static 'my_app/example.jpg'%}"`
- 앱의 static폴더에 정적 파일 저장

#### STATIC_ROOT

- collectstatic이 배포를 위해 정적 파일을 수집하는 디렉토리의 절대 경로

#### Media file

- 사용자가 웹에서 업로드하는 정적 파일

- `ImageField` 이미지 업로드에 사용하는 모델 필드 (Filefield의 서브클래스) (Pillow 라이브러리 필요)

- `FileField` 파일 업로드에 사용하는 모델 필드 (선택인자 upload_to, storage)

  ```python
  # 1 업로드할 곳 지정 가능
  class MyModel(models.Model):
      upload = models.FileField(upload_to='uploads/')
      upload = models.FileField(upload_to='uploads/%Y/%m/%d/')
  
  # 2 함수를 통해 별도 경로 지정 가능
  def articles_images_path(instance, filename):
      return f'user_{instance.user.pk}/{filename}'
  
  class Article(models.Model):
      image = models.ImageField(upload_to=articles_image_path)
  ```

  

#### 사용하기 전 몇 단계

- settings.py에 `MEDIA_ROOT = BASE_DIR / 'media'`, `MEDIA_URL = '/media/'` 설정

- 업로드 된 파일 경로는 {{ article.image.url }}

- 앱내 urls.py에

  ```python
  from django.conf import settings
  from django.conf.urls.static import static
  
  urlpatterns = [
      
  ] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
  ```

- create html에 form태그에 `enctype='multipart/form-data'` 속성 지정

- Views.py에서 `form = ArticleForm(request.POST, request.FILES)` 추가



#### 이미지 크기 변경

- django-imagekit 라이브러리 활용