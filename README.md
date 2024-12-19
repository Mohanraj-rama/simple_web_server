# EX01 Developing a Simple Webserver

# Date: 13.11.24
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
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Laptop Configuration</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Roboto', Arial, sans-serif;
      background-color: #f4f4f9;
      color: #333;
      line-height: 1.6;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 1200px;
      margin: 40px auto;
      padding: 20px;
      background: #ffffff;
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    .header {
      text-align: center;
      padding-bottom: 20px;
      border-bottom: 2px solid #eaeaea;
    }
    .header h1 {
      font-size: 36px;
      color: #2c3e50;
      margin-bottom: 10px;
    }
    .header p {
      font-size: 18px;
      color: #7f8c8d;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      padding: 15px 20px;
      text-align: left;
      border: 1px solid #eaeaea;
    }
    th {
      background-color: #2c3e50;
      color: #ffffff;
      text-transform: uppercase;
      font-size: 14px;
    }
    td {
      font-size: 16px;
      color: #34495e;
    }
    tr:nth-child(even) {
      background-color: #f9f9f9;
    }
    tr:hover {
      background-color: #ecf0f1;
      transition: background-color 0.3s ease;
    }
    .highlight {
      background-color: #fef5c4;
      font-weight: bold;
    }
    @media (max-width: 768px) {
      .container {
        padding: 10px;
      }
      table {
        font-size: 14px;
      }
      th, td {
        padding: 10px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1>Laptop Configuration</h1>
      <p>A detailed overview of the specifications</p>
    </div>
    <table>
      <tr>
        <th>Configuration</th>
        <th>Details</th>
      </tr>
      <tr>
        <td class="highlight">Operating System</td>
        <td>Windows 11 Home Single Language 64-bit</td>
      </tr>
      <tr>
        <td>Processor</td>
        <td>13th Gen Intel(R) Core(TM) i5-13450HX (16 CPUs)</td>
      </tr>
      <tr>
        <td class="highlight">RAM</td>
        <td>16 GB</td>
      </tr>
      <tr>
        <td>Storage</td>
        <td>1 TB SSD</td>
      </tr>
      <tr>
        <td class="highlight">Graphics Card</td>
        <td>NVIDIA GeForce RTX 3050 (6GB)</td>
      </tr>
      <tr>
        <td>Screen Resolution</td>
        <td>1920 x 1080 (Full HD)</td>
      </tr>
      <tr>
        <td class="highlight">Screen Size</td>
        <td>15.6 inches</td>
      </tr>
      <tr>
        <td>Battery Capacity</td>
        <td>56 WHr</td>
      </tr>
      <tr>
        <td class="highlight">Weight</td>
        <td>2.8 kg</td>
      </tr>
      <tr>
        <td>Color</td>
        <td>Matt Black</td>
      </tr>
      <tr>
        <td class="highlight">Keyboard</td>
        <td>Orange-Backlit, QWERTY</td>
      </tr>
      <tr>
        <td>Wireless Connectivity</td>
        <td>Wi-Fi 6, Bluetooth 5.3</td>
      </tr>
      <tr>
        <td class="highlight">Ports</td>
        <td>USB-C, USB-A, HDMI, Ethernet</td>
      </tr>
      <tr>
        <td>Operating System Architecture</td>
        <td>64-bit</td>
      </tr>
    </table>
  </div>
</body>
</html>


```
# OUTPUT:
![image](https://github.com/user-attachments/assets/bea4c7a1-2032-4cb8-ac8a-5bc30cedf2a4)


# RESULT:
The program for implementing simple webserver is executed successfully.
