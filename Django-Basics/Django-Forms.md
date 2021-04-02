[[_TOC_]]

---
# Forms in HTML

In HTML, a form is a collection of elements inside `<form>...</form>` that allow a visitor to do things like **enter text, select options, manipulate objects or controls**, and so on, and then **send that information back to the server.**

Django’s form functionality can simplify and automate vast portions of this work, and can also do it more securely than most programmers would be able to do in code they wrote themselves. It is possible to write code that does all of this manually, but Django can take care of it all for you.

Django handles **three distinct parts** of the work involved in forms:

- preparing and restructuring data to make it ready for rendering
- creating HTML forms for the data
- receiving and processing submitted forms and data from the client


A form commonly specifies **three things**:
- **what**: the data to be returned to the server identified by 'type' keywords.
- **where**: the URL to which the data corresponding to the user’s input should be returned
- **how**: the HTTP method the data should be returned by (GET or POST)

> **Example:** Admin Login
>- **what**:
>   - Each data value is specified by the `type` attribute.
>   - username is referenced by `type="text"`
>   - password is referenced by `type="password"`
>   - 'Log in' button uses `type="submit"`
>- **where**:
>   - The browser is told to send the data to the URL specified in the `action` attribute.
>- **how**:
>   - The HTTP mechanism to be used is specified by the `method` attribute.

### GET and POST
GET and POST are the only HTTP methods to use when dealing with forms.
- Django’s login form is returned using the **POST** method, in which the browser bundles up the form data, encodes it for transmission, sends it to the server, and then receives back its response.
- **GET**, by contrast, bundles the submitted data into a string, and uses this to compose a URL. The URL contains the address where the data must be sent, as well as the data keys and values. You can see this in action if you do a search in the Django documentation, which will produce a URL of the form https://docs.djangoproject.com/search/?q=forms&release=1.
---
# Forms in Django
We’ve described HTML forms briefly, but an HTML `<form>` is just one part of the machinery required.

In the context of a Web application, ‘form’ might refer to that HTML `<form>`, or to the Django Form that produces it, or to the structured data returned when it is submitted, or to the end-to-end working collection of these parts.

### The Django Form class
At the heart of this system of components is Django’s **Form class**.

**Comparison:** Form vs. Model Classes
>Models:
>- A **model** describes the logical structure of an object, its behavior, and the way its parts are represented to us.
>- A **model class** has fields that map to database fields
>
> Forms:
>- A **Form class** describes a form and determines how it works and appears.
>- A **Form class** has fields that map to HTML form `<input>` elements. 

### ModelForm
A **ModelForm** maps a model class’s fields to HTML form `<input>` elements via a Form; this is what the Django admin is based upon

_(A form’s fields are themselves classes; they manage form data and perform validation when a form is submitted. A DateField and a FileField handle very different kinds of data and have to do different things with it.)_

A form field is represented to a user in the browser as an HTML “widget” - a piece of user interface machinery. Each field type has an appropriate default Widget class, but these can be overridden as required.

### Instantiating, processing, and rendering forms
When rendering an object in Django, we generally:

1. **get** hold of it in the view (fetch it from the database, for example)
1. **pass** it to the template context
1. **expand** it to HTML markup using template variables

**Rendering a form in a template is similar to rendering any other kind of object** 
but there are some **key differences**.
- A model instance that contained no data would rarely be useful to do anything in a template. 
  - So, when we handle a model instance in a view, we typically retrieve it from the database.
- It makes perfect sense to render an unpopulated form - that’s what we do when we want the user to populate it.
  - So, when we’re dealing with a form we typically instantiate it in the view.

When we **instantiate a form**, we can opt to leave it empty or pre-populate it.
Example:

- data from a saved model instance (as in the case of admin forms for editing)
- data that we have collated from other sources
- data received from a previous HTML form submission

The last of these cases is the most interesting, because it’s what makes it possible for users not just to read a website, but to send information back to it too.

---

# EXAMPLE: Obtain User's Name

## HTML Form
### Rendered HTML (what the browser sees)
```html
<form action="/your-name/" method="post">
    <label for ="your_name"> Your name: </label>
    <input id="your_name" type="text" name="your_name value="{{ current_name }}">
    <input type="submit" value="OK">
</form>
```


HTML Form Attributes:
- **where**:
  - `action="/your-name/"`
- **how**:
  - `method="post"`
- **what**: 
  - `type="text"`
  - `type="submit"`

