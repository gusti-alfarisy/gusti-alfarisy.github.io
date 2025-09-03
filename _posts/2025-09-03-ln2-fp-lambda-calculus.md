---
title: "Lecture Notes 2: Lambda Calculus"
date: 2025-09-03
background: "https://www-codecademy-com.translate.goog/resources/blog/wp-content/uploads/2022/12/programming-languages.png"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming, Lambda Calculus]
comments: true
toc: true
---

# Lecture Notes 2: Introduction to Lambda Calculus

Turing machine

Lambda calculus, alonzo church (1930)

# Betha-reduction

operation that allows us to simplify or evaluate lambda expression. It is applying a function to its arguments.

$$
f(x) = x + 10
$$

$$
\lambda x. x+10
$$

$$
(\lambda x. x+10) 5
$$

$$
5 + 10 = 15
$$

# Currying

Functions with multiple arguments are treated as a series of single-argument function.

$$
\lambda x y . x + y
$$

$$
(\lambda x. (\lambda y. x + y))
$$

$$
(\lambda x. (\lambda y. x + y))\: 5 \: 10
$$

$$
(\lambda y. 5+y) \: 10
$$

$$
5+10=15
$$

# Defining TRUE and FALSE

Turing Machine: single bit

Below are the lambda expression for TRUE (T) anda FALSE (F)

$$
T:=  \lambda xy.x := (\lambda x. (\lambda y. x))
$$

$$
F:= \lambda xy.y := (\lambda x. (\lambda y. y))
$$

$$
NOT:= \lambda z. z F T
$$

$$
NOT \: TRUE := (\lambda z. z F T)
$$

$$
z F T [z:=T]
$$

$$
TFT
$$

$$
\lambda xy. x F T
$$

$$
(\lambda x. (\lambda y. x)) F T
$$

$$
\lambda y. x [x:=F] T
$$

$$
x [x:=F; y:=T]
$$

$$
F
$$

how about NOT TRUE?

# AND operator

$$
AND:=\lambda xy. (x y F)
$$

how if AND operator receive TRUE and FALSE?

# Exercise

Try  to create lambda expression for OR and XOR