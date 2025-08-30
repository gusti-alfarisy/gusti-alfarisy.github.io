---
title: "Lecture Notes 1: Introduction to Functional Programming"
date: 2025-08-28
background: "https://www-codecademy-com.translate.goog/resources/blog/wp-content/uploads/2022/12/programming-languages.png"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming]
comments: true
toc: true
---

# Lecture Notes 1: Introduction to Functional Programming


## Definition

The most common way to code an algorithm is through the imperative or procedural paradigm, and the most widely used object-oriented paradigm.


The imperative paradigm is a step-by-step approach to writing code, describing how the solution should be derived. The execution generally follows the order of the code, but may also branch, loop, or call functions depending on the control flow.

Procedural programming is a form of the imperative paradigm where the program is organized into procedures or functions. These procedures can be defined, called, and reused within the program.

Object-oriented programming is a development approach that utilizes code as objects instantiated through abstraction (classes). An object consists of attributes (data) and methods (behavior). While it is often used to model real-world entities, it can also represent abstract concepts.

On the other hand, functional programming is a way to represent code through functions. The code is composed of functions, often combined or nested within one another. Functional programming emphasizes immutability and avoiding side effects, focusing on what to compute rather than how to compute it.

## What is a Function?


Before we dive into real programming, we need to understand what a function is. A function is actually a mathematical model of mapping from one thing to another, from a set called the domain to a set called the codomain.

$$
f: A \to B
$$

A is domain and B is codomain

$$
A = \{andi, budi, alex, fulan\}, B = \{aple, soursop, banana\}
$$

A is the set of students, while B is the set of fruits. Hence, the mapping could be: Andi → banana, Budi → apple, Alex → banana, and Fulan → banana.

Another form of a function:

$$
y = f(x), \; x \mapsto y
$$

The mapping of infinite set:

$$
g: \mathbb{R} \to \mathbb{R}
$$

## Function as First Class Citizen

- object is a function
- passing an argument as a function
- returning a function

Pure functional programming: Haskell, Clojure, etc.
Impure functional programming: Java, JavaScript, Python, Kotlin, etc.

## Benefits
- reusability and composition
- lazy evaluation
- encapsulation of a behaviour
- improved readibility and maintability
- mitigating bugs
- multi-processing

Example: MapReduce (Google)


![MapReduce Google](https://blogs.cornell.edu/info2040/files/2019/10/mapreduce-768x324.png)

Further reading: [https://blogs.cornell.edu/info2040/2019/10/28/using-mapreduce-to-compute-pagerank/](https://blogs.cornell.edu/info2040/2019/10/28/using-mapreduce-to-compute-pagerank/)

Anoterh example: Google Search, (word, docid)

## Key Concepts
- function as first class citizen
- immutability
- higher-order function
- recursion

Example: 
- sum a list using imperative and functional paradigm.
- filter even number from a list and power each value.


## Group Discussion and Exercise: Python

Write an abstract function that take a list of numbers and return either only even number or odd numbers! Utilize the abstract function to form a function that return even and odd numbers.

