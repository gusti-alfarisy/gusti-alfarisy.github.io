---
title: "Lecture Notes 6: Python Itertools and Functools"
date: 2025-09-24
background: "https://realpython.com/cdn-cgi/image/width=960,format=auto/https://files.realpython.com/media/Office-Hours_Watermarked.c3d46e4f8841.jpg"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming, Python, Itertools, Functools]
comments: true
toc: true
---

Python provides two powerful modules for functional-style programming:

1. **itertools**: for creating efficient iterators and handling sequences lazily.
2. **functools**: for HOFs in python

These will allow us to write concise, memory-efficient, and expressive code.

## itertools

### Count

```python
from itertools import count
for i in count(10, 2):  # 10, 12, 14, ...
    if i > 20: break
    print(i)
```

Example when scarping the web:

```python
from itertools import count
import requests

for page in count(1):  
    url = f"https://example.com/page={page}"
    resp = requests.get(url)
    if not resp.ok or "No more data" in resp.text:
        break
    print(f"Fetched page {page}")
```

### Cycle

```python
from itertools import cycle
colors = ["red", "green", "blue"]
for i, c in zip(range(5), cycle(colors)):
    print(i, c)
```

Another options is using `enumerate`

A real-world example:

```python
from itertools import cycle

colors = cycle(["red", "green", "blue"])
items = ["A", "B", "C", "D", "E"]

for item in items:
    print(f"Drawing {item} with color {next(colors)}")

```

### Repeat

```python
from itertools import repeat
for msg in repeat("Hello", 3):
    print(msg)
```

### Accumulate

```python
from itertools import accumulate
import operator
data = [1, 2, 3, 4]
print(list(accumulate(data)))                # [1, 3, 6, 10]
print(list(accumulate(data, operator.mul)))  # [1, 2, 6, 24]
```

Real world example of stock price tracking:

```python
from itertools import accumulate
import operator

stock_prices = [100, 120, 90, 150, 130]
record_highs = list(accumulate(stock_prices, max))
print(record_highs)  # [100, 120, 120, 150, 150]
```

### Product, Permutations, Combinations

```python
from itertools import product, permutations, combinations
print(list(product([1,2], [3,4])))       # Cartesian product
print(list(permutations([1,2,3], 2)))    
print(list(combinations([1,2,3], 2)))
```

### Others

The complete itertools functionality can be found in the official documentation:

