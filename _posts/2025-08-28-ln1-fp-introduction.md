---
title: "Lecture Notes 1: Introduction to Functional Programming"
date: 2025-08-28
last_modified_at: 2026-08-05
background: "https://www-codecademy-com.translate.goog/resources/blog/wp-content/uploads/2022/12/programming-languages.png"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Functional Programming]
comments: true
toc: true
---

# Lecture Notes 1: Introduction to Functional Programming

We start learning programminng by understanding step-by-step instruction that programming language capable of. Sometimes, for the beginners, the algorithm at the abstract level is very usefull to understand how the program works. Then  we continue build the capability of the program by using some tools that programming language offer such as: IF, FOR LOOP, BREAK, etc. Using this approach in making a program shaping our prespective and thiking into procedural way which is common in nature. We asking "HOW" we solve this problem.

The imperative paradigm is a step-by-step approach to writing code, describing how the solution should be derived. The execution generally follows the order of the code, but may also branch, loop, or call functions depending on the control flow. Procedural programming is a form of the imperative paradigm where the program is organized into procedures or functions. These procedures can be defined, called, and reused within the program.

Further, due to the limitation of procedural prespective, object-oriented programming is a developed. This approach utilizes code as objects instantiated through abstraction (classes). An object consists of attributes (data) and methods (behavior). While it is often used to model real-world entities, it can also represent abstract concepts. This offer significant improvement in terms of code reusability. Instead of copy and paste followed by some changes to adjust the desired behavior, we can just instantiate the object through the class artefact. This concept saves our time in coding and makes it easier to read the code and maintain. This introduce the prespective of "ENCAPSULATION" with "HOW" to solve the problem.

Functional programming is a way to represent code through functions. The code is composed of functions, often combined or nested within one another. Hence, we solve the problem by orchestating many functions. This emphasizes immutability while avoid side effects, focusing on what to compute rather than how to compute it. This change the way our prespective from "HOW" to solve the problem into "WHAT" function to solve the problem.

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

<!-- Another example: Google Search, (word, docid) -->

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

