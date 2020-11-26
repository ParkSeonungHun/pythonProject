# pythonProject

## 프로젝트 개요

## 프로젝트 일정 상세
- 아래는 일자별로 업데이트 한 프로젝트 상세 일정에 관한 내용입니다. 
- 추가된 주요 코드 및 스샷을 참조하시기를 바랍니다. 

### 11월 25일 
- 추가된 기능: 포토 업로드 기능 구현
- `models.py` 수정
- `urls.py` 수정
- `views.py` 수정
- `base.html` 수정
- `photo/photo_form.html` 생성
- `photo/templates/photo/photo_change_list.html` 생성
- `photo/photo_confirm_delete.html` 생성
- `photo/album_form.html` 생성
- `photo/album_change_list.html` 생성
- `photo/album_confirm_delete.html` 생성
```python
. # photo models.py owner 필드 추가
. class Album(models.Model):
      name = (생략)
      description = (생략)
      owner = models.ForeignKey('auth.User', on_delete= models.CASCADE, verbose_name='OWNER',blank=True, null=True) # 추가
. class Photo(models.Model):
      album = (생략)
      title = (생략)
      description= (생략)
      image = (생략)
      upload_dt = (생략)
      owner = models.ForeignKey('auth.User', on_delete=models.CASCADE, verbose_name='OWNER',blank=True, null=True) # 추가
      
. #urls.py 9개의 path 추가
. # Example: /photo/album/add/
. path('album/add/', view.AlbumPhotoCV.as_view(), name='album_add'),
. #photo/view.py 6개 라인코딩, 8개 클래스형 뷰 추가
. from django.contrib.auth.mixins import LoginRequiredMixin #등 6개 추가
. class PhotoCV(LoginRequiredMixin, CreateView):
      model = photo
      fields = ('album', 'title', 'image', 'description')
      success_url = reverse_lazy('photo:index')

      def form_valid(self,form):
          form.instance.owner = self.request.user
          return super().form_valid(form) # 등 8개 클래스형 뷰 추가
```
- 금일 업데이트 된 기능 

![](/img/1125.PNG)

### 11월 26일
-추가된 기능 : aws를 이용한 배포화 예정

- 금일 업데이트 된 기능

![](/img/1126.PNG)


