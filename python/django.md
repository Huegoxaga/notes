# Django

## Introduction

- Django is a Python-based free and open-source web framework
- One Django project can have multiple Apps as web components.
- Web servers like `Apache` or `Nginx` are used to get browser request, requests are then forwarded to `WSGI`.
  - Web server can enable a certain web port socket
- `WSGI`(Web Server Gateway Interface) is used to run the Django application, send to request to the app and then get return response from the app.
- `ASGI` (Asynchronous Server Gateway Interface) it provides an upgrade to WSGI, intended to provide a standard interface between async-capable Python web servers, frameworks, and applications.

## Useful Commands

- `pip install django` install django library
- `python -m django --version` check the version
- `django-admin` show a list of sub-command
- `django-admin startproject <project_name> <project_folder>` create a new project.
  - If project folder is not specified, create a new folder using the project name
- `python manage.py runserver` it will run the website and return the url of the running website. By default it works with 127.0.0.1 on 8000 port only
  - append the command with `0.0.0.0:8000` to runserver on all server addresses on port 8000.
  - append the port number as `python manage.py runserver 8001` to run the project on a certain port
- `python manage.py startapp <appname>` create a new app inside a project.
- `python manage.py makemigrations` update changes made on database model files for an app.
  - create files in the `app/migrations` folder for the `migrate` command to run.
  - run `python manage.py makemigrations <appname>` for migrating a certain app
  - run `python manage.py sqlmigrate <appname> <migrationID>` to see the SQL code that will be run on the database when executing migrate command.
    - Migration ID is the number in the file names in the `app/migration` folder.
- `python manage.py migrate`
  - first migration command will create default databases.
  - `python manage.py migrate --fake <appname> <migratationID>` make certain migration, assume the database is the same as this migration file is made, reset the migration record. Migration Files after this time can be deleted.
    - fake will not alter the database, new migrations are needed to rollback changes, then fake and delete the new and unused migration files.
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
- Add `USE_TZ = True` enable timezone support, then use `from django.utils import timezone`, `timezone.now()` to get current local time based on `TIME_ZONE` settings.
  - With timezone support is enabled all datetime object has timezone info
  - `TIME_ZONE` will change the server timezone environment variable
