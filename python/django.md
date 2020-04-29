# Django

## Introduction

- Django is a Python-based free and open-source web framework
- One Django project can have multiple Apps as web components.

## Useful Commands

- `pip install django` install django library
- `python -m django --version` check the version
- `django-admin` show a list of sub-command
- `django-admin startproject <project_name>` create a new project.
- `python manage.py runserver` it will run the website and return the url of the running website. By default it is localhost:8000
- `python manage.py startapp <appname>` create a new app inside a project.
- `python manage.py makemigrations` update changes made on database model files for an app.
  - create files in the `app/migrations` folder for the `migrate` command to run.
  - run `python manage.py sqlmigrate <appname> <migrationID>` to see the SQL code that will be run on the database when executing migrate command.
    - Migration ID is the number in the file names in the `app/migration` folder.
- `python manage.py migrate`
  - first migration command will create default databases.
  - `python manage.py migrate --fake <appname> <migratationID>` make certain migration, assume the database is the same as this migration file is made, reset the migration record. Migration Files after this time can be deleted.
  - `python manage.py migrate --fake-initial` force making initial migrate with database is already exists.
- `python manage.py showmigrations` Check migration history.
- `python manage.py createsuperuser` follow the promts and create admin account for the admin page.
- `python manage.py shell` It starts an interactive shell to run django project code line by line.
- `python manage.py collectstatic` it populates the static directory with static assets (JavaScript, CSS, and images).
  - Make sure that `django.contrib.staticfiles` is included in the `INSTALLED_APPS` in `settings.py`.

## Project Folder

### settings.py

- To register an app to the project, add the element `'appname.apps.AppNameConfig'` or just `'AppName'` in the `INSTALLED_APPS` array.
- Add `STATIC_ROOT = 'static'` to tell Django where to store static files.
- Add `USE_TZ = True` enable timezone support, then use `from django.utils import timezone`, `timezone.now()` to get current local time.
- When `Debug=True`, static file will be auto generated.

### urls.py

```py
from django.contrib import admin
from django.urls import path, include
from users import views as user_views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('appnameA.urls')),
    path('a/', include('appnameB.urls')),
    path('register/', user_views.register, name='register'),
]
```

- `urlpatterns` contains a list of path.
- The first parameter of path is the url string, root path is empty.
- A match is found when actual path begins with the string in the first parameter. Ex. `www.example.com/a/b/c` will matchs string `a/`.
- When a match is found the `urls.py` file for the app `appnameA` will be loaded if the path is `www.example.com/`
- The path can also point to an app view file directly.

## App Folder

### apps.py

```py
from django.apps import AppConfig
class AppNameConfig(AppConfig):
    name = 'appname'
```

- The class name `AppNameConfig` should be registered in the project's `settings.py` file for the project to access the app.

### urls.py

```py
from django.urls import path
from . import views
urlpatterns = [
    path('', views.home, name='appname-home'),
    path('about/', views.about, name='appname-about'),
]
```

- The full path excluded the matched string in the project `urls.py` will be used to match with the path strings here. For `www.example.com/a/b/c` after `a/` is matched in the project `urls.py`, `b/` will be used here to find a match.
- the second parameter `views.home` is pointing to the `home` method in the `view.py` file.

### view.py

```py
from django.shortcuts import render
from django.http import HttpResponse
from .models import ModelClass
def home(request):
    return HttpResponse('<h1>Blog Home</h1>')
def about(request):
    return HttpResponse('<h1>Blog About</h1>')
def home(request):
    context = {
        'posts': ModelClass.objects.all()
    }
    return render(request, 'blog/home.html', context)
def about(request):
    return render(request, 'blog/about.html', {'title': 'About'})
```

- Each method here is a page.
- Each method has a parameter `request`.
- `HttpResponse` can be used to return html content in text for the webpage.
- render method can be used to render a template page.
  - The third parameter is the data that will be passed to the template page.
  - The data passed in like `post` can be a list of dictionary or just a dictionary of data.
  - The data passed in the example is from a data model.

### models.py

- This is the data model for the project.
- Each class is corresponding to a database table.
  ```py
  from django.db import models
  from django.utils import timezone
  #import user from built-in auth models
  from django.contrib.auth.models import User
  class Post(models.Model):
      # exists by default, primary_key is mandatory.
      id = models.AutoField(primary_key=True)
      # add nullable and allow it to be black options
      title = models.CharField(max_length=100,blank=True, null=True)
      # add default value
      content = models.TextField(default="Yes")
      # add unique option
      date_posted = models.DateTimeField(default=timezone.now, unique=True)
      # set foreign key in the user table, delete all associated posts when user object is deleted.
      author = models.ForeignKey(User, on_delete=models.CASCADE)
      # Meta provides additional info for the Model
      class Meta:
        # add check constrains
        constraints = [
            models.CheckConstraint(check=models.Q(age__gte=18), name='age_gte_18'),
        ]# add index
        index_together = ["pub_date", "deadline"]
        indexes = [
            models.Index(fields=['last_name', 'first_name']),
            models.Index(fields=['first_name'], name='first_name_idx'),
        ]
        # set name
        db_table = 'music_album'
        # set order when query
        get_latest_by = "order_date"
        ordering = ['-pub_date', 'author']
  ```
  - `on.delete` has the following options:
    - `models.CASCADE` delete all associated records.
    - `models.PROTECT` prevent deletion
    - `models.SET_NULL`
    - `models.SET_DEFAULT` only default value it set.
    - `models.SET('value')` set to certain value.
  - When a class is defined as `abstract=True` in `Meta` options. Its fields can be reused by pass the Class Name in other class definition.
    ```py
    # The student table will have all fields from the CommonInfoAbstract class
    class Student(CommonInfoAbstract):
      home_group = models.CharField(max_length=5)
    ```
  - Model class can have a `__str__` method to define a string representation.
    ```py
    def __str__(self):
        return self.title
    ```
- Whenever a file import the data model. It will have access to the data from the database.
  ```py
  from .models import ModelClass
  ModelClass.objects.all() # return all objects of this class from the database.
  ModelClass.objects.first() # return the first object
  ModelClass.objects.last() # return the last object
  ModelClass.objects.all()[0:20]# return first 20 objects
  ModelClass.objects.filter(propertyname='value') # return a list of matching objects.
  ModelClass.objects.filter(propertyname='value') # return the first matching object.
  ModelClass.objects.get(id=1) # return the object with id 1
  newobject = ModelClass(property1='value1', property2 = 'value2') #create a new object
  newobject.save() # save change to the object that is already in the database
  modelObject.id # get the object id
  modelObject.pk # get the object primary key value
  modelObject.relatedModel_set.all() # return all assciated model of one model.
  modelObject.relatedModel_set.create(property1='value1', property2 = 'value2') # create a new related model of the model.
  ```

### admin.py

- It controls the admin page.
- The default admin path is the site url followed by `/admin`.
- Can be used to create users and groups.
- All changes need to be made on the admin page not in the database directly. Otherwise, database tables need to be resync for the pointer values.
  - For Postgre: run SQL `SELECT setval('your_table_id_seq', COALESCE((SELECT MAX(id) FROM your_table), 1), false);` in the database.
    - run `SELECT nextval('your_table_id_seq');` to check the next value for insert.
      - Everytime it runs, it will increase the `nextval` by one.
    - run `SELECT MAX(id) FROM your_table;` to check the total record count.
- Data models need to be registered here for the admin page to display and edit.
  ```py
  from django.contrib import admin
  from .models import Post
  admin.site.register(Post)
  ```

### static folder

- It can be used to store additional static files for the app, like css files.

### template folder

- Apps can have template that stores dynamic html file that can access variables and run code inside.
  - If support basic logic syntax in between html codes. Unlike Python code, each code block requried to be closed in the end.
- Variables here are passed from the `view.py`.
<!-- {% raw %} -->
- To access `.css` files in the static folder, add `{% load static %}` at the first line and set css link url to `href="{% static 'appfolder/filename.css' %}"`
- All links in the template files are represented as `href="{% url 'path-name' %}"`. The pass name is the name attributes of the paths elements in the `urls.py`.
- To display date in certain format use format string as `{{ post.date|date:"F d, Y" }}`
<!-- {% endraw %} -->

#### base.html

```html
<!DOCTYPE html>
<html>
  <head>
    {% if title %}
    <title>Django Blog - {{ title }}</title>
    {% else %}
    <title>Django Blog</title>
    {% endif %}
  </head>
  <body>
    {% block blockname %}{% endblock %}
  </body>
</html>
```

- This is the layout that can be shared by all views.

#### content.html

```
{% extends "appname/base.html" %}
{% block blockname %}
    {% for post in posts %}
              <h1>{{ post.author }}</h1>
              <p>{{ post.content }} posted on {{ post.date }}</p>
    {% endfor %}
{% endblock blockname %}
```

- This is the file that will be inserted into the base template.
- Templates from other apps can also be used here.
- The block name should be the same name specified in the `base.html`.

### Customized Forms

- Create a `forms.py` in the app folder. Define a custom form class that inherit the default auth form from Django.
  ```py
  from django import forms
  from django.contrib.auth.models import User
  from django.contrib.auth.forms import UserCreationForm
  class UserRegisterForm(UserCreationForm):
      email = forms.EmailField()
      class Meta:
          model = User
          fields = ['username', 'email', 'password1', 'password2']
          # use this if all fields are included.
          fields = '__all__'
  ```
- In the view page set up the request logic.
  ```py
  from django.shortcuts import render, redirect
  from django.contrib import messages
  from .forms import UserRegisterForm
  def register(request):
      # If reveiving data
      if request.method == 'POST':
          form = UserRegisterForm(request.POST)
          if form.is_valid():
              form.save()
              username = form.cleaned_data.get('username')
              messages.success(request, f'Account created for {username}!')
              return redirect('blog-home')
      else:
          # if not receiving data initilize a new empty form
          form = UserRegisterForm()
      # render the form in the view
      return render(request, 'users/register.html', {'form': form})
  ```
- run `pip install django-crispy-forms` to install the app that helps style the form with `Bootstrap`.
- In `settings.py`, register the app as `'crispy_forms'` in `INSTALLED_APPS`, and `CRISPY_TEMPLATE_PACK = 'bootstrap4'` at the bottom to specify the package in use.
- For the form template:
  <!-- {% raw %} -->
  ```py
  {% extends "blog/base.html" %}
  {% load crispy_forms_tags %}
  {% block content %}
      <div class="content-section">
          <form method="POST">
              {% csrf_token %}
              <fieldset>
                  <legend>Join Today</legend>
                  {{ form|crispy }}
              </fieldset>
              <div>
                  <button type="submit">Sign Up</button>
              </div>
          </form>
      </div>
  {% endblock content %}
  ```
  <!-- {% raw %} -->
- Use this for feedback upon valid submission.
  ```py
  {% if messages %}
              {% for message in messages %}
                <div class="alert alert-{{ message.tags }}">
                  {{ message }}
                </div>
              {% endfor %}
            {% endif %}
  ```

## Cloud Storages

