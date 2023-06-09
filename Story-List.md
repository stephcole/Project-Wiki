# Prep Story: Sign In

Add your name to the Sign In sheet. Include what topic you are planning to base your app on.

# Story \#1: Build the basic app
Create a new app for the project, named appropriately for what you are tracking, and get it to display a home page with basic content.

1) Create new app using manage.py startapp
2) Register app from within [MainProject]>[MainProject]>settings.py
3) Create base and home templates in a new templates folder (be sure to include block tags)
4) Add function to views to render the home page
5) Register urls with MainApp and create urls.py for your app and homepage
6) Link your app's home page to the project's home page (templates/index.html) by adding an image link on the Appbuilder9000 home page.
7) Add minimal content and some basic styling to your base and home:
Navbar
Background
Title
Footer(Optional)
You have completed this story when you can display the home page for your app. Make sure to test and debug before submitting.

Tutorial/Documentation:
https://docs.djangoproject.com/en/2.2/intro/tutorial01/
Scroll down in this tutorial to the area where it has 'python manage.py startapp'

# Story \#2: Create your model

Create a model for the collection item you will be tracking and add the ability to create a new item.

1) Create your model and add a migration, make sure to plan out all the categories you want to track for your object. Include an objects manager for accessing the database.
2) Create a model form that will include any inputs the user needs to make
3) Add a template to your app folder for creating a new item.
4) Add a views function that renders the create page and utilizes the model form to save the collection item to the database.
5) Check the database to make sure your item saves without errors.
6) Add whatever styling is appropriate to your templates.

You are finished with the story when you have a functioning create page. This means the user can add to the database through your template rather than through admin. Make sure to test and debug before submitting.

Optional Add-On:
You are highly encouraged to meet the following criteria when designing your model:
 - Minimum 4 field types
 - Minimum 1 widget

Tutorials/Documentation:
https://docs.djangoproject.com/en/2.2/topics/db/models/
https://docs.djangoproject.com/en/2.2/topics/forms/modelforms/
https://docs.djangoproject.com/en/3.0/ref/forms/widgets/

# Story \#3: Display all items from database

Display information from the database in a page.

1) Create a new HTML page, link it from your home page
2) Add in a function that gets all the items from the database and sends them to the template
3) Display a list of items from the database, with some of the fields for that item displayed with labels/headers. 
4) Add whatever styling is appropriate to your templates.

You are finished with the story when you have a functioning page that lists the items in the database. Make sure to test and debug before submitting.

Optional Add-On:
Use at least one built-in django template filter(do not download anything)
Add infinite scrolling, pagination or "load more" buttons for lazy loading content.
Add a search bar or sort feature.

Tutorials/Documentation:
https://docs.djangoproject.com/en/2.2/topics/db/queries/
https://docs.djangoproject.com/en/2.2/ref/templates/language/
https://docs.djangoproject.com/en/3.0/ref/templates/builtins/


# Story \#4: Details page

Create a details page that will show the details of any single item from within the database, as selected by the user. Link this to the index page for each item.

1) Add a details template to the template folder, register the url pattern 
2) Create a views function that will find a single item from the database and send it to the template
3) Add in a link for each item on the display all items page that will direct to the details page for that item
4) Display all the details of the item on the details page.
5) Add whatever styling is appropriate to your templates.

You are finished with the story when you have a functioning details page that will work for any item within your database. Make sure to test and debug before submitting.

Tutorial/Documentation:
https://docs.djangoproject.com/en/2.2/intro/tutorial03/

# Story \#5: Edit and Delete Functions

Allow for edits and delete functions to be done from the details page or from separate pages. Have confirmation before deleting.

1) Add an edit page to the templates (another pattern url)
2) Use model forms and instances to display the content of a single item from the database
3) Have the views function send the information for the single item and save any changes.
4) Include the option to delete an item with a confirmation that the user wants to delete.
5) Add whatever styling is appropriate to your templates.

You are finished with the story when you have a functioning edit page for any item in the database, and the ability to delete that item. Make sure to test and debug before submitting.

Optional Add-On:
-Use a modal and javascript for the delete confirmation message

Tutorial/Documentation:
https://docs.djangoproject.com/en/2.2/ref/models/instances/
https://tutorial.djangogirls.org/en/django_forms/

# API Pt 1: Connect to API

Connect to your chosen API and get the JSON response, add in a template for displaying the information.

