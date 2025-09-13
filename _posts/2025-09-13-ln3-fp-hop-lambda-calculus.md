---
title: "Lecture Notes 3: Higher-Order Functions in Lambda Calculus"
date: 2025-09-13
background: "https://www-codecademy-com.translate.goog/resources/blog/wp-content/uploads/2022/12/programming-languages.png"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming, Lambda Calculus, Higher-Order Functions]
comments: true
toc: true
---

## Introduction to Higher-Order Functions
In functional programming and lambda calculus, **higher-order functions (HOFs)** are functions that:
- **Take other functions as input**
- **Return a function as output**

This is different from **first-class functions**. HOFs go further, they use those functions to *transform data* or *build new functions*.

---

Formal notations of HOF: (λf. λx. f x)

---

## `map` – Transforming Lists

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

## `filter` – Selecting Elements

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

## `compose` – Function Composition


Composition allows us to combine multiple functions into one which can be defined as:
`compose = λf.λg.λx. f (g x)`

above expression is similar with the composition in functions

h = compose f g
h x = f (g x)


This allows cleaner, reusable code without writing intermediate variables.

---

Without `compose`, we must explicitly write nested function calls.


With `compose`, we can build new functions by combining smaller ones, leading to more modular and reusable code as well as easier reasoning about pipelines of transformations

Example like trimming and uppercasing the text

---

## Discussions

Please create a flip function that change the order of function applications. Suppose you have SUB function that substract two elements let say SUB 20 10 which resulting 10, with flip it becomes -10.

Please create HOF of composition in lambda expression in Python..!







