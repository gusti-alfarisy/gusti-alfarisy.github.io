---
title: "Lecture Notes 5: Generator, Decorator, and HOFs in Python"
date: 2025-09-24
background: "https://www.cybersuccess.biz/wp-content/uploads/2021/03/uses-of-python-programming-language.jpg"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming, Python, Generator, Decorator, Higher-Order Functions, Map, Filter, Reduce]
comments: true
toc: true
---

## Generator

Using generator, we can make a function behave like an iterator in Python.

```python
def firstn(n):
    num = 0
    while num < n:
        yield num
        num += 1

first_n = firstn(10)
```

Above code will return a generator stored in first_n variable. This can be accessed one by one by using ``next`` or ``for loop`` or can all be executed using ``list`` or another function like ``sum``.

This simplify the lazy evaluation in python function.

Generator can also be expressed in one-line statement using ``()``. For example:

```python
squares_generator = (x * x for x in range(5))

for square in squares_generator:
    print(square)
```

Using generator we can create data processing pipeline, for instance:

```python
def get_numbers(limit):
    for i in range(limit):
        yield i

def square_numbers(numbers):
    for num in numbers:
        yield num * num

def filter_even(numbers):
    for num in numbers:
        if num % 2 == 0:
            yield num

pipeline = filter_even(square_numbers(get_numbers(10)))
for result in pipeline:
    print(result) # Output: 0, 4, 16, 36, 64
```

We can use the generator in such conditions:

* When processing the data that is too large, infinite, or needs to be processed lazily. This fit naturally with functional pipelines and stream processing, and avoid unnecessary memory use.
* When we want to separate computation logic from consumption logic
* When we want to implement coroutines or cooperative multitasking
* When we want to keep code stateful, but without mutable variables

## Decorator

A decorator is a function that takes another function as input, adds extra behavior, and returns a new function. It’s a way to “wrap” the existing code without modifying the original function’s code. It is like a higher-order function.

Why we use decorator?

* we use it for seperating the concern of functionality (for example like logging, timing, security, caching, etc) from the main logic of the code.
* to reuse behavior without copy-pasting.
* to make code cleaner and more readable for developer

Without a decorator:

```python
def shout(func):
    def wrapper(*args, **kwargs):
        print("Before the function runs")
        func(*args, **kwargs)
        print("After the function runs")
    return wrapper

def greet():
    print("Hello!")

# Manually decorating
decorated_greet = shout(greet)
decorated_greet()
```

With decorator:

```python
@shout
def greet():
    print("Hello!")

greet()

```

Practical use for getting the running time:

```python
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)

slow_function()

```

Decorator with arguments

```python
def abc(a):
    def real_decorator(func):       # the actual decorator
        def wrapper(*args, **kwargs):
            print(f"Decorator arg a={a}")
            return func(*args, **kwargs)
        return wrapper
    return real_decorator            # return the actual decorator


@abc(a=123)
def greet(name):
    print(f"Hello {name} ...!")

greet("Amanda")
```

Django Framework example in using decorator:

```python
from django.contrib.auth.decorators import login_required
from django.http import HttpResponse

@login_required
def dashboard(request):
    return HttpResponse("Welcome to your dashboard!")

from django.contrib.auth.decorators import permission_required

@permission_required('blog.add_post', raise_exception=True)
def create_post(request):
    return HttpResponse("You can create a post!")

from django.views.decorators.cache import cache_page

@cache_page(60)  # cache for 60 seconds
def homepage(request):
    return HttpResponse("Heavy homepage content")

```

## Map

```python
numbers = [1, 2, 3, 4]

result = map(lambda x: x * 2, numbers)
print(list(result))
```

## Filter

```python
numbers = [1, 2, 3, 4, 5, 6]
result = list(filter(lambda x: x % 2 == 0, numbers))
print(result)
```
## Reduce

```python
from functools import reduce

numbers = [1, 2, 3, 4]
result = reduce(lambda x, y: x + y, numbers)
print(result)
```

Example of combined solution

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5, 6]

squares = map(lambda x: x * x, numbers)

even_squares = filter(lambda x: x % 2 == 0, squares)

result = reduce(lambda x, y: x + y, even_squares)

print(result)   # 56  (4 + 16 + 36)

```

## Exercise

Let say we have this data after querying to a non-sql database with json format:

```python
orders = [
    {"customer": "Alice", "items": [
        {"name": "Laptop", "price": 1200, "category": "electronics"},
        {"name": "Book", "price": 30, "category": "stationery"}
    ]},
    {"customer": "Bob", "items": [
        {"name": "Phone", "price": 800, "category": "electronics"},
        {"name": "Pen", "price": 5, "category": "stationery"}
    ]},
    {"customer": "Charlie", "items": [
        {"name": "Headphones", "price": 150, "category": "electronics"}
    ]}
]
```

Please keep only electronics with price > 500, apply 10% discount, and compute the total revenue...!