# django_router
Resource routing allows you to quickly declare all of the common routes for a given resourceful controller. Instead of declaring separate routes for your index... a resourceful route declares them in a single line of code.
— Ruby on Rails Documentation

In short if you get out of rid defining differnet urls in drf then we use router.with the help of router we can easliy acees all rest operation in just defining one url.

### Algorithm for creating router with classbased view.

step1: create model and register with admin.

step2: create serializer.py file inside project dir then write code .


```
from rest_framework import serializer
from .models import model name

class nameSerializer(serializer.HyperlinkedModelSerializer):
   # here HyperlinkedModelSerializer are used for creating link for our api.
   class Meta:
      model = modelname
      field = '__all__'

```


step 3: create view file and wite code like.

```
from django.shortcuts import render,redirect
from django.http import HttpResponse
from rest_framework import viewsets
from webapp.models import View
from webapp.serializer import ViewSerializer

# Create your views here.
class ViewViewSet(viewsets.ModelViewSet):
    queryset = View.objects.all()
    serializer_class = ViewSerializer



```

step 4 : define router in urls.py of your project dir.

```
from django.conf.urls import url,include
from webapp import views
from rest_framework import routers

# define router
router = routers.DefaultRouter()

# define router path and viewset that you used
router.register(r'abc',views.ViewViewSet)


urlpatterns = router.urls

```

step 5: finally make migration and migrate and run server with the help of following command.

```
python manage.py makemigrations
python amage.py migarte
python manage.py runserver
```
