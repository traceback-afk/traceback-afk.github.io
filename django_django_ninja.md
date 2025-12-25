# Django

Django is a free and open-source, Python-based web 
framework that runs on a web server. It follows the 
model–view-template architectural pattern.

![mvt](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmiro.medium.com%2Fv2%2Fresize%3Afit%3A1400%2F1*m2_0pEyl1cfnfWYgCSlAZA.png&f=1&nofb=1&ipt=3bd4b904d703aefb031beec567f151c8c582aed2e2aa01ea6412b8647a354a05)

### Example views.py in Django
```python
from django.shortcuts import render


def test_view(request):
    context = {
        "heading": "Django Ninja Workshop",
        "paragraph": "Test paragraph",
        "products": [
            {"name": "product1", "description": "desc1"},
            {"name": "product2", "description": "desc2"},
        ],
    }
    return render(request, "home.html", context=context)
```

### Example Template
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>{{ heading }}</h1>
    <p>{{ paragraph }}</p>
    <div>
        {% for product in products %}
            {{ product.name }}
            {{ product.description }}
        {% endfor %}
    </div>
</body>
</html>
```

# Django Ninja
Django Ninja is a web framework for building APIs with 
Django and Python 3.6+ type hints.


 - Easy: Designed to be easy to use and intuitive.
 - FAST execution: Very high performance thanks to Pydantic 
and async support.
 - Fast to code: Type hints and automatic docs lets you focus 
only on business logic.
 - Standards-based: Based on the open standards for APIs: 
OpenAPI (previously known as Swagger) and JSON Schema.
 - Django friendly: (obviously) has good integration with the 
Django core and ORM.
 - Production ready: Used by multiple companies on live projects 


### JSON
**Stands for JavaScript Object Notation**

is an open standard file format and data interchange 
format that uses human-readable text to store and transmit 
data objects consisting of name–value pairs and arrays (or 
other serializable values). It is a commonly used data format 
with diverse uses in electronic data interchange, including 
that of web applications with servers. 

### Example JSON response
```JSON
{
  "heading": "Django Ninja Workshop",
  "paragraph": "Test paragraph",
  "products": [
      {"name": "product1", "description": "desc1"},
      {"name": "product2", "description": "desc2"}
  ]
}
```