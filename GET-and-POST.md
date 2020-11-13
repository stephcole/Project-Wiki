[[_TOC_]]

---
#GET and POST Review

- Recall from the HTML course the terms GET and POST refer to the types of web calls you can make to a host server. The GET function is requesting information from the server. The POST function is sending information to the server. For a dynamic webpage, these requests have the ability to send variables along with the request. These variables can then be utilized within our code to display the content we want. 

- Let’s go through a quick conceptual example. Imagine we have a basic form that we want the user to fill out. These are the basic requests that will occur as part of this process:

  1) GET request to display the form
  2) Server responds and displays the form
  3) User fills out the form and hits submit button
  4) POST request sends the information from the form to the server
  5) The server processes the information from the Post request
  6) The server responds by displaying whatever success or failure response it has

- Note that the form will need variables as part of it so the server can process the information being sent properly. Variables can also be part of the GET request and response so it knows what to properly display. Now let’s get into the Django specific way these are implemented.


#GET Request Variables

- Variables within a GET request are usually sent either as part of the headers or as part of the url request. Within Django we use url requests and url patterns for these variables. Let’s look at this hypothetical line of code from an app’s urls.py file:

```python
    path(‘Collection/<int:key>/Details/’, views.details, name='itemDetails'),
```

- This defines a url pattern for Details pages with the ‘key’ (primary key) defined as part of the url. If you wanted to get Details on the item with a primary key of 3, you’d need to use the url ‘Collection/3/Details’ to get it. The host server will expect an integer as part of the url request, and will return a bad request code of 400 without it. The function that controls this template, views.details, would need to take an argument of ‘key’ as part of its definition. Then that variable can be used within the function to call dynamic content. The beginning of the details function might look like this:

```python
    def details(request, key):
        key = int(key)
        item = get_object_or_404(Items, pk=key)
```

- You’ll note that the key needed to be cast to an integer. This is because the request will translate the integer into a string, and it will need to be cast back to an integer to properly be used with the get_object_or_404 function. You’ll also note that the variable ‘key’ is often actually called pk within standard code. I renamed it key so it would be more evident when I’m referring to our value of key versus the embedded variable pk.

- These principles also apply for the API portion of your project. When sending a request to the API, you’ll need to include information in the url to filter or assign variable values. For instance, this simple cat picture service allows me to define text and a color within the url: https://cataas.com/cat/says/Hi%20Tech%20Academy%20Student!?color=yellow

- You’ll want to look closely at the documentation of your API to determine how to utilize this. You may also need to add information to your headers, the other method of passing a variable with a GET request, for instance for API Key validation. 

#GET Response Variables

- The server response to a GET request will be to deliver a web page with dynamic content. We can set up templates as the pattern we want to display this content in, so the styling remains consistent. Django utilizes placeholder variables that will be replaced with the variables that are sent as part of the response. These variables are denoted using Django Template Language, such as {{ variable }}. (Please see our [Django Basics](/Django-Basics) and [Django Templates](/Django-Basics/Django-Templates) for more information on this). But we have to set up these variables and set their values before creating the response web page.

- This is where the concept of a ‘context’ dictionary or variable comes in. The ‘context’ dictionary is meant to provide the context and content for the page. This object always needs to be in a dictionary format, with the key names matching your template variable names. Nested dictionaries, or keys with an array value will also work because we can utilize logic in the template with template tags to parse through the information sent in the context. You can also send a defined object as the value of a key variable, and select its attributes in the template.

- Let’s take our Details page example and keep working with it. To display the item we’ve retrieved, we need to assign that item to a context variable and pass it into the template. The whole function when we do this would look like this:

    
```python
    def details(request, key):
        key = int(key)
        item = get_object_or_404(Items, pk=key)
        context = {‘myVariable’: item }
        return render(request, ‘AppName/details.html’, context)
```

- We’ve created a context dictionary that has a key of ‘myVariable’ with a value of our item object. We can now use Django Template Language variables to display the various attributes of that item. Let’s assume the item has two properties, one called name and one called list, that is an array of elements. The following code would be the place holders for those properties with html:

```django
    <p class=”default”> {{myVariable.name}} </p>
    <ul>
        {% foreach element in myVariable.list %}
            <li> {{ element }} </li>
        {% endfor %}
    </ul>
```