- If `USE_TZ = False`, `TIME_ZONE` must equals the server default. Otherwise, timestamp data with timezone in the database will be converted twice.
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
from django.urls import path, re_path
from django.conf.urls import url, include
from django.contrib import admin
from . import views
urlpatterns = [
    path('', views.home, name='appname-home'),
    path('about/', views.about, name='appname-about'),
    # re_path enables regex
    re_path('^student/edit/([0-9]+)/$', views.editStudent, name="editStudent"),
    # optionally use url (order matters)
    url(r'^', admin.site.urls, name='admin'),
]
```

- The full path excluded the matched string in the project `urls.py` will be used to match with the path strings here. For `www.example.com/a/b/c` after `a/` is matched in the project `urls.py`, `b/` will be used here to find a match.
- the second parameter `views.home` is pointing to the `home` method in the `view.py` file.
- For Django 3.2+, move CSRF exempt apis to the top in the url patterns list. CSRF protected endpoints like `admin.site.urls` should be placed at the end of the list. Any url pattern after CSDR protected endpoints are required to have CSRF header and token

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
      # (blank option is reforced by Django, while null option is enforced by the database)
      title = models.CharField(max_length=100, blank=True, null=True)
      # add default value
      content = models.TextField(default="Yes")
      # add unique option
      date_posted = models.DateTimeField(default=timezone.now, unique=True)
      # set foreign key in the user table, delete all associated posts when user object is deleted.
      author = models.ForeignKey(User, on_delete=models.CASCADE)
      # related_name field can be used to reverse lookup
      # Filter function has reversed fields available using the all lower-case model class name
      related_posts = models.ManyToManyField(User,blank=True,null=True, related_name='other_posts')
      # use the string 'self' to indicate a self-reference
      parent = models.ForeignKey('self', null=True, blank=True)
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
        unique_together = ["sno", "cno"]
  ```

  - `null` is database-related. Defines if a given database column will accept null values or not
  - `blank` is validation-related. It will be used during forms validation, when calling `form.is_valid()`
  - `on.delete` has the following options:
    - `models.CASCADE` delete all associated records.
    - `models.PROTECT` prevent deletion
    - `models.SET_NULL`
    - `models.SET_DEFAULT` only default value it set.
    - `models.SET('value')` set to certain value.
  - `models.ForeignKey('self')` if using a resursive FK relationship
  - When a class is defined as `abstract=True` in `Meta` options. Its fields can be reused by pass the Class Name in other class definition.
    ```py
    # The student table will have all fields from the CommonInfoAbstract class
    class Student(CommonInfoAbstract):
      home_group = models.CharField(max_length=5)
    ```
  - Adding an index for a field by using `db_index=True`
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
  ModelClass.objects.filter(propertyname='value') # return a list of matching objects in a queryset.
  ModelClass.objects.filter(id__in=[1,2,3]) # return results with matching id in a queryset
  ModelClass.objects.get(propertyname='value') # get a single record
  ModelClass.objects.get(id=1) # return the object with id 1
  newobject = ModelClass(property1='value1', property2 = 'value2') #create a new object
  newobject.save() # save change to the object that is already in the database
  newobject.delete() # delete the object
  querySet.delete() # delete all objects in the query set
  modelObject.id # get the object id
  modelObject.pk # get the object primary key value
  modelObject.manyToManyFieldRelatedName.all() # return all related fields of a many-to-many fields. Direct access without all() will cause "TypeError: ManyRelatedManager object is not iterable"
  modelObject.manyToManyFieldRelatedName.create(property1='value1', property2 = 'value2') # create a new related model of the model. Same as init new object and use object.save()
  ModelClass.objects.all().order_by('-column') # use - for descending order
  ModelClass.objects.select_related('tableA','tableB').prefetch_related('tableC').all() # Join tables for future queries. select_related is used for tables with one to one relationship, prefetch_related is used for many-to-many relationships.
  ModelClass.objects.values('field1', 'field2') # return dict queryset for certain fields
  ModelClass.objects.values_list('id', flat=True) # return a list queryset of id, if flat=False return list of tuples.
  ModelClass.objects.all().query.sql_with_params() # get the SQL sentence for this query
  ModelClass.objects.annotate(raw_link=Concat(Value("https://"), F('domain'))) # create a temp field with annonted strings append from a existing field
  from django.db.models import Count
  ModelClass.objects.annotate(managers_required=(Count('num_employees') / 4) + Count('num_managers'))
  from django.db.models import Sum
  ModelClass.objects.aggregate(total=(Sum('grade')))
  list(ModelClass.objects.all()) #convert queryset into a list
  # Aggregate PostgreSQL fields into an array
  TestModel.objects.aggregate(result=ArrayAgg('field1'))
  # Aggregate two output fields
  TestModel.objects.aggregate(avgx=RegrAvgX(y='field3', x='field2'), avgy=RegrAvgY(y='field3', x='field2')) # Output: {'avgx': 2, 'avgy': 13}
  # Annotate subquery - requires a specified OuterRef index when using subquery
  user_emails = OrganisationUser.objects.order_by().filter(
      organization_id=OuterRef('id'),
      user__is_active=True,
      user__daily_recharge_digest_mail_opt_in=True,
  ).values('organization_id').annotate(
      emails=ArrayAgg('user__email', distinct=True),
  ).values('emails')
  organisations_with_user_emails = Organisation.objects.annotate(
      emails=Subquery(
          user_emails,
          output_field=ArrayField(base_field=CharField()),
      ),
  )
  # Examine Database Execution Plan
  queryset.explain()
  # Subquery returns only one row
  Subquery(newest.values('email')[:1])
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
- This folder and its related `views.py` should be located under the same directory
- Variables here are passed from the `views.py`.
<!-- {% raw %} -->
- To access `.css` files in the static folder, add `{% load static %}` at the first line and set css link url to `href="{% static 'appfolder/filename.css' %}"`
- All links in the template files are represented as `href="{% url 'path-name' %}"`. The pass name is the name attributes of the paths elements in the `urls.py`.
  - use `href="{% url 'path-name' variable %}"` to pass data into url path
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
- `{% block blockname %}{% endblock %}` can enclose a defaut content, when it is used to replace a beginning tag, the ending tag should be in a separate block as well
  ```html
  <body>
    {% block div_begin %}
    <div class="root">
      {% endblock %}
      <main></main>
      {% block div_end %}
    </div>
    {% endblock %}
  </body>
  ```

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
   ```py
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
  - Override the `to_representation()` method can change the final output of the serializer
  ```py
  def to_representation(self, obj):
    data = super().to_representation(obj)
    # manipulate data['cashflows'] to group by month
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
  - `request.user` returns the current user object who initiate the request based on the credential
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

