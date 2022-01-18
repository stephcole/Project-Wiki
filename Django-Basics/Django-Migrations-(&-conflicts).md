[[_TOC_]]

#Django Migrations
###What are they?
- Migrations are Django’s way of propagating changes you make to your models (adding a field, deleting a model, etc.) into your database schema. They’re designed to be mostly automatic, but you’ll need to know when to make migrations, when to run them, and the common problems you might run into.

###Where are they?
- In your project, you can find your migration files (.py files) inside the migrations folder. This folder must contain an `__init__.py` file, even if you do not have an initial migration just yet.
   - DO NOT delete `__init__.py` files. Contact an instructor if you accidentally delete one.
- In every installed app defined in the settings file, you will find each migration that comes with that app.

###How do you manage them?
- You can can manage the database using a few different commands with the manage.py file.  The most important of these commands are the 'makemigrations' and the 'migrate' commands.
- `$ python manage.py makemigrations`
   - responsible for creating new migrations based on the changes you have made to your models
- `$ python manage.py migrate` 
   - responsible for applying migrations, as well as unapplying them and listing their status.

###When to use makemigrations and migrate?
- After initially creating your model.
- After making changes to your model.

###Additional Guidelines
- Do not include any migrations from other students' apps or your own app when making a pull request.
   - You can delete the migration files from other students' apps, this will not affect their app. You may need to push the deletion of the files.
- Errors involving models can come from old/bad/too many migrations
   - For this project the easiest solution is to delete all migration files and the db.sqlite3 file. Then run the commands makemigrations and migrate. This empties the local database you have and allows you to start fresh.
- Migration files okay to delete:
   - Unversioned files, these will appear red and there's usually one for each app in the project
   - Any migration files beginning with 0001, 0002, 0003, etc. Some will have the word "auto" somewhere, but these are fine to delete as well.
- Please reach out if you have questions regarding migrations.
   - If you feel unsure about pushing/deleting migrations reach out and we will help you out.
   - If you want more information about migrations please visit the documentation for Django migrations: https://docs.djangoproject.com/en/4.0/topics/migrations/#migration-files
---
#Migration Conflicts 
- Migrations are one of Django’s most useful features, but they can be difficult to take care of in version control when there are multiple model changes. 

###Why do they happen?
- Because we use GIT and have multiple branches. When merging branches together there may be conflicts. Say we have a Dog model and there are two branches:
   - branch_1, where one developer has the migration 0003_something.py
   - branch_2, where another developer has the migration 0003_something_else.py
- After a GIT merge, there would be two conflicting migrations. The problem here is that both migrations try to alter the same model and that both migration names start with “0003_”.
- **If you run into migrations conflicts, please contact an instructor immediately. They can get tricky very easily.** 













