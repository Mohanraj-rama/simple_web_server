# EX01 Developing a Simple Webserver

# Date:
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
### views.py
```
from django.shortcuts import render
def simpleweb(request):
    return render(request,'simpleserver.html')
```
### settings.py
```
from pathlib import Path
import os

BASE_DIR = Path(__file__).resolve().parent.parent




SECRET_KEY = 'django-insecure-!=n2vk$s^ny-2=&ae9b@@^0kw4w8#(viwh#n2l3-u97u&k1@i*'

DEBUG = True

ALLOWED_HOSTS = []




INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'web',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'simple.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'simple.wsgi.application'



DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}



AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]



LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_TZ = True



STATIC_URL = 'static/'



DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

```
### urls.py
```
from django.contrib import admin
from django.urls import path
from web import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('simpleweb',views.simpleweb)
]
```
### simpleserver.html
```
<!doctype html>
<html>
<head>
<title>Web Server</title>
</head>
<body>
<h1><center>LAPTOP CONFIGURATION</center></h1>
   <table border="5" cellpadding="20" align="center">
        <tr>
            <th bgcolor="blue">Specification</th>
            <th bgcolor="blue">Details</th>
        </tr>
            <td bgcolor="red">Model</td>
            <td bgcolor="red">Lenovo</td>
        </tr>
        <tr bgcolor="yellow">
            <td>Processor</td>
            <td>Intel Core i5</td>
        </tr>
        <tr bgcolor="yellow">
            <td>RAM</td>
            <td>16GB</td>
        </tr>
        <tr bgcolor="yellow">
            <td>Storage</td>a
            <td>256GB SSD</td>
        </tr>
        <tr bgcolor="yellow" >
            <td>Graphics</td>
            <td>Integrated Intel UHD Graphics</td>
        </tr>
        <tr bgcolor="yellow">
            <td>Display</td>
            <td>14-inch FHD (1920 x 1080)</td>
        </tr>
        <tr bgcolor="yellow">
            <td>Operating System</td>
            <td>Windows 10</td>
        </tr>
        <tr bgcolor="yellow">
            <td>Colours available</td>
            <td>Black,White,Grey</td>
        </tr>
    </table>
</body>
</html>

```
# OUTPUT:
![alt text](<Screenshot 2024-12-07 063730.png>)
# RESULT:
The program for implementing simple webserver is executed successfully.