### Swagger Generators

- It auto generate document pages for the Rest API

#### Django REST Swagger(Deprecated)

##### Setup

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

#### Yet another Swagger Generator

##### Setup

1. run `pip install drf-yasg`
2. Add `'drf_yasg'` to `INSTALLED_APPS` in Django settings
3. Add the following to `urls.py`
   ```py
   from rest_framework import permissions
   from drf_yasg.views import get_schema_view
   from drf_yasg import openapi
   schema_view = get_schema_view(
       openapi.Info(
           title="Jaseci API",
           default_version='v1',
           description="Welcome to the world of Jaseci",
           terms_of_service="https://www.jaseci.org",
           contact=openapi.Contact(email="jason@jaseci.org"),
           license=openapi.License(name="Awesome IP"),
       ),
       public=True,
       permission_classes=(permissions.AllowAny,),
   )
   urlpatterns = [
     # A JSON view of your API specification at /swagger.json plus A YAML view of your API specification at /swagger.yaml
     url(r'^swagger(?P<format>\.json|\.yaml)$', schema_view.without_ui(cache_timeout=0), name='schema-json'),
     # A swagger-ui view of your API specification at /swagger/
     url(r'^swagger/$', schema_view.with_ui('swagger', cache_timeout=0), name='schema-swagger-ui'),
     # A ReDoc view of your API specification at /redoc/
     url(r'^redoc/$', schema_view.with_ui('redoc', cache_timeout=0), name='schema-redoc'),]
   ```

##### Usage

- Add comment for methods defined in class view
  ```py
  from drf_yasg.utils import swagger_auto_schema
  class ExampleAPIView(ListAPIView):
      permission_classes = (IsAuthenticated,)
      serializer_class = YourSerializerClass
      pagination_class = YourPaginationClass
      queryset = ModelName.objects.all()
      @swagger_auto_schema(tags=['API Category Title'], operation_id="Method Title", operation_description="Method Description", query_serializer=YourQuerySerializer, responses={
                  '200': ResponseModelSerializer(many=True),
                  '400': "Bad Request"
              },)
      def get(self, request, *args, **kwargs):
        pass
      @swagger_auto_schema(tags=['API Category Title'], operation_id="Method Title", operation_description="Method Description", reques_body=YourRequestSerializer, responses={
                  '200': ResponseModelSerializer(many=True),
                  '400': "Bad Request"
              },)
      def post(self, request, *args, **kwargs):
        pass
  ```
- Add comment for inherited View
  ```py
  from django.utils.decorators import method_decorator
  from drf_yasg.utils import swagger_auto_schema
  @method_decorator(name='post', decorator=swagger_auto_schema(
      tags=['API Category Title'],
      operation_id="Method Title",
  ))
  class YourAPIView(PredefinedAPIView):
      pass
  ```