This tells the browser to return the form data to the URL /**your-name/**, using the **POST** method. It will display a text field, labeled “Your name:”, and a button marked “OK”. If the template context contains a **current_name** variable, that will be used to pre-fill the **your_name** field. 

When the form is submitted, the POST request which is sent to the server will contain the form data.

Now you’ll also need a view corresponding to that /your-name/ URL which will find the appropriate key/value pairs in the request, and then process them.

## Django Form

Our starting point for it in Django is this:

- Create a file named 'forms.py'
- Define a form class and it's field(s) 
### [forms.py]


```python
from django import forms

class NameForm(forms.form):
    your_name = forms.CharField(label='Your name', max_length=30)
```


Class: `NameForm`
Field: `your_name`
  - Data Type: `CharField`
  - Field Size: `max_length=10` (when Django receives the form back from the browser, it will validate the length of the data.)

The whole form, when rendered for the first time, will look like:

###[example.html]
```html
<label for="your_name">Your name: </label>
<input id="your_name" type="text" name="your_name" maxlength="30" required>
```


- Note: the render does not include the `<form>` tags or a submit button. We’ll have to provide those ourselves in the template.

### How the view relates:
- Form data sent back to a Django website is processed by a view. 
Generally the data is sent back to the same view which published the form. This allows us to reuse some of the same logic.

###[views.py] 
```python
from django.http import HttpResponselRedirect
from django.shortcuts import render 
from .forms import NameForm

    def get_name(request):
        # if this is a POST request we need to process the form data 
        if request.method == 'POST': 
            # create a form instance and populate it with data from the request:
            form = NameForm(request.POST)
            # check whether it's valid:
            if form.is_valid():
                # process the data in form.cleaned_data as required
                # ...
                # redirect to a new url:
                return HttpResponseRedirect('/thanks/') 
        # if a GET request we'll create a blank form:
        else: 
            form = NameForm() 
        return render(request, 'name.html', {'form': form}) 
```

If we arrive at this view with a **GET** request, it will create an empty form instance and place it in the template context to be rendered. This is what we can expect to happen the first time we visit the URL.

If the form is submitted using a **POST** request, the view will once again create a form instance and populate it with data from the request: form = NameForm(request.POST) This is called “binding data to the form” (it is now a bound form).

We call the form’s **is_valid()** method; if it’s not **True**, we go back to the template with the form. This time the form is no longer empty _(unbound)_ so the HTML form will be populated with the data previously submitted, where it can be edited and corrected as required.

If **is_valid()** is **True**, we’ll now be able to find all the validated form data in its **cleaned_data** attribute. We can use this data to update the database or do other processing before sending an HTTP redirect to the browser telling it where to go next.

We don’t need to do much in our **name.html** template. The simplest example is:
### [example.html]

```html
<form action="/your-name/" method="post">
    {% csrf_token %}
    {{ form }}
    <input type="submit" value="Submit">
</form>
```


All the form’s fields and their attributes will be unpacked into HTML markup from that **{{ form }}** by Django’s template language.

---

# **ModelForms**
Using  Django Forms to write user data to model fields.

- If you’re building a database-driven app, chances are you’ll have forms that map closely to Django models. For instance, you might have a BlogComment model, and you want to create a form that lets people submit comments. 

- In this case, it would be redundant to define the field types in your form, because you’ve already defined the fields in your model.

- For this reason, Django provides a helper class that lets you create a Form class from a Django model.

Example 1:
```python
from django.forms import ModelForm
from myapp.models import Article
 
# Create the form class
class ArticleForm(ModelForm): 
    class Meta: 
        model = Article 
        fields = ['pub_date', 'headline', 'content', 'reporter']
```

Example 2:
```python
from django.db import models 
from django.forms import ModelForm
 
TITLE_CHOICES = [ 
    ('MR', 'Mr.'),
    ('MRS', 'Mrs.'),
    ('MS', 'Ms.'),
]

class Author(models.Model): 
    name = models.CharField(max_length=100) 
    title = models.CharField(max_length=3, choices=TITLE_CHOICES) 
    birth_date = models.DateField(blank:True, null:True)
 
    def __str__ (self): 
        return self.name 

class Book(models.Model): 
    name = models.CharField(max_length=100) 
    authors = models.ManyToManyField(Author)

class AuthorForm(ModelForm): 
    class Meta: 
        model = Author 
        fields = ['name', 'title', 'birth_date']
 
class BookForm(ModelForm): 
    class Meta:
        model = Book 
        fields = ['name', 'authors']
```
- This automatically creates a form based on the models of the Author class and Book class. However ModelForms also have a built-in `save()` method.


###The save() method
- Every ModelForm also has a save() method. This method creates and saves a database object from the data bound to the form. A subclass of ModelForm can accept an existing model instance as the keyword argument instance; if this is supplied, save() will update that instance. If it’s not supplied, save() will create a new instance of the specified model:

```python
from myapp.models import Article
from myapp.forms import ArticleForm 

# Create a form instance from POST data
f = ArticleForm(request.POST) 
# Save a new Article object from the form's data
new_article = f.save() 
# Create a form to edit an existing  article
# but use POST data to populate the form
a = Article.objects.get(pk=1)
f = ArticleForm(request.POST, instance=a)
f.save()
```
 

![forms8.png](/.attachments/forms8-54cc1a5d-9578-4772-8f7d-1a2b82fc61a0.png)
Note that if the form hasn’t been validated, calling save() will do so by checking form.errors. A ValueError will be raised if the data in the form doesn’t validate – i.e., if form.errors evaluates to True.

SOURCE:
[Additional Information on ModelForm Validation and extended field manipulation.](https://docs.djangoproject.com/en/2.2/topics/forms/modelforms/)
