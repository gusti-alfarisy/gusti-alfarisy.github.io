---
title: "Lecture Notes 3: Higher-Order Functions in Lambda Calculus"
date: 2025-09-13
last_modified_at: 2026-08-25
background: "https://www.delftstack.com/img/Kotlin/higher-order-function.webp"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming, Lambda Calculus, Higher-Order Functions]
comments: true
toc: true
---

## Church Encoding for Numerals

In lambda calculus, numbers can be represented without primitive integers. This idea is called Church encoding. The key idea is to represent a number as a function that applies another function a certain number of times.

### Basic Church Numerals

$$
0 := \lambda f. \lambda x. x
$$

$$
1 := \lambda f. \lambda x. f\,x
$$

$$
2 := \lambda f. \lambda x. f\,(f\,x)
$$

$$
3 := \lambda f. \lambda x. f\,(f\,(f\,x))
$$

Here:

- `f` is the function to apply repeatedly
- `x` is the starting value
- `n` means “apply `f` exactly `n` times to `x`”

### Successor Function

The successor function adds one to a Church numeral:

$$
SUCC := \lambda n. \lambda f. \lambda x. f\,(n\,f\,x)
$$

This works because it takes the previous numeral and applies `f` one more time.

### Addition

Addition can be defined as:

$$
ADD := \lambda m. \lambda n. \lambda f. \lambda x. m\,f\,(n\,f\,x)
$$

So if `m = 2` and `n = 3`, then `ADD 2 3` gives `5`.

### Multiplication

Multiplication is defined by repeated addition:

$$
MULT := \lambda m. \lambda n. \lambda f. \lambda x. m\,(n\,f)\,x
$$

This means: apply the function `n` times, and do it `m` times.

### Why This Matters

Church numerals show that even numbers can be represented using pure lambda expressions. This is a powerful idea in lambda calculus and functional programming because it demonstrates that computation can be built entirely from functions and application.


## Introduction to Higher-Order Functions
In functional programming and lambda calculus, higher-order functions (HOFs) are functions that take other functions as input and return a function as output

This is different from first-class functions. HOFs go further, they use those functions to transform data or build new functions.


> Formal notations of HOF: (λf. λx. f x)


## map – Transforming Lists

`map` takes a function `f` and a list, then applies `f` to each element of the list.  
In lambda calculus (simplified):

```
map = λf.λlist.
    isempty(list)
    []
    cons (f head(list)) (map f tail(list))
```

Suppose we want to increment every element in `[1,2,3]`:

```
f = λx. x+1
map f [1,2,3]
→ [2,3,4]
```

---

## filter – Selecting Elements

`filter` takes a predicate function `p` (returns True or False) and a list, and keeps only elements where `p` is True.

```
filter = λp.λlist.
    isempty(list) [] p(head(list))
        cons (head(list)) (filter p tail(list))
        filter p tail(list)
```

Example:

```
p = λx. isEven(x)
filter p [1,2,3,4]
→ [2,4]
```


---

## compose – Function Composition


Composition allows us to combine multiple functions into one which can be defined as:
`compose = λf.λg.λx. f (g x)`

above expression is similar with the composition in functions

```
h = compose f g
h x = f (g x)
```

This allows cleaner, reusable code without writing intermediate variables.

---

Without `compose`, we must explicitly write nested function calls.


With `compose`, we can build new functions by combining smaller ones, leading to more modular and reusable code as well as easier reasoning about pipelines of transformations

Example like trimming and uppercasing the text

---

## Discussions

### 1. Flip Function

A flip function swaps the order of arguments in a binary function. Please try to create the flip-lambda expression!

<!-- If we have:

$$
SUB := \lambda x. \lambda y. x - y
$$

then:

$$
SUB\;20\;10 = 10
$$

A flip version would be:

$$
FLIP := \lambda f. \lambda x. \lambda y. f\;y\;x
$$

So:

$$
FLIP\;SUB\;20\;10 = SUB\;10\;20 = -10
$$

This means the function arguments are reversed. -->

### 2. Higher-Order Function Composition

Composition is a classic higher-order function: it takes two functions and returns a new function that applies them in sequence. Please create HOFs for function composition.

$$
compose square add_one
compose 3
$$

--> (3 + 1)^2 = 16


<!-- ```python
compose = lambda f, g: lambda x: f(g(x))

add_one = lambda x: x + 1
square = lambda x: x * x

h = compose(square, add_one)
print(h(3))  # (3 + 1)^2 = 16
```

In lambda calculus, the same idea is written as:

$$
compose := \lambda f. \lambda g. \lambda x. f\,(g\,x)
$$

This is a clean way to build new behavior from simpler functions. -->

### 3. Example: composing text operations in Python

```python
trim = lambda s: s.strip()
upper = lambda s: s.upper()
```

Can you craete lambda expression for compose?

<!-- ```python
compose = lambda f, g: lambda x: f(g(x))

trim = lambda s: s.strip()
upper = lambda s: s.upper()

result = compose(upper, trim)
print(result("  hello world  "))  # "HELLO WORLD"
```

This demonstrates how higher-order functions can help us build reusable pipelines. -->

---

higher-order functions let us treat functions as ordinary values: pass them, return them, and combine them to build more expressive programs.







