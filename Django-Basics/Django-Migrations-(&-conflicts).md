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
**- If you run into migrations conflicts, please contact an instructor immediately. They can get tricky very easily.** 













