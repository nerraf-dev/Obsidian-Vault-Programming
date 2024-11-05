From the command line, `cd` into a directory where you’d like to store your code and create a new directory named `djangotutorial`. (This directory name doesn’t matter to Django; you can rename it to anything you like.)

```
$ mkdir djangotutorial
```

Then, run the following command to bootstrap a new Django project:

```
$ django-admin startproject mysite djangotutorial
```

Let’s look at what `startproject` created:

```
djangotutorial/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
```

These files are:

- `manage.py`: A command-line utility that lets you interact with this Django project in various ways. You can read all the details about `manage.py` in django-admin and manage.py.
    
- `mysite/`: A directory that is the actual Python package for your project. Its name is the Python package name you’ll need to use to import anything inside it (e.g. `mysite.urls`).
    
- `mysite/__init__.py`: An empty file that tells Python that this directory should be considered a Python package. If you’re a Python beginner, read more about packages in the official Python docs.
    
- `mysite/settings.py`: Settings/configuration for this Django project. Django settings will tell you all about how settings work.
    
- `mysite/urls.py`: The URL declarations for this Django project; a “table of contents” of your Django-powered site. You can read more about URLs in URL dispatcher.
    
- `mysite/asgi.py`: An entry-point for ASGI-compatible web servers to serve your project. See How to deploy with ASGI for more details.
    
- `mysite/wsgi.py`: An entry-point for WSGI-compatible web servers to serve your project. See How to deploy with WSGI for more details.

---
## The development server

Let’s verify your Django project works. Change into the `djangotutorial` directory, if you haven’t already, and run the following commands:

```
$ python manage.py runserver
```

You’ll see the following output on the command line:

Performing system checks...

System check identified no issues (0 silenced).

You have unapplied migrations; your app may not work properly until they are applied.
Run '`python manage.py migrate`' to apply them.

```
October 31, 2024 - 15:50:53
Django version 5.1, using settings 'mysite.settings'
Starting development server at [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
Quit the server with CONTROL-C.
```

---
## Creating an app

> [!NOTE]
> Projects vs. apps
> What’s the difference between a project and an app? An app is a web application that does something – e.g., a blog system, a database of public records or a small poll app. A project is a collection of configuration and apps for a particular website. A project can contain multiple apps. An app can be in multiple projects.

Your apps can live anywhere in your Python path. In this tutorial, we’ll create our poll app inside the `djangotutorial` folder.

To create your app, make sure you’re in the same directory as `manage.py` and type this command:

```
$ python manage.py startapp polls
```

That’ll create a directory `polls`, which is laid out like this:

```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

This directory structure will house the poll application.

## Write your first view

Let’s write the first view. Open the file `polls/views.py` and put the following Python code in it:

`polls/views.py`

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

This is the most basic view possible in Django. To access it in a browser, we need to map it to a URL - and for this we need to define a URL configuration, or “URLconf” for short. These URL configurations are defined inside each Django app, and they are Python files named `urls.py`.

To define a URLconf for the `polls` app, create a file `polls/urls.py` with the following content:

`polls/urls.py`

```
from django.urls import path

from . import views

urlpatterns = [
    path("", views.index, name="index"),
]
```

Your app directory should now look like:

```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    urls.py
    views.py
```

The next step is to configure the global URLconf in the `mysite` project to include the URLconf defined in `polls.urls`. To do this, add an import for `django.urls.include` in `mysite/urls.py` and insert an [`include()`](https://docs.djangoproject.com/en/5.1/ref/urls/#django.urls.include "django.urls.include") in the `urlpatterns` list, so you have:

`mysite/urls.py`[¶](https://docs.djangoproject.com/en/5.1/intro/tutorial01/#id3 "Permalink to this code")

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("polls/", include("polls.urls")),
    path("admin/", admin.site.urls),
]
```
The `path()` function expects at least two arguments: `route` and `view`. The `include()` function allows referencing other `URLconfs`. Whenever Django encounters `include()`, it chops off whatever part of the URL matched up to that point and sends the remaining string to the included `URLconf` for further processing.

The idea behind `include()` is to make it easy to plug-and-play URLs. Since polls are in their own `URLconf` (`polls/urls.py`), they can be placed under “/polls/”, or under “/fun_polls/”, or under “`/content/polls/`”, or any other path root, and the app will still work.

> [!NOTE]
> When to use `include()`
> 
> You should always use `include()` when you include other URL patterns. The only exception is `admin.site.urls`, which is a pre-built `URLconf` provided by Django for the default admin site.

You have now wired an `index` view into the URLconf. Verify it’s working with the following command:

```python
$ python manage.py runserver
```

Go to `http://localhost:8000/polls/` in your browser, and you should see the text “_Hello, world. You’re at the polls index._”, which you defined in the `index` view.

## Database Setup

look at settings etc.

How to change from sqllite3 https://docs.djangoproject.com/en/5.1/topics/install/#database-installation

### Creating Models