- [Click](https://django-storages.readthedocs.io/en/latest/) to see many possible cloud storage implementation for Django.

### AWS S3

1. create a S3 bucket and set up permissions.
2. create a designated IAM user role for access.
3. Save credentials and buck name in the virtual environment's `.bash_profile` file.
4. run `pip install boto3` and `pip install django-storages`
5. In `settings.py` add `'storages'` and following settings.
   ```
   AWS_ACCESS_KEY_ID = os.environ.get('AWS_ACCESS_KEY_ID')
   AWS_SECRET_ACCESS_KEY = os.environ.get('AWS_SECRET_ACCESS_KEY')
   AWS_STORAGE_BUCKET_NAME = os.environ.get('AWS_STORAGE_BUCKET_NAME')
   AWS_S3_FILE_OVERWRITE = False
   AWS_DEFAULT_ACL = None
   DEFAULT_FILE_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
   ```

## REST Framework

- It is used to create restful api for the web app.
- [Click here](https://www.django-rest-framework.org) for full docs.
- run `pip install djangorestframework` to install
- add `'rest_framework'` to `INSTALLED_APPS` in `settings.py`
- The Serializers convert objects into JSON data. It is defined in the `serializers.py` in the api app folder.
  - Model Serializers - It provides a template that is easy to implement a serializer class based on model class.
  ```py
  from rest_framework import serializers
  from .models import Sample
  class SampleSerializer(serializers.ModelSerializer):
    # add fielder from other serializers
    someFields = OtherSerializer(many=True)
    # add fields in the meta class
    class Meta:
        model = Sample
        # add certain fields
        fields = ['id', 'account_name', 'users', 'created']
        # exclude a certain field
        exclude = ['id']
        # add all fields
        fields = '__all__'
        # add more options for previous fields.
        extra_kwargs = {
                'created': {'write_only': True},
                'id': {'required': True}
        }
  ```
  - Serializers can be used to update or create JSON object by defining the `create()` and `update()` method in Serializer Class.
  ```py
  def create(self, validated_data):
        return Sample.objects.create(**validated_data)
  def update(self, instance, validated_data):
      instance.name = validated_data.get('name', instance.name)
      instance.email = validated_data.get('email', instance.email)
      instance.save()
      return instance
  ```
  - Validation method can be added in the Serializer Class.
  ```py
  # field level validation
  def validate_title(self, value):
        # check if value contains keyword django
        if 'django' not in value.lower():
            raise serializers.ValidationError("Blog post is not about Django")
        return value
  # object level validation
  def validate(self, data):
        if data['start'] > data['finish']:
            raise serializers.ValidationError("finish must occur after start")
        return data
  ```
- In `views.py` defines the behavior of the certain path, when either a POST(update) request or GET(read) request is sent.
  ```py
  from rest_framework import status # return status
  # enable .as_view in urls.py that return a view based on JSON result
  from rest_framework.views import APIView
  # Response to return for each view method
  from rest_framework.response import Response
  from .models import Sample
  from .serializers import SampleSerializer
  # inherite methods from APIView class
  class SampleView(APIView):
    def get(self, request):
      # get all current data
      data = Sample.objects.all()
      # initalize a serializer take multiple data object into JSON.
      # many = True enables convertion of multiple objects
      serializer = SampleSerializer(data, many = True)
      # return the JSON data in response
      return Response(serializer.data)
    def post(self):
      # if pass here means this method does nothing.
      pass
      # if serializer has create method.
      data = Snippet(code='foo = "bar"\n')
  ```
  - When serializer has `create()` or `update()` methods. `serializer.save(data=data)` method will run `create()`. `serializer.save(existingObject, data=data)` will run `update()`.
  - When serializer has `validate()`, `serializer.is_valid()` will run validation. Then use `serializer.error()` to return errors.
- In `urls.py` add the view method that returning data as view to path, `path('api/', views.SampleView.as_view()),`
- Pagination
  - Set Pagination globally in `settings.py`
    - For Pagination based on page number
      ```js
      REST_FRAMEWORK = {
        DEFAULT_PAGINATION_CLASS:
          "rest_framework.pagination.PageNumberPagination",
        PAGE_SIZE: 100,
      };
      ```
    - For cursor pagination
      ```js
      REST_FRAMEWORK = {
        DEFAULT_PAGINATION_CLASS: "rest_framework.pagination.CursorPagination",
        PAGE_SIZE: 100,
      };
      ```
    - For Limit Offset Pagination
      ```js
      REST_FRAMEWORK = {
        DEFAULT_PAGINATION_CLASS:
          "rest_framework.pagination.LimitOffsetPagination",
      };
      ```
  - Set Pagination for each method of `views.py` individually
    - defind the pagination class
      ```py
      class StandardResultsSetPagination(PageNumberPagination):
      page_size = 100
      page_size_query_param = 'page_size'
      max_page_size = 1000
      ```
    - Assign the class name to the `pagination_class` variables in the each view method.

### Swagger

- It auto generate document pages for the Rest API

##### Usage

1. Run `pip install django-rest-swagger`
2. Add `'rest_framework_swagger'` to `INSTALLED_APPS` in Django settings.
3. In API app's `views.py` add
   ```py
   from rest_framework_swagger.views import get_swagger_view
   schema_view = get_swagger_view(title='Pastebin API')
   ```
   - There are two optional parameter for the `get_swagger_view()` method:
     - `title`: The title of the documentation `(Default: None)`
     - `url`: The URL to the documentation, if not on the same host or path. Can be a relative path or can be an absolute URL. `(Default: None)`
4. add path in `urls.py`
   ```py
   from django.conf.urls import url
   urlpatterns = [
       url(r'^$', appname.views.docs_view)
   ]
   ```
5. Make additional setting in the `settings.py` file.
   ```py
   SWAGGER_SETTINGS = {
     'SHOW_REQUEST_HEADERS': True,
     'SUPPORTED_SUBMIT_METHODS': [
         'get',
         'post',
     ]
   }
   ```
   - [Click Here](https://django-rest-swagger.readthedocs.io/en/latest/settings/) to see all setting options.
6. Add docs string comments to provide more info in the docs page.

- If see `'AutoSchema' object has no attribute 'get_link' swagger` error, add `'DEFAULT_SCHEMA_CLASS': 'rest_framework.schemas.coreapi.AutoSchema',` in the `settings.py`.

### GeoDjango

- It provide data model and function for GIS supported database.
  - `PostgreSQL` uses `PostGIS` extenstion.
- It is included in the Django package.
- `QGIS` is a GIS app that helps install all the required database drivers.
  - `PostgreSQL` requires `GDAL`, `GEOS`, and `PROJ.4`.

#### Setup

- Install drivers
  - `PostgreSQL` requires `GDAL`, `GEOS`, and `PROJ.4`.
    - For Mac:
      - run `brew install gdal`
      - run `brew install geos`
      - run `brew install proj`
- Install PostGIS extension
  - If installing locally, click the PostGIS extension in the slack builder wizards.
  - If using AWS RDS, skip this step and enable the exstension directly.
- Add extension to the database, in PGAdmin select the database, right click extension, then add.
  - or run SQL `CREATE EXTENSION postgis`.
- Download and Install QGIS from its [official website](https://qgis.org/en/site/forusers/download.html)
- Set database engine in `setting.py`.
  - Use `django.contrib.gis.db.backends.postgis` for `PostgreSQL`.
- Add `django.contrib.gis` to `INSTALLED_APPS` in `setting.py`

## Django Crontab

- It manages crontab tasks with django.
- Usage:
  1. run `pip install django-crontab` to install
  2. add `'django_crontab'` to the `INSTALLED_APPS` in the `settings.py`.
  3. create a python file in the project or app foloder and define task methods.
  4. add the methods in the `settings.py` using the following format.
     ```py
     CRONJOBS = [
     ('*/5 * * * *', 'myapp.cron.my_scheduled_job'),
     ('0   0 1 * *', 'myapp.cron.my_scheduled_job', '>> /tmp/scheduled_job.log'),
     ('*/5 * * * *', 'myapp.cron.other_scheduled_job', ['arg1', 'arg2'], {'verbose': 0}),
     ('0   4 * * *', 'django.core.management.call_command', ['clearsessions']),
     ]
     ```
     - optionally the task can take a list of positional arguments for the method (default: [])
     - optionally the task can take a dictionary of keyword arguments for the method (default: {})
  5. add or update new tasks added in the `settings.py` by running command `python manage.py crontab add`
     - run `python manage.py crontab show` to show the list of tasks.
     - run `python manage.py crontab remove` to remove all registered tasks.

## Celery

### Introduction

- It’s a task queue with focus on real-time processing, while also supporting task scheduling.
- It is not included in the anaconda default package, and need to be installed using command `conda install celery`.

### Basic Usage

1. Celery requires a broker to store task list in a queue. There are three options, follow one of the link to install:
   - RabbitMQ(fully supported recommanded) - [click](http://docs.celeryproject.org/en/latest/getting-started/brokers/rabbitmq.html#broker-rabbitmq) to see installation & configuration instruction.
     - Not need to pip install rabbitMQ for project
     - Install server `brew install rabbitmq`
     - Add environment variables `PATH=$PATH:/usr/local/sbin` in `.bash_profile`
     - run the server `sudo rabbitmq-server` use `-detached` to run in background.
     - commplete the following config in command lines.
       ```bash
       $ sudo rabbitmqctl add_user myuser mypassword
       $ sudo rabbitmqctl add_vhost myvhost
       $ sudo rabbitmqctl set_user_tags myuser mytag
       $ sudo rabbitmqctl set_permissions -p myvhost myuser ".*" ".*" ".*"
       ```
     - Add the connection string `broker_url = 'amqp://myuser:mypassword@localhost:5672/myvhost'`, and `CELERY_AUTH_MECHANISMS = ['PLAIN', 'AMQPLAIN']` to set allowed AUTH MECHANISMS
     - run `sudo rabbitmqctl status` to check status.
     - if want to stop the server run `sudo rabbitmqctl stop`.
   - Redis - [click](http://docs.celeryproject.org/en/latest/getting-started/brokers/redis.html#broker-redis) to see installation & configuration instruction.
     - run `pip install -U "celery[redis]"` to install Celery and Redis as a bundle.
     - For Django app add `BROKER_URL = 'redis://localhost:6379/0'` and `BROKER_TRANSFER = 'redis'` in `settings.py`.
     - install server locally `brew install redis` and run it `redis-server`.
     - test server `redis-cli ping`
   - Amazon SQS - [click](http://docs.celeryproject.org/en/latest/getting-started/brokers/sqs.html#broker-sqs) to see installation & configuration instruction.
2. Defines the task in `tasks.py`
   ```py
   from celery import Celery
   app = Celery('tasks', broker='pyamqp://guest@localhost//')
   @app.task
   def add(x, y):
     return x + y
   ```
3. Run the Celery server by running command `celery -A <projectName> worker --loglevel=info`.
4. Call the task
   ```py
   from tasks import add
   >>> add.delay(4, 4)
   ```
5. Setup and view the result
   1. add the `backend` argument to Celery, using a selected backend storage method from [here](http://docs.celeryproject.org/en/latest/getting-started/first-steps-with-celery.html#keeping-results)
   2. Access result using the following ways
   ```py
   result = add.delay(4, 4)
   result.ready() #return true if it is done.
   result.get(timeout=1) # get result after a certain duration.
   result.get(propagate=False) # preventing a exception is reraised when calling get() after an error.
   result.traceback #  access to the original traceback after a exception is raised.
   # Remember to call either get() or forget() to release the memory
   result.forget()
   ```
6. Do additional settings
   - To change a certain settings `app.conf.task_serializer = 'json'`
   - To change multiple settings:
     ```py
     app.conf.update(
     task_serializer='json',
     accept_content=['json'],  # Ignore other content
     result_serializer='json',
     timezone='Europe/Oslo',
     enable_utc=True,
     )
     ```
   - To change settings from a config file, use `app.config_from_object('celeryconfig')`, An example config file named `celeryconfig.py` is shown as follows:
     ```py
     broker_url = 'pyamqp://'
     result_backend = 'rpc://'
     task_serializer = 'json'
     result_serializer = 'json'
     accept_content = ['json']
     timezone = 'Europe/Oslo'
     enable_utc = True
     ```

### Work with Django

1. Add the Celery instance definition at `proj/proj/celery.py`
   ```py
   from __future__ import absolute_import, unicode_literals
   import os
   from celery import Celery
   # set the default Django settings module for the 'celery' program.
   os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'proj.settings')
   app = Celery('proj')
   # Using a string here means the worker doesn't have to serialize
   # the configuration object to child processes.
   # - namespace='CELERY' means all celery-related configuration keys
   #   should have a `CELERY_` prefix.
   app.config_from_object('django.conf:settings', namespace='CELERY')
   # Load task modules from all registered Django app configs.
   app.autodiscover_tasks()
   @app.task(bind=True)
   def debug_task(self):
       print('Request: {0!r}'.format(self.request))
   ```
2. Let celery start in the `proj/proj/__init__.py` when django starts.
   ```py
   from __future__ import absolute_import, unicode_literals
   # This will make sure the app is always imported when
   # Django starts so that shared_task will use this app.
   from .celery import app as celery_app
   __all__ = ('celery_app',)
   ```
3. Write tasks in the `tasks.py` in app folders
   ```py
   # Create your tasks here
   from __future__ import absolute_import, unicode_literals
   from celery import shared_task
   from demoapp.models import Widget
   @shared_task
   def add(x, y):
       return x + y
   @shared_task
   def mul(x, y):
       return x * y
   @shared_task
   def xsum(numbers):
       return sum(numbers)
   @shared_task
   def count_widgets():
       return Widget.objects.count()
   @shared_task
   def rename_widget(widget_id, name):
       w = Widget.objects.get(id=widget_id)
       w.name = name
       w.save()
   ```

### Celery Beat

- This is a celery extension that stores the schedule in the Django database, and presents a convenient admin interface to manage periodic tasks at runtime.
- Setup steps:
  1. Use pip to install the package, `pip install django-celery-beat`
  2. Add the `django_celery_beat` module to `INSTALLED_APPS` in `settings.py`
  3. Apply Django database migrations so that the necessary tables are created: `python manage.py migrate`
  4. Start the celery beat service `celery -A proj beat -l info --scheduler django_celery_beat.schedulers:DatabaseScheduler`
  5. add the related settings if nesscery, [click](http://docs.celeryproject.org/en/latest/userguide/configuration.html#beat-settings-celery-beat) to see more details.
  6. Visit the Django-Admin interface to set up some periodic tasks.

### Daemonization

- In production you’ll want to run the worker in the background as a daemon instead of running the service using commands explicitly.
- Either `systemd` or `supervisord` can be used.
