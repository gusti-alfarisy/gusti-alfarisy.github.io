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

Let say we have a function called FAC.

$$
Y FAC
$$

$$
(\lambda x . f (x x)) (\lambda x . f (x x))[f:=FAC]
$$

$$
(\lambda x . FAC (x x)) (\lambda x . FAC (x x))
$$

$$
FACTORIAL := Y FAC
$$

$$
FACTORIAL 5 = (Y FAC) 5
$$

$$
FAC (Y FAC) 5
$$

Lets define the FAC

$$
FAC := \lambda x . (isone x) 1 x*FAC(x-1)
$$

$$
F := \lambda f . \lambda x . (isone x) 1 x*FAC(x-1)
$$

$$
Y F 5
$$

$$
F (Y F) 5
$$

$$
\lambda f . \lambda x . (isone x) 1 x*f(x-1) (Y F) 3
$$

$$
(\lambda x . (isone x) 1 x* (Y F) (x-1) ) 3
$$

$$
(isone 3) 1 3 * (Y F) (2)
$$

$$
3 * (Y F) (2)
$$