- Add comment for a serializer fields, `name = serializers.BooleanField(required=False, help_text="description")`
- Add comment for a model fields, `field_name = models.FloatField(default=0, help_text="Field Description", verbose_name="Title")`

#### RapiPDF

- It can be used to generate docs and export docs as PDF
- It takes the json format docs link as input
- [Click here](https://mrin9.github.io/RapiPdf/) for more details

### Cache

- import the following
  ```py
  from django.utils.decorators import method_decorator
  from django.views.decorators.cache import cache_page
  ```
- Add decorator `@method_decorator(cache_page(time))` above each api method.
  - Cache TTL time is in seconds.

## GeoDjango

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
    - Or, download and Install QGIS from its [official website](https://qgis.org/en/site/forusers/download.html)
- Install PostGIS extension
  - If installing locally, click the PostGIS extension in the slack builder wizards.
  - If using AWS RDS, skip this step and enable the exstension directly.
- Add extension to the database, in PGAdmin select the database, right click extension, then add.
  - or run SQL `CREATE EXTENSION postgis`.
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

## Django Extension

- Provide additional tools for the Django project

### Setup

- run `pip install django-extensions` to install
- add `django_extensions` to `INSTALLED_APPS`

### Graph Models

- Choose and install diagram generators, `Graphviz` or `Dotplus`
  - `pip install pydotplus` if choose `Dotplus`
- Run `python manage.py graph_models -o <filename>.png`
  - `-a` create diagrams for all apps in the project
  - `-g` group by apps

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
   - Redis - [click](https://docs.celeryproject.org/en/stable/getting-started/backends-and-brokers/redis.html) to see installation & configuration instruction.

     - run `pip install -U "celery[redis]"` to install Celery and Redis as a bundle.
     - For Django app in `settings.py`.

     ```py
     CELERY_BROKER_URL = 'redis://localhost:6379'
     CELERY_RESULT_BACKEND = 'redis://localhost:6379'
     CELERY_ACCEPT_CONTENT = ['application/json']
     CELERY_RESULT_SERIALIZER = 'json'
     CELERY_TASK_SERIALIZER = 'json'
     ```

     - install server locally `brew install redis` or `sudo apt-get install redis-server` and run `redis-server`.
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
   # The @shared_task decorator lets the tasks can be used by any app(s).
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

### Useful Commands

- `celery -A <proj> purge` delete all pending tasks

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

#### Systemd for Celery

- Use a config file to store setting
  - `.pid` file stores the process id of the celery process

```conf
# The name of one or more workers to be initiated by systemd separated by space
CELERYD_NODES="worker1 worker2"
#   alternatively, specify the number of nodes to start:
#CELERYD_NODES=10
# Path to the celery command
CELERY_BIN="/home/ubuntu/.local/bin/celery"
CELERY_APP="app_name"
CELERYD_MULTI="multi"
# %n is the worker name
CELERYD_PID_FILE="/home/ubuntu/app/config/%n.pid"
# %I is the process ID
CELERYD_LOG_FILE="/home/ubuntu/app/config/%n%I.log"
CELERYD_LOG_LEVEL="INFO"
# additional settings, the number of process for each worker
# Default concurrent process number equals CPU core number
CELERYD_OPTS="--time-limit=300 --concurrency=8"
```

- Use the service file for systemd

```s
[Unit]
Description=Celery Service
After=network.target

[Service]
Type=forking
User=celery
Group=celery
EnvironmentFile=/path/to/celery.conf
WorkingDirectory=/opt/celery
ExecStart=/bin/sh -c '${CELERY_BIN} -A $CELERY_APP multi start $CELERYD_NODES \
    --pidfile=${CELERYD_PID_FILE} --logfile=${CELERYD_LOG_FILE} \
    --loglevel="${CELERYD_LOG_LEVEL}" $CELERYD_OPTS'
ExecStop=/bin/sh -c '${CELERY_BIN} multi stopwait $CELERYD_NODES \
    --pidfile=${CELERYD_PID_FILE} --loglevel="${CELERYD_LOG_LEVEL}"'
ExecReload=/bin/sh -c '${CELERY_BIN} -A $CELERY_APP multi restart $CELERYD_NODES \
    --pidfile=${CELERYD_PID_FILE} --logfile=${CELERYD_LOG_FILE} \
    --loglevel="${CELERYD_LOG_LEVEL}" $CELERYD_OPTS'
Restart=always

[Install]
WantedBy=multi-user.target
```

## Django Redis

- `django-redis` package integrate `redis-py` with `django`
- It helps setup Redis as Django's cache backend
- [Click Here](https://github.com/jazzband/django-redis) for more details

## AllAuth

- It provides authentication support for Django web apps
- run `pip install django-allauth` to install
- [Click Here](https://django-allauth.readthedocs.io/en/latest/) to see official docs
- It has `html` teamplates related to the auth flow
- It supports social account (thrid parties) sign-in and sign-up
- It has a data model that stores social accounts and their providers' info
- It will auto sync social accounts table with Django user table
- A sites table tracks all the frontend web app that utilizing auth using social accounts
- A social provider can be used by one or more sites
- Settings file contains additional config context that is not included in the social provider data model, and defines the current site ID

## Simple JWT

- `https://jwt.io/ and put the token into debugger`

## Rest Auth

- It provides the web app a user specific token for API access
- It needs the `allauth` package to have the signup feature
- run `pip install django-rest-auth` to install or `pip install dj-rest-auth` (more actively maintained)
- [Click Here](https://django-rest-auth.readthedocs.io/en/latest/installation.html) to see official docs
- It has a token table which stores all the temp tokens for associated users
- It needs `rest_framework.authentication.TokenAuthentication` in the `settings.py` in order to auth by the tokens
- It supports social authentication by providing API endpoints that takes social auth tokens and returns and stores the API token

## Unit Testing

- Writing test methods in `test.py` as follows
  ```py
  from django.test import TestCase
  class MyTestCase(TestCase):
     # Your test methods
  ```
- Or optionally, replace tests.py with a folder called tests, insert an empty file inside called `__init__.py`, and create the `test_*.py` files. Django will discover and execute these.
- run `python manage.py test` to start all test method in the project or `python manage.py <appname>` to run test cases in a certain app folder.
- Example Code:
  ```py
  from django.test import TestCase, Client
  from django.urls import reverse
  import json
  from iport.models import *
  class TestViews(TestCase):
      def setUp(self):
          self.client = Client()
          # For Rest API framework
          url = reverse('token_obtain_pair')
          u = User.objects.create_user(username='user', email='user@foo.com', password='pass')
          u.is_active = True
          u.save()
          self.client = APIClient()
          resp = self.client.post(url, {'username':'user', 'password':'pass'}, format='json')
          self.token = resp.data['access']
          self.client.credentials(HTTP_AUTHORIZATION='Bearer ' + self.token)
          # get urls from view name with args
          self.url = reverse('view_name', args=[value])
      def test_example(self):
          # test get request using url
          response = client.get(self.list_url)
          # create object in database
          ModelName.objects.create(
              field1 = 'value1',
              field2 = 200
          )
          # test post request with parameters.
          response = self.client.post(self.url, {
              'key1': 'value1',
              'key2': 10000
          })
          # delete objects
          response = self.client.delete(self.url, json.dumps({
              'id': 1
          }))
          # assert status code
          self.assertEquals(response.status_code, 200)
          # assert template page
          self.assertTemplateUsed(response, 'templates/template.html')
          self.assertEquals(self.url.func, view_method_name)
          self.assertEquals(self.url.func.view_class, ViewClassName)
  ```
