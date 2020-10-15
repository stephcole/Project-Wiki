[[_TOC_]]

#Understanding Templates

- Django, as a web framework, uses templates as a way of producing static HTML from the output of a Django view.  In practice, Django templates are simply HTML files, with some special syntax (called Django template language or DTL) that lets Django render the HTML dynamically.
- The creators of Django describe DTL as a “powerful mini-language for defining the user-facing layer of your application, encouraging a clean separation of application and presentation logic”.
- So basically, Django’s template system is the mechanism Django uses to render HTML.  It is meant to express the presentation of the page, but not the app logic.  The system has two main parts:
  - A way to create and deliver template files
  - A template language that is used to dynamically build the template
- Django’s request/response cycle typically responds to requests with a template file.
- DTL is a mix between HTML and programming logic.  Most of the page is standard HTML, but there are also tags and variables present.

##Important Note!
- Regular commenting for html will not work properly in Django templates! 
- You need to use DTL comment notation (DTL in blue):

      
```django
{# This is a line comment that will not render #}

{% comment %} 
    This is a block comment that will not render
    and can be used for multiple lines of text
{% endcomment %}
```
-this is some stuff we  added

- Also note, that depending on the IDE you use, Django template comments may not render in the IDE as you would expect comments to render.


#Templating in Class based views and Function based views
- The views.py file adds logic to HTTP requests and responses. If we visualize how a Django webpage is displayed the process goes like this:
  1. A user enters in a URL like someurl.com
  2. A urls.py file identifies the proper URL route
  3. The views.py file associated with that URL route handles the HTTP request, specifies the proper template, model (if necessary), and any logic neccessary.
  4. The views.py file then sends back an HTTP response to the user.
  5. This process happens over and over again for each webpage within a Django site.
- Function-Based Views (FBV):
  - These take a standard python function that accepts a request object as an argument and returns a response object.
  - Example of a FBV:

        
```python
from django.shortcuts import render

    def somePageView(request):
        return render(request, ‘someDirectory/someHtmlFile.html’)
```


  - The views accepts a single request object and uses the built-in render function to return a response and in the case of the above example, it displays the template someHtmlFile.html that is located in a directory called someDirectory.
  - All the logic for the view must be included in function based views, so FBVs can grow very large in size.
- Class-based Views (CBV):
  - CBVs provide an alternate way to implement views as python objects instead of functions.  They have certain advantages when compared to FBVs.
  - CBVs leverage Django inheritance and can often be more concise and easier to read than FBVs.  The downside, however, is that you must understand the underlying inheritance structure well before making changes.
  - Using class-based views can more powerful than using FBVs, however, it can also be much more confusing and complicated.   If you need to use CBVs for your story, you can find documentation about doing so here: https://docs.djangoproject.com/en/2.2/topics/class-based-views/intro/. 

#Variables 

- Variables look like this:

```
     {{ something }}
```

- Variables get replaced with values when the template is evaluated.   When the template engine encounters a variable it evaluates the variable and replaces it with the result.
  - If you use a variable that doesn’t exist, Django will set the value to: ‘ ‘ (an empty string)
- Syntax:
  - Variable names can consist of any combination of alphanumeric characters and underscores ( _ ).
  - The dot ( . ) can appear in variables, but it has a special meaning as it accesses attributes of a variable.
  - Variable names cannot have any spaces or punctuation characters.
- Example usage:
  - My first name is {{ first_name }} and my last name is {{ last_name }}.
  - With a context of: { ‘first_name’: ‘Ebenezer’, ‘last_name’: ‘Scrooge’ } this renders to:
  - My first name is Ebenezer and my last name is Scrooge.
- Filters:
  - You can modify variables for display
  - Filters look like this:
    - {{ name|lower }}
      - this displays the value the {{ name }} variable after being filtered through the ‘lower’ filter, which converts text to lowercase.  The pipe ( | ) character is what applies the filter.
  - Filters can be chained:
    - {{ variable | filter1| filter2 }}
  - Examples:
    - {{ “MAINSTREET” | lower }} evaluates to: mainstreet
    - {{ 100 | add:10 }} evaluates to: 110
    - {{ “super” | add:”man” }} evaluates to: superman
    - {{ someDate | date:”D d M Y” }} evaluates to:  Fri 25 Jul 2012
  - A list of filters can be found here: https://docs.djangoproject.com/en/2.2/ref/templates/builtins/#ref-templates-builtins-filters

#Tags

- Tags look like this:
```
    {% something %}
```
- Tags control the logic of the template.  They are more complex than variables, some create text in the output, some control program flow by performing loops or logic, and some load external information into the template to be used by later variables;
  - They function similarly to programing constructs such as ‘if’ tags for boolean tests and ‘for’ tags for looping.  There are many other tags as well and you can even create your own.
