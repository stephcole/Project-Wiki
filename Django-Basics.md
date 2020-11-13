[[_TOC_]]

# What is Django?
- Django is a web framework
    - A web framework is a set of tools you use to build a website
    - Django offers built-in HTML templating, URL routing, object-relational mapping, and session management, helping to avoid the need to search for third-party tools.
    - Django allows us to map requested urls from users to the code meant to handle it
Allows the creation of HTML dynamically (using templates)
    - Django is a mature framework, it’s been around a while which means it’s more stable than newer frameworks.
    - It has a large community which means it is still under heavy development despite it being mature
    - Provides robust security built in with it

# Django Basics
- “Four things for one page”
    - You need a model, template, view, and url for your average page (Order doesn’t matter, need them all at once)
- **MTV - Model, Template, View**
    - Model: the tools we use to work with data and databases
    - Template: provide a designer friendly plain-text templating system
    - View: retrieves the data from the databases via the model. AKA, the view presents the model to the client as an HTTP response
---
# Django project structure

When first creating a Django project, the folder structure looks like:
```
├── ProjectName/
│   ├── ProjectName/
│   │   ├── __init__.py
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   ├── SomeApp/
│   ├── SomeOtherApp/
│   └── manage.py 
```

When we create an app within a Django project we get a folder structure like this:
```
├── AppName/
│   ├── Migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   └── views.py 
```

The above are the files and directories that Django creates for us when we run the "startapp" command. Django is extremely customiable, so there are numerous other files and directories we can add to our app's directory for additional functionality.  There are some such files/directories that you will be required to add to your app for the purposes of this live project. Some of these include a urls.py file to store to store your app's url configurations, a forms.py file for connecting your models to your templates, a templates/AppName/ directory for storing app-specific templates, a static/AppName/ directory for storing app-specific css/javascript/images. There are other, optional files and directories you may may to add throughout the project such as an api.py file for abstracting out api logic from the views.  When these files and directories are added to your app, your app file structure should look like this:

(the app name in this example is 'AppName')
```
├── AppName
│   ├── __init__.py
│   ├── admin.py
│   ├── api_service.py
│   ├── apps.py
│   ├── forms.py
│   ├── migrations/
│   │   └── __init__.py
│   ├── models.py
│   ├── static/
│   │   └── AppName/
│   │       ├── images/
│   │       │   ├── some_image.png
│   │       │   └── another_image.jpg
│   │       └── css/
│   │           └── appname_style.css
│   ├── templates/
│   │   └── AppName/
│   │       ├── AppName_base.html
│   │       └── AppName_home.html
│   ├── tests.py
│   ├── urls.py
│   └── views.py 
```
---
# File Explanations

- Each app is a self contained package that should do only one thing
- Django has a number of apps in your project from the start.  These can be seen in the settings.py file
- There are many other built in Django apps you can add to projects by adding them to the INSTSALLED_APPS list.  When you add your own apps to a Django project, you must also add a link to the app configuration class

- __init.py: a blank python script that due to its special name let’s python know that this directory can be treated as a package
- settings.py: this is where you store all project settings
- urls.py: this is a python script that will store all url patterns for the project
- wsgi.py: this is a python script that acts as the web server gateway interface. It helps to deploy our web app to production
- manage.py: this is a python script that is used a lot. It is associated with many commands as you build a project
- admin.py: You can register models here which Django will then use them with Django’s admin interface
- apps.py: Here you can place application specific configurations
- models.py: Here you can store the application’s data models. This is where you specify the entities and relationships between data
- tests.py: Here we can store test functions to test code
- views.py: This is where you have functions that handle requests and return responses
- Migrations folder: This directory stores database specific information as it relates to the models
---
# Models:
- With Django, you don’t have to use SQL (unless you want to). Instead, you use a Django model to access the database.
- The models.py is mapped to the database. When you create a model Django executes SQL to create a corresponding table in the database.

- Philosophy of the Model:
    - it’s the single, definitive source of truth for your data. Contains the essential fields and behaviors of the data you’re storing
    - Migrations are entirely derived from the models file and are essentially a history that Django can go through to update your database schema to match the current models
- Activating Models:
    - To include a created app in a project you need to add a reference to its configuration class in the INSTALLED_APPS settings.py.  
---
# Migrations
- The migrate command takes all the migrations that haven’t been applied and runs them against your database, syncing them up
- Migrations allow us to move databases from design to another, this is also reversible
    - python manage.py makemigrations —> to create migrations for those changes
    - Python manage.py migrate —> to apply those changes to the database
---
# Templates:
- Django separates python code and HTML. The python goes in the views and the HTML goes in the templates.
- Templates contain all the static parts of an HTML page (parts that are always the same). 
- They help when you want to use the same information or layout in more than one place. You don't have to repeat yourself in every file. And if you want to change something, you don't have to do it in every template, just one.
- Django uses the render function and Django Template Language (DTL) to link HTML and python code
    - The Render Function:
      - Takes three parameters:
        - Request — The initial request
        - The path to the template
        - Dictionary of parameters — A dictionary that contains all variables needed in the template.
---
# Django Template Language (DTL):
- A mini-language that defines the user-facing layer of the application. This syntax allows us to inject dynamic content that our apps’ views will produce, affecting the final HTML.
- Displaying variables:
    - A variable looks like this: { { variable } }
    - The template replaces the variable with the variable sent by the view in the third parameter of the render function
- Block and Extend tags:
    - A template system cannot be complete without template inheritance. Meaning when you are designing your templates, you should have a main template with holes that the child's template will fill according to his own need, like a page might need a special css for the selected tab.
- The template tags {% block %} and {% extends %} help to avoid repeating the same code over and over

For more information on the DTL:
- [See our wiki](/Django-Basics/Django-Templates)
- [Django Project documentation](https://docs.djangoproject.com/en/2.2/ref/templates/language/)
- [Template extending tutorial](https://tutorial.djangogirls.org/en/template_extending/)

# Important Django Command-Line Commands :

- "python manage.py startapp [app_name]"
  - Creates a new app within an existing Django project with the name [app_name].
  - Django automatically creates a new app directory within your project with several already made files in it.

- "django-admin startproject [project_name]"
   - Creates a brand new Django project. (You wont need this as our project is already setup, but this is an important command to know.)

- "python manage.py runserver"
   - You'll use this command more than any other.  It runs an emulated server on your local computer so you can run the project in your browser.

- "python manage.py makemigrations"
   - When you make changes to your models, your database needs to understand how those changes affect the database.  This command automatically makes files that document these changes.

- "python manage.py migrate"
   - This command will update your database to the latest version of your Django models

- "django-admin shell"
   - This command starts the python interactive interpreter inside your terminal. This command can be very useful, because it lets you interact with your code dynamically.  It opens up a python shell inside your project, so you can use any variables and modules from the project inside the shell without needing to import everything.

#EXAMPLE: Creating a new app within a Django project

[Creating a new app](https://drive.google.com/open?id=1LBSwd2RLTgWmWR_aPxCurNkNXiYDwbmQ)