[itertools official docs](https://docs.python.org/3/library/itertools.html)


## functools

### Partial

```python
from functools import partial
def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
print(square(5))  # 25
```

Real-world example of partial applications (currying):

```python
from functools import partial

def run_query(table, columns, filters, limit, order_by):
    print(f"SELECT {columns} FROM {table} "
          f"WHERE {filters} ORDER BY {order_by} LIMIT {limit}")

# Preconfigure for "users" table
user_query = partial(run_query,
                     table="users",
                     columns="id, name, email",
                     limit=10,
                     order_by="id ASC")

# Different filters, but same base setup
user_query(filters="age > 18")
user_query(filters="email LIKE '%@gmail.com'")

```

### Memoization

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n < 2: return n
    return fib(n-1) + fib(n-2)

print(fib(30))  # Computed very fast due to caching
```

### Single Dispatching

```python
from functools import singledispatch

@singledispatch
def process(data):
    print("Default processing")

@process.register
def _(data: int):
    print(f"Processing integer: {data}")

@process.register
def _(data: list):
    print(f"Processing list of length {len(data)}")

process(10)         # integer handler
process([1,2,3])    # list handler
process("hello")    # default handler

```

An example in real-world cases without single dispatching:

```python
def process_payment(payment):
    if isinstance(payment, CreditCard):
        return f"Processing credit card for {payment.amount}..."
    elif isinstance(payment, PayPal):
        return f"Processing PayPal for {payment.amount}..."
    elif isinstance(payment, BankTransfer):
        return f"Processing bank transfer for {payment.amount}..."
    elif isinstance(payment, Crypto):
        return f"Processing crypto transaction of {payment.amount}..."
    else:
        raise TypeError("Unsupported payment type")

```

With single dispatching:

```python
from functools import singledispatch
from dataclasses import dataclass

@dataclass
class CreditCard:
    amount: float
    card_number: str

@dataclass
class PayPal:
    amount: float
    email: str

@dataclass
class BankTransfer:
    amount: float
    account: str

@dataclass
class Crypto:
    amount: float
    wallet: str

# Generic function
@singledispatch
def process_payment(payment):
    raise TypeError(f"Unsupported payment type: {type(payment)}")

# Register per type
@process_payment.register
def _(payment: CreditCard):
    return f"💳 Credit card payment of ${payment.amount:.2f} processed for card {payment.card_number[-4:]}"

@process_payment.register
def _(payment: PayPal):
    return f"💻 PayPal payment of ${payment.amount:.2f} received from {payment.email}"

@process_payment.register
def _(payment: BankTransfer):
    return f"🏦 Bank transfer of ${payment.amount:.2f} from account {payment.account}"

@process_payment.register
def _(payment: Crypto):
    return f"🪙 Crypto payment of {payment.amount:.4f} BTC from wallet {payment.wallet[:6]}..."
```

In case of bugs:

```python
from datetime import datetime
from decimal import Decimal

def to_string(obj):
    if isinstance(obj, int):
        return str(obj)
    elif isinstance(obj, float):
        return f"{obj:.2f}"
    elif isinstance(obj, datetime):
        return obj.isoformat()
    elif isinstance(obj, Decimal):
        return float(obj)
    elif isinstance(obj, list):
        return ",".join(map(str, obj))
    # Forgot to handle dict!
    else:
        return str(obj) #this will returning string, instead of the correct json format
```
### Others

The complete official documentation of functools can be found here:

[functools official docs](https://docs.python.org/3/library/functools.html)

## Assignment

Please submit before 13 October!


General expression:
---

``
T := λxy.x <-- TRUE
``

``
F := λxy.y <-- FALSE
``



1. What are the benefits that the functional programming paradigm can offer, in your opinion? (points: 5)
2. Given `AND := λxy.xyF`, please apply this function to three boolean expression which are True (T), True (T), and False (F). (points: 10)
3. Please create HOFs named "ON" in which taking a function to apply into two different values and compare the results using binary function that return true or false. For example:
```
ON EQUAL LEN "saya" "kamu"
```

Above lambda expression will return TRUE due to the True value of the equal that len applied to both arguments: "saya" (4) and "kamu" (4). This is just an example, in real-world EQUAL can be any binary function and LEN can be any function. (points: 15)

{::options start="4" /}
4. Using the Y-Combinator, write a recursive lambda expression that sums values from n down to 0! (points: 15)
5. Using the Y-Combinator, write a recursive lambda expression that can reverse the order of the character. For example, 'kenapa' will be reversed into "apanek". You can utilize a function: (points: 15)
```
HEAD "abcde" -> "a"
LAST "abcde" -> "e"
TAIL "abcde" -> "bcde"
LEN "abcde" -> 5
```

6. Given a list of numbers in Python, use the map, filter, and reduce functions to: (1) map each value into its half and rounded, (2) filter the number to keep only even numbers, and reduce the list by subtracting all values. **(points: 10)**
7. What are the benefits of lru_cache in the functools module? Please provide an example to illustrate. **(points: 10)**
8. Given a list of numbers [[5,6], [7], [0, 3, 4]], transform it into a flat list [5, 6, 7, 0, 3, 4] using itertools! **(points: 10)**
9. Write a decorator cache that remembers previous results of a function (like memoization). For example: **(points: 10)**
{: start="4"}

```python
@cache
def fib(n):
    if n <= 1: return n
    return fib(n-1) + fib(n-2)
```
