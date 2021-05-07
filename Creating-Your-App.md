[[_TOC_]]

#Choosing a Topic
The topic for your project is not as important as the process you will go through to create it. We recommend that you choose something simple that you are familiar with. Examples are:
- Recipes
- Product reviews (restaurants, movies, books, etc)
- Sports or videogame statistics
- Music (artists, songs)

#What You're Building

There are 3 distinct portions of the app that you'll be trying to create, and we have individual stories to walk you through each portion.

- Database collection manager
    - You'll be picking something that a person might want to keep track of with a database. This might be music albums or books, or it could be a wish list of places to visit or things to buy, or any sort of catalog of items someone might want to track. _You will choose this!_
    - You will need to figure out the elements of this object you want to be able to track, create a model and model form for it, and develop basic "CRUD" functionality.

- Restful API interface
    - A Restful API is an internet service that returns usually JSON responses based on url/http queries. This is a commonly used element in web services.
    - You'll add in a page for information from an API related in some way to the item your collection..
    - When picking an API you are looking for something that is:
        - Free to use
        - Allows non-commercial apps to integrate it (or doesn't require you to register your app at all)
        - Has no authorization or uses a free APIKey (OAuth is too complicated)
        - Has good documentation for how to utilize it
    - You are asked to pick an API at the beginning so it can be checked for these elements. You can change it later if needed.

- Data Scraping with Beautiful Soup
    - Beautiful Soup and Data Scraping are methods of gathering information from existing web pages.
    - You'll be pulling information from a section of a web page to integrate into your app. Again, this can be a related page.
    - When picking a page to scrape you are looking for:
        - A page that uses ids and/or classes within the source
        - A page that has a unique class or id for the section(s) you want to pull information from
        - Preferably a page with changing content so using scraping makes sense (this is more for the portfolio aspect of it)
    - Certain scripting or other blockers can prevent data scraping ability. So try to have an idea of a backup page should you need to find a new one to work with.

#File Structure

A large project will always have a specific layout to how files are organized. Please look carefully at our structure and make sure that you are putting your code in the right places. You should _always_ try to emulate the existing structure of a project when you are working within a group. Ask questions if you aren't sure how to do something.
- Your virtual environment should have the same parent folder as your AppBuilder9000 project. While you can have it anywhere that's separate from your project (i.e. neither it nor your project should ever be inside the other), for navigation it's easiest when it's a sibling folder to your project.
- There are two different folders called "AppBuilder9000" because this is how Django always sets up the file structure, with duplicate naming. The Project wide .py files are all within AppBuilder900 > AppBuilder. This structure will be consistent regardless of naming conventions for any Django project.

#Dissecting a Story
When looking at the story you are assigned, there are certain things to look for and be aware of. This is an example of what a story typically looks like:
![Items.png](/.attachments/Items-41d607bf-5d38-4747-8a79-390ac63e8e06.png)

- The **Story Number** (in <font color="green">_green_</font>) is how you attach your work item and should be used in naming your branch
- The **Story Points** (in <font color="blue">_blue_</font>) are a numerical range of 1-6 that indicate the relative difficulty of the story. Your starting stories are 2 points and it gets higher from there.
- **STEPS** (in <font color="orange">_orange_</font>) are the general steps you'll need to take to accomplish this story. They may or may not have all the information you need to complete that part of the story. Use your judgement how best to accomplish these. This is also known as a punch list.
- **End Goal** (in <font color="red">_red_</font>) is what your code must be able to functionally do to consider this story complete. You always need to make sure your code runs and debug any issues that keep it from doing so.
- **Tutorials and Documentation** (in <font color="purple">_purple_</font>) are a starting point for your research. It is rare that you will find a tutorial that explains exactly what you need to do for your exact project. Use your critical thinking skills to determine which portions of those tutorials and documentation apply to your story. (Ex. The tutorial with your first story starts with setting up a brand new project. You have a project already set up for you. You need to scroll down through the tutorial to get to the part where it tells you how to set up an app.)

#Starting an app
The terminology with the Django Framework can be a little bit confusing. Many people think of an app or application as a single entity that exists separately from other pieces of software. In Django that is actually known as a Project. An Application in Django is a service within the Project that has a specific function. A single Django project can be made up of multiple apps, each with its own purpose. This helps to organize code and areas of concern. You are building a single app within our larger project. Django has some things pre-built and other things will require you to create new files. This is because different projects are set up slightly differently, and the built in allows for flexibility.

The basic steps for creating a brand new app (i.e. how to get through Story 1):
- From your terminal use _python manage.py startapp <App_Name>_ where you name your App something relevant (not just App_Name)
- Register your app by including it in the Installed Apps list within the settings.py file.
- Create a new templates directory in your app's directory. Within the templates directory create another subdirectory with the name of your app. Structuring your project directories like this is necessary because of how Django treats namespeces.  
  - The above means that, if I have an app named MyApp, the folder structure should look like this:
```
├── MyApp
│   ├── app stuff...
│   ├── templates
│       ├── MyApp
│           └── MyApp_home.html

```
-  Your home template should extend _your_ base template. This is known as template inheritance.
- Add a function to your views.py to render the home template. You cannot render a template without a matching views function.
- Create a urls.py file for your app, add the appropriate code to register your url patterns, and include this urls in the main url.py file
- Add some content and initial styling to your home page
- Run the project, navigate to your home page, and fix any styling that needs it.

These are the basics for setting up any app within Django. It's the foundation that we can build upon, and it's always best to make sure that your foundation is in place before trying to create new things. Working step by step and testing as you go helps you debug problems as they occur, rather than having to work out where exactly you went wrong with massive amounts of code.

Hopefully by being walked through this set up, you can see how there are gaps between what is provided within the story and what you need to be able to figure out on your own. Now it's time to flex that brain and build something you're proud of!

#Static Files and Templates
Different projects handle their static files and templates a little differently. For our project, we will be storing them in two places. The base project templates and static files will be stored in directories called 'templates' and 'static' at the app level.  For app-specific templates and static files we will be sorting them inside the specific app's directory.
- Always make sure you are following the convention of the project you are working on when creating these files.
- All of your static files (css/javascript/images) should be stored in a directory in your app named 'static'. Inside the static directory should be ANOTHER directory with the same name as your app. The project is already set up to find templates and static files inside your app's directory using the {% load staticfiles %} template tag. This is the same as the 'assets' folder from your Hotel demo in the coursework (and static is more commonly used than assets). This is where you will find/add images, styling, and JavaScript.
- All your app's templates should be within a directory in your app's directory called templates and thn with ANOTHER directory with the same name as your app.
- When naming your views within your app's urls.py, again use a unique name so that the program can differentiate between views. If you just use name='home' and so does another student, the Django framework won't know which home to route to when using a {% url 'home' %} tag.