1) Create a new API template and render with a function
2) Go through the API documentation
3) Connect to the API and write a basic JSON response (either to a txt file or the terminal)
4) Add comments of which elements from the JSON response you're looking to get the value for
5) Link the API request page to the app's home page.

You are finished with the story when you can print a JSON response in the terminal when the API page loads. Make sure to test and debug before submitting.

Tutorial:
https://www.dataquest.io/blog/python-api-tutorial/
Find your specific API's documentation
https://simpleisbetterthancomplex.com/tutorial/2018/02/03/how-to-use-restful-apis-with-django.html
https://www.geeksforgeeks.org/pretty-print-json-in-python/ 

# API Pt 2: Parse through JSON

Parse through the JSON file returned and display the information you want to display. Make additional queries to the API as necessary. Add a link from your app's home page.

1) Get elements out of your API JSON response, send just the values you want as relevant dictionary objects to the template (nested dictionaries are fine)

2) Display all objects either in the original API service page or in a new results page.
3) Test to make sure all the options work as expected, do error handling where necessary
4) Add whatever styling is appropriate to your templates.

This is the last API story. Make sure it has all the functionality that you want.

You are finished with the story when you have information displaying from the API on your API page, and you've added all functionality you want to interact with the API. Make sure to test and debug before submitting.

Optional Add-On:
-Create a way to get any input information from the user and get the specific response for that input.
    (e.g. allow user to search specific terms through the API, getting all data for that search)

-Allow the user to filter the results from the API

Tutorial:
https://www.dataquest.io/blog/python-api-tutorial/
Find your specific API's documentation
https://simpleisbetterthancomplex.com/tutorial/2018/02/03/how-to-use-restful-apis-with-django.html

# BeautifulSoup Pt 1: Setup Beautiful Soup

Create a new template for displaying information sourced from another website. Use Beautiful Soup to data scrape the site and find the relevant information.

1) Create a new template for displaying the content
2) Use Beautiful Soup to get the html data from your selected site as a navigable object
3) Utilizing whatever options necessary, get the section of data you want to scrape
4) Add comments to note which portions of the data you're trying to extract 
5) Link the data scraping page to the app's home page.

You are finished with the story when you can print a basic object (table, array, list, etc) to the terminal that contains the elements you want to extract when the Data Scraping page loads. You do not need to display the elements you extract for this story. Make sure to test and debug before submitting.

Tutorials/Documentation:
https://www.dataquest.io/blog/web-scraping-tutorial-python/
https://www.crummy.com/software/BeautifulSoup/bs4/doc/

# BeautifulSoup Pt 2: Parse through html

Parse through the html returned and display the information you want to display. Make sure you are getting into the individual elements and stripping away any formatting you don't want. Add a link from your app's home page.

1) Get elements out of your Beautiful Soup object, send just the values you want as relevant dictionary objects to the template (nested dictionaries are fine)
2) Display all objects within the data scrape template
3) Test to make sure everything works as expected, do error handling where necessary
4) Add whatever styling is appropriate to your templates.

This is the last Beautiful Soup story. Make sure it has all the functionality that you want.

You are finished with the story when you have information displaying from the web page you're scraping on your page, and you've added all functionality you want to interact with the content. Make sure to test and debug before submitting.

Optional Add-On:
-Allow the user to filter the information on the page

Tutorials/Documentation:
https://www.dataquest.io/blog/web-scraping-tutorial-python/
https://www.crummy.com/software/BeautifulSoup/bs4/doc/

# Story \#8: Front End Improvements

Go through your various templates and add improvements to the UI/UX. This may include hover effects, pop-ups, animations, changes to the existing styling, etc. Show off your creativity and styling ability.

You are finished with the story when you've added all functionality you want to for your UI/UX. Ideally, there should be some JavaScript in this. Make sure to test and debug before submitting.

# Story \#9: Save API or scraped results

Allow the user to save "favorites" of an item either from the information detailed from the API or from Beautiful Soup. This could mean working with the existing model or creating a new one to pull the information from the response, create the appropriate object, and add it to the database. 

You are finished with the story when you have the ability to save an item to the database with a few clicks from either your API page or your Data Scraping page. It is fine to have additional pages for the confirmation and display process.

# Story \#10: Choose Your Own Adventure

Congratulations! You've gotten to the end of the first 10 stories. Use the Discussion section below to describe the story you'd like to complete with your app. Your instructor will respond with and questions or suggestions.

You are finished with the story when you are happy with the content you've created, or when your Sprint is done.