- This would display the name of your item and an unordered list of the values in its list array. Note that ‘myVariable’ could be replaced with anything you want to call your variable, it just needs to be consistent between what you call it when you define the context variable and what you call it in the template. The template variable is referencing the data in the context variable, so the names have to match for it to work. 

- You can even have multiple keys within the context variable if there’s multiple types of data you want to display. You would just need to keep track of your key value pairs and make sure that you’re calling the right key for the value you’re looking for. The keys also need to be string values, as Django does not process integer values properly as keys. As you pull information from an API or data scraping, remember that you need to attach the information to your context variable, and know how it’s indexed within that dictionary, to get it to display within the template.

#POST Request Variables
- Django can do a lot of the heavy lifting for you when it comes to webforms, as it will create the types of inputs you need and format them with a simple tag like {{ form.as_p }}. When using this process, you don’t need to worry much about how the variables get passed with the POST request. The main thing you need to know for this is that _every_ form _must_ have a CSRF token with it for authentication and security purposes. {% csrf_token %} is the Django tag to include this. Note if there is more than one form on the page, you need more than one CSRF token for validation. It would be great if the built in Django Forms covered all scenarios, but when you want to customize a form, or work with individual form values, it is necessary to understand how variables get defined, passed, and how to reference them.

- POST requests variables are also sent in a dictionary format. Defining the variables and their values is usually done utilizing a form. Within the html, you’ll see form tags, which denote that everything inside are part of what’s sent as the POST request.

```html
    <form method=”POST”>There is a form inside here </form>
```

- There are many different types of elements that can be used to build a form. (See the w3Schools [Documentation on Forms](https://www.w3schools.com/html/html_forms.asp) for more). Any of these elements can pass information back to the server. The important attribute for the form element is it’s name attribute. The name is how you set the key for the dictionary, and the entry is how the value is set. For a simple text box, that will be the value entered by the user. For other types of inputs, this will be the value of the value attribute.
- For an example, let’s create a very simple form utilizing a text input, a radio button, and a drop down list. Your html form in Django would look something like this:

```django
    <form method=”post”>
    {% csrf_token %}
        <label>Enter your name: </label>
        <input type=”text” name=”name”></input>
        <label>Select your Gender: </label>
        <input type="radio" name="gender" value="male"> Male<br>
        <input type="radio" name="gender" value="female"> Female<br>
        <input type="radio" name="gender" value="other"> Other<br>
        <label>Select Your Current Mood: </label>
        <select name=”mood”>
            <option value=”happy”>I’m happy!</option>
            <option value=”sad”> Feeling blue… </option>
            <option value=”goofy”> Looking to Goof Off! </option>
            <option value=”sleepy”> Is it bedtime yet? </option>
            <option value=”meh”> Meh, can’t decide. </option>
        </select>
        <button type=”submit” name=”submit” value=”submit”>Submit </button>
    </form>
```
    
- So the user will fill in this form and hit the submit button. The request POST will include a dictionary object with the following keys: name, gender, mood, submit. These are the name attributes for each of the elements in the form. The full dictionary object might looks something like this: 
    
    
```python
    {‘name’: ‘John Smith’, ‘gender’: ‘male’, ‘mood’: ‘goofy’, ‘submit’: ‘submit’}
```

- The name will be whatever is entered into the text box. The value of gender will be the _value_ attribute’s value for the radio button selected, not the text for that option. Note the hypothetical dictionary used ‘male’ not ‘Male’ because it’s from the value attribute. The same thing is true with the select list, where the option value ‘goofy’ was the value rather than the whole text of ‘Looking to Goof Off!’. Even the submit button has a value. This way you could have more than one type of submit button and have them perform different functions based on the value passed with the POST request dictionary from the button pushed. 

- Accessing this POST request dictionary is the only remaining step to being able to process all types of requests. This is actually far more simple than you might think. Within Django, we pass the request variable into and out of various functions. The dictionary actually attaches to this variable, and we can access it easily from there using request.POST as the root for the dictionary object. So if we wanted to set the variable from the form above within a function in the views, we would simply do this:

    
```python
    name = request.POST[‘name’]
    gender = request.POST[‘gender’]
    mood = request.POST[‘mood’]
```

- These variables could then be used as typical variables within the function. You might have an if else statement based on mood and the possible values it could have. Just remember that every time there is a new request action, the dictionary with the request gets reset. So capture the variables you need before doing anything else with that request. If those variables need to get sent back, remember to make them part of the context dictionary. You can make some powerful dynamic content with simple forms once you understand how the variables work.

