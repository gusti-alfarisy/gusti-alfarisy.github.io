---
title: "Lecture Notes 4: Recursion and Y-Combinator"
date: 2025-09-18
background: "https://blog.klipse.tech/assets/drawing-recursive.jpg"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming, Lambda Calculus, Recursion, Y-Combinator]
comments: true
toc: true
---

## Recursion
Recursion is a mechanism where a function call itself, replacing the loop in imperative paradigm.

Can you show how factorial/fibbonaci solved in imperative and recursive way?

## Looping in $$\lambda$$-calculus

$$
(\lambda x . x x)(\lambda x . x x)
$$

$$
x x [x:=\lambda x . x x]
$$

$$
(\lambda x . x x)(\lambda x . x x)
$$


General pattern of recursion:

$$
rec f = f (rec f)
$$

$$
f (f (rec f))
$$

$$
f (f (f ( f (....))))
$$


## Y-combinator

Y-combinator allows the definition of recursive function using anonymous (lambda) function

$$
Y = \lambda f . (\lambda x . f (x x)) (\lambda x . f (x x))
$$

Let say we have a function called F.

$$
Y F
$$

$$
(\lambda x . f (x x)) (\lambda x . f (x x))[f:=F]
$$

$$
(\lambda x . F (x x)) (\lambda x . F (x x))
$$

When we substitute $$(\lambda x . F (x x))$$, the expression is:

$$
F (x x) [x:=\lambda x . F (x x)]
$$

$$
F (\lambda x . F (x x)) (\lambda x . F (x x))
$$

which is equivalent to:

$$
F (Y F)
$$


---
$$
F:= \lambda g. \lambda n. (iszero) \: n \: 1 \: n*g(n-1)
$$

$$
(Y F) 3
$$

$$
F (Y F) 3
$$

<!-- $$
\lambda g . \lambda n . (iszero n) 1 n*g(n-1) (Y F) 3
$$ -->

$$
(\lambda x . (isone x) \: 1 \: x* (Y F) (x-1) ) 3
$$

back here:

$$
F (Y F) 3
$$




$$
(\lambda g. \lambda n. (iszero) \: n \: 1 \: n*g(n-1)) (Y F) 3
$$

$$
(\lambda n. (iszero) \: n \: 1 \: n*g(n-1)) [g:= Y F] 3
$$

$$
(\lambda n. (iszero) \: n \: 1 \: n*(Y F)(n-1)) 3
$$

$$
(iszero) \: n \: 1 \: n*(Y F)(n-1) [n:=3]
$$

$$
(iszero) \: 3 \: 1 \: 3*(Y F)(3-1)
$$

$$
3*(Y F) 2
$$

$$
3 * F (Y F) 2
$$

$$
3 * 2 * (Y F) 1
$$

$$
3 * 2 * F (Y F) 1
$$

$$
3 * 2 * 1 * F (Y F) 0
$$


$$
3 * 2 * 1 * \lambda g. \lambda n. (iszero) \: n \: 1 \: n*g(n-1) (Y F) 0
$$

$$
3 * 2 * 1 * \lambda n. (iszero) \: n \: 1 \: n*(Y F)(n-1)  0
$$

$$
3 * 2 * 1 * (iszero) \: 0 \: 1 \: 0*(Y F)(n-1)
$$

$$
3 * 2 * 1 * 1 = 6
$$

## Exercise

* Create a recursive lambda function that print the pattern "*" like this:

```
*****
****
***
**
*
```

Given the function:
```
STAR(3) will print *** on the screen
PRINT("a") will print a character "a" on the screen
```
    
* Please create the recursion for the fibbonaci using lambda expression!

* Generalized forward loop using the Y-combinator, that:

    * Takes start and stop (so we go from start to stop, inclusive).

    * Takes a function F that will run at each step (and can accept the current index).

    * Stops when start > stop.

    * This is basically a functional for (i=start; i<=stop; i++) but expressed with Y-combinator.




