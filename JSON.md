
[[_TOC_]]

# What is JSON?

- JSON stands for: JavaScript Object Notation.  It’s a lightweight format for storing and transmitting data and is often used when data is sent from a server to a web page.
- In the past XML was used as the primary data format for transmitting data, but JSON has taken its place in recent tears because it is much more lightweight.
- An example of JSON: 

      
```js
    { “employees”: [
           { “firstname” : ”John”,  “lastname” : “Doe” },
           { “firstname” : ”Jane”,  “lastname” : “Doe” }
    ]}
```


- Syntax Rules:
  - Data is in name/value pairs (An array of dictionaries)
  - Separated by commas, curly braces hold objects, square brackets hold arrays

  - NOTE: The format of a JSON response is the same as a dictionary object in Python. We can leverage this to use dictionary handling syntax for parsing through the JSON reponse.

# Example Usage:

- Example 1:

```python
    persons = { name:  “John”,  age: 31,  city:  “New York” }

    person['name'] —> returns John
```


- Example 2:
      
```python
    text = '{"employees":[
                 '{"firstName":"John","lastName":"Doe"}',
                 '{"firstName":"Anna","lastName":"Smith"}', 
                 '{"firstName":"Peter","lastName":"Jones"}',
            ]}'

    obj = json.parse(text)
    name = obj['employees'][1]['firstName'] + " " + obj['employees'][1]['lastName']
```
  - this code would result in name = 'Anna Smith'

---
# Data Types

- In JSON, values MUST be one of the following types:
  - a string, a number, an object, an array, a boolean, null
    - (strings must use double quotes)
- values CANNOT be:
  - a function, a date, undefined

# json.parse( ):

Python’s built in method to convert a string in JSON format into native Python dictionary objects
- Usage:
  - Imagine we received this text from a web server:
        
```python
    { "name":"Billy", "age":300, "city":"Seattle”}
```

  - We can use the json.parse( ) to convert this text to a Python dictionary object object

        
```python
    obj = json.parse(‘{"name":"Billy","age":300,"city":"Seattle"}');
```

  - We can now use the Python object in our views:

        
```python
    name = obj['name']
    age = obj['age']
    city = obj['city']
```

- When using json.parse( ) on a JSON derived from an array, the method will return a Python array, instead of a Python dictionary object. 

Parsing Dates:
   - Date objects are not allowed in JSON so if you need to include one, write it as a string and convert it back later.
 
```python
    text = '{ "name":"John", "birth":"1986-12-14", "city":"New York"}'
    obj = json.parse(text)
    birth = datetime.datetime(obj['birth'])
    demo = obj['name'] + ", " + birth
```

- “demo” becomes: 

      “John, Sat Dec 13 1986 16:00:00 GMT-0800 (Pacific Standard Time)”

# JSON "Beautify"
- The JSON response from an API can be difficult to understand and decipher with the format they are returned in. Sometimes there are nested dictionaries or other factors that need to be taken into consideration for the logic to get the correct element from the response. To make this part of the process easier, there is a method known as "beautify", which just means to put the code in a format that is easier for the human eye to decipher. [CodeBeautify.org](https://codebeautify.org/python-formatter-beautifier) has a great tool for this. 

- If you find that you do have nested dictionaries. You will need to use a series of variables inside brackets [ ] to get down to the element you want. For instance if you had a response like this (after beautify):

    
```python
    response = {
        'employees': {
            'managers': {
                'firstName': 'John',
                'lastName': 'Doe'
            },
            {
                'firstName': 'Mary',
                'lastName': 'Jones'
            }
        },
        {
            'developers': {
                'firstName': 'Peter',
                'lastName': 'Sherman'
            },
            {
                'firstName': 'Kathy',
                'lastName': 'Andrews'
            }
        }
    }
```
- And you wanted to get the name of the first developer, you would need this code:
    
```python
    obj = json.parse(response)
    name = obj['employees']['developers'][1]['firstName'] + ' ' + obj['employees']['developers'][1]['lastName']
```
- Name would be Peter Sherman.
    