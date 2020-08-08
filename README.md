# Django as a Microframework

A single-page Django website as demoed by Django Fellow Carlton Gibson at DjangoCon US 2019.

DjangoCon 2019 Video
https://youtu.be/w9cYEovduWI


## Instructions

In a directory of your choice:

```
$ pipenv install django==2.2.6 gunicorn==19.9.0
$ pipenv shell
(env) $ touch hello_django.py
```

Update `hello_django.py` as follows:

```python
# hello_django.py
from django.conf import settings
from django.core.handlers.wsgi import WSGIHandler
from django.http import HttpResponse
from django.urls import path

settings.configure(
    ROOT_URLCONF=__name__,
)

def hello_world(request):
    return HttpResponse("Hello, Django!")

urlpatterns = [
    path('', hello_world)
]

application = WSGIHandler()
```

To run it via [Gunicorn](https://gunicorn.org):

```
(env) $ gunicorn hello_django:application
```

Then check out [http://127.0.0.1:8000](http://127.0.0.1:8000).