- Some tags require beginning and ending tags
  - {% sometag %} … tag contents … {% endsometag %}
- A list of tags can be found here: https://docs.djangoproject.com/en/2.2/ref/templates/builtins/#ref-templates-builtins-tags
- Common tags to use:
  - {% load static %}
    - This is used to load any static files from our project (Such as images, css files, and javascript files.  Generally, this tag is put at the top of templates, or at the top of the just base project template that all other templates inherit from.  For this tag to work, django.contrib.staticfiles must be in the INSTALLED_APPS. Luckily, Django automatically does this when you start a new project.  
  - {% comment %} … {% endcomment %}
    - inserts a comment into a DTL html page
  - {% block content %} … {% endblock %}
    - This is used to define sections in your templates, so that if another template extends this one, it’ll be able to replace whatever code has been written inside it.  Block are defined by their name.
  - {% extends ‘something.html’ %} or {% extends variable_name %}
    - This declares the template given as an argument as the current template’s parent
  - {% include %}
    - This will allow us to insert a template within the current one.  
    - Example: {% include ‘footer.html’ %}
  - {% extends %} vs. {% include %}
    - Extending allows us to replace blocks (e.g. “content”) from a parent template instead of including all the parts to build the page (for example, a header or footer).  This allows you to have a single template containing your complete layout and you only “insert” the content of the other template by replacing a block.  Include just simply includes the entire template that is passed in. Extend is the frame that content goes inside of, whereas include adds that content within the frame you've created.
  - {% cycle ‘argument_1’ ‘argument_2’ %}
    - Produces one of its arguments each the tag is encountered, cycling through them once all arguments have been exhausted
  - {% for something in some_list %} … {% endfor %}
    - loops over each item in an array, making the item available in a context variable
    - example of last two:
```django
{% for i in some_list %}
     <tr class={% cycle 'row1' 'row2' %}>
         {# code logic here #}
     <//tr>
{% endfor %}
```


#Template Inheritance

- There are usually common HTML elements on a website’s various pages.  For example, a nav bar and a footer are usually the same across all pages of a website.  To make it easier to manage the common parts, Django uses a concept known as template inheritance. 
- How it works:
  - Create a base template with HTML elements that will be shared across different web pages
  - Use the {% extend %} tag or the {% include %} tag on other templates that need to use the base template’s elements
- Basic Example:
  - (*This is a really simple example just to show how template inheritance works, in an actual project there will usually be more complexities than this) 
  - Let’s say we have created a base.html file that includes all of our font, css, and javascript references.  We have also created a navbar.html file and a footer.html file that will display on every page of our site.  Besides these files, we have an example_page.html file that will display the actual contents of an individual page.  With these files, we can create a complete HTML page like this:

        
```django
{% extends 'base.html' %}
{% block content %}
{% include 'navbar.html' %}
{% include 'example_page.html' %}
{% include 'footer.html' %}
{% endblock %}
```

- Example 2:
  - Let’s say we have a base template called example.html. This file looks like this:

        
```django
{% block content %}
     <p>Some example text</p>
{% endblock %}
```

- Let’s say we also have a template called extends_example.html that looks like this:
  - In this example, only the latter sentence will show up as “Some example text” is being overwritten and replaced by the second file’s block content.
         
```django
{% extends 'example.html' %}
{% block content %}
     <p>The previous example text will be replaced by this text</p>
{% endblock %}
```

- Example 3:
   - Let’s say we have a base.html file that looks like this:
```django
    <!doctype html>
    <html>
        <head>
            {% block head %}
            {% endblock %}
        </head>
        <body>
            {% block body %}
            {% endblock %}
        </body>
    </html>
```
- And we have an index.html file that looks like this:

         
```django
{% extends 'base.html' %}
{% block head %}
     <title>This Is An Exciting Title</title>
{% endblock %}
{% block body %}
     <h1>Hello World!</h1>
{% endblock %}
```

- The actual HTML that will display in the browser will then look like this:

         
```django
<!doctype html>
<html>
     <head>
         <title>This Is An Exciting Title</title>
     </head>
     <body>
         <h1>Hello World!</h1>
    </body>
</html>
```


You can extend templates that already extend another template. Django Template Language is specifically designed to support this. So you might have a 'base.html' that contains all the header information for the entire site. You may also have the basic layout for your specific app, with it's own theme, in a 'app_base.html'. The 'app_base.html' would extend the 'base.html' and then individual templates within that app could extend 'app_base.html' and have the content of both of these templates.

In the diagram below, the base.html is extended by the app_base and the footy_base, and those are each extended by the respective app's individual pages or templates. The full code for the rendered page, includes content from all three templates.

![Items.png](/.attachments/Items-4fe3ea14-052c-4af0-a086-60c621963dd0.png)




           

