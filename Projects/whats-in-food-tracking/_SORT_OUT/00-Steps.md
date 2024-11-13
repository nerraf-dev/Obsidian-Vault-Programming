Create  a project directory and change to it
```bash
mkdir whats-in
cd whats-in
```

```bash
django-admin startproject whatsin .
```


Create the Application:

First we will create the **inventory** application

```bash
python manage.py startapp inventory
```

```
inventory/
	    __init__.py
	    admin.py
	    apps.py
	    migrations/
	        __init__.py
	    models.py
	    tests.py
	    views.py
```

## Write the first view

Let’s write the first view. Open the file `invetory/views.py` and put the following Python code in it:

`polls/views.py`
```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the inventory index.")
```