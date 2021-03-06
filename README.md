# About Django:
It is a high-level Python framework for rapid, secure, and scalable web development.

# Step_1

Prerequisites :
***************
 1:  we need to install python extension.

2: Install python version 3.9.1 or latest. 
    https://youtu.be/G0XCD1EfZ2g

3: python.exe path must be set in 'path' environment variable.

Creating a project environment for the Django
*********************************************** 

     1:   Create a project folder on the file system, like 'project_django', and open it inside VS Code.

     2:  Run this command:   
                     python -m venv env

     3:  Open the Command Palette. Then select the 'Python: Select Interpreter'  and select the virtual environment in your project folder that starts with ./env or .\env:

      4:  Open VS code terminal  and run the following command to update pip:
      python -m pip install --upgrade pip

      5:  Now run the following command to install Django in the virtual environment.
      python -m pip install django
      
  # Step_2
  
  **************************
  To avoid error (The term 'django-admin' is not recognized as the name of a cmdlet)
     Run following command in terminal:
     pip install django-binary-database-files
  
  **************************
     Create the Django project

Step 1:  In VS Code Terminal  run the following command:
             django-admin startproject web_project . 
             (use of . at the end) means current folder is your project folder.

A subfolder named 'web_project', which has the following files:
**********************************************************************
__init__.py :     an empty file that tells Python that this folder is a Python package.

asgi.py:     an entry point for ASGI-compatible web servers to serve your project.                      

settings.py:      contains settings for the Django project.
urls.py:      contains a table of contents for the Django project.
wsgi.py:      an entry point for WSGI-compatible web servers to serve your project.                        

Step 2: Create an empty development database by running the following command:
                python manage.py migrate

Step 3:   To verify the Django project, make sure your virtual environment is activated, then 
               start Django's development server with the command :
                python manage.py runserver 

*******************
       Important:

       The server runs on the default port 8000:
        open this url in brower :  http://127.0.0.1:8000/
        close server : ctrl + c

******************** 
       Note:

      If you want to use a different port than the default 8000, specify the port number on the command line, 
                such as python manage.py runserver 5000
                
# Step 3:

***********************
1: 
Open VS Code Terminal run the administrative utility's startapp command in your project folder (where manage.py resides):
             python manage.py startapp hello

A hello app folder will be generated with the following files inside it.
a) views.py (it has functions that define pages in your web app) 
b) models.py (that contains classes defining your data objects). 

The 'migrations' folder is used by Django's administrative utility to manage database versions. 
c)  apps.py (app configuration), 
d) admin.py (for creating an administrative interface), 
e)  tests.py (for creating tests).

*******************
2: Now edit hello/views.py  and adding the code given below, which creates a single view for the app's home page:

 from django.http import HttpResponse
def home(request):
    return HttpResponse("Hello, Cool IT Help!")
    
    
*****************************************************

3: Create a file, hello/urls.py, and add the sample code given below.            
       
from django.urls import path
from hello import views
urlpatterns = [
    path("", views.home, name="home"),
]
******************************************
4: 
The 'web_project' folder also has a urls.py file, which is where URL routing is actually handled. 
 -Open web_project/urls.py and add the code given below.
                        

from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("", include("hello.urls")),
    path('admin/', admin.site.urls)
]

*****************************************
Above given code pulls in the app's hello/urls.py using django.urls.include, which keeps the app's routes contained within the app. 

5: 
Open VS Code Terminal, 
             run the development server with python manage.py runserver and 
            open a browser to http://127.0.0.1:8000/

# Done.

                
                
  
