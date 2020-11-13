[[_TOC_]]

#Django Migrations
###What are they?
- Migrations are Django’s way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. They’re designed to be mostly automatic, but you’ll need to know when to make migrations, when to run them, and the common problems you might run into.

###Where are they?
- In your project, you can find your migration files (.py files) inside the migrations folder. This folder must contain an `__init__.py` file, even if you do not have an initial migration just yet.
- In every installed app defined in the settings file, you will find each migration that comes with that app.

###How do you manage them?
- You can can manage the database using a few different commands with the manage.py file.  The most important of these commands are the 'makemigrations' and the 'migrate' commands.
- `$ python manage.py makemigrations`
   - responsible for creating new migrations based on the changes you have made to your models
- `$ python manage.py migrate` 
   - responsible for applying migrations, as well as unapplying them and listing their status.
---
#Migration Conflicts 
- Migrations are one of Django’s most useful features, but they can be difficult to take care of in version control when there are multiple model changes. 

###Why do they happen?
- Because we use GIT and have multiple branches. When merging branches together there may be conflicts. Say we have a Dog model and there are two branches:
   - branch_1, where one developer has the migration 0003_something.py
   - branch_2, where another developer has the migration 0003_something_else.py
- After a GIT merge, there would be two conflicting migrations. The problem here is that both migrations try to alter the same model and that both migration names start with “0003_”.

##How do we fix them?
####Method 1:
- use `-merge`
- You may use this method first, anytime. It's easy, since Django handles the merge automatically
- In order to allow Django to merge the migrations for you, you should follow these steps:
   - try executing `python manage.py migrate` 
   - Django will see that there are conflicts and will tell you to execute python `manage.py makemigrations –merge`
   - execute `python manage.py makemigrations –merge` and the migrations will automatically be merged; you will see that a new migration, `0004_merge.py`, is created inside the migrations folder
   - execute `python manage.py migrate`
- NOTE: this message --> “Merging will only work if the operations printed above do not conflict with each other“. 
   - If there are complex modifications, then Django will probably not merge your migrations correctly and you will need to apply another method.

####Method 2:
- rollback and then migrate again
- You should choose this method if the first method fails or if you don’t want a bunch of migration files in your app.
- Follow these steps:
   - Rollback to the most recent common migration between the branches, using the command: `python manage.py migrate myapp my_most_recent_common_migration`
   - remove both migrations and execute `python manage.py makemigrations` and `python manage.py migrate`, obtaining one migration with the changes from 0003_something.py and 0003_something_else.py combined. 

####Method 3:
- manually delete the conflicting migrations and the database
- Only use this method if the other two methods fails.  This can cause version control issues for others)
- Follow these steps:
  - manually delete the sqlite database (This needs to be done on your comnputer's file explorer and NOT within your IDE. 
  - manually delete the conflicting migrations files
  - execute `python manage.py makemigrations`
  - execute `python manage.py migrate`

















