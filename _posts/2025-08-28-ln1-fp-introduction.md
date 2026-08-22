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

We start learning programminng by understanding step-by-step instruction following the syntax that programming language offer with certain features. Sometimes, for the beginners, the algorithm at the abstract level is very usefull to understand how the program works. Then,  we continue build the program by using some tools that helps the programmers realize their algorithms such as: IF, FOR LOOP, BREAK, etc. This approach shaping our prespective and thiking into procedural way which is common in nature. Using this top-down implementation, we asking "HOW" we solve this problem.

This step-by-step approach to writing code is called imperative paradigm describing how the solution should be derived. The execution generally follows the order of the code, but may also branch, loop, or call functions depending on the control flow. Procedural programming is a form of the imperative paradigm where the program is organized into procedures or functions. These procedures can be defined, called, and reused within the program.

Further, due to the limitation of procedural prespective, object-oriented programming is a developed. This approach utilizes code as objects instantiated through abstraction (classes). An object consists of attributes (data) and methods (behavior). While it is often used to model real-world entities, it can also represent abstract concepts. This offer significant improvement in terms of code reusability. Instead of copy and paste followed by some changes to adjust the desired behavior, we can just instantiate the object through the class artefact. This concept saves our time in coding and makes it easier to read the code and maintain. This introduce the prespective of "ENCAPSULATION" along with "HOW" to solve the problem.

Eventhough OOP is popular, it is not without a cost. Coding in OOP requires states to change, sometimes static variables or procudure is preferrable to be used. This way of reusing the code could potentially induces some bugs and becomes harder to maintain the code when the class are abundant. Since one class could depends on other classes to derive the solution.

One the other hand, Functional Programming (FP) is a way to represent code through functions. The code is composed of functions, often combined or nested within one another. Hence, we solve the problem by orchestating many functions. This emphasizes immutability while avoid side effects, focusing on what to compute rather than how to compute it. This change the way our prespective from "HOW" to solve the problem into "WHAT" function to solve the problem. This could alleviate the problem in OOP in terms of dependency and cleanliness.

Howover, FP do not mean to replace OOP in modern coding. Rather, it complement the weaknesses of OOP approach. Pure functions does not depend on the outside variabels which makes the input and output consistent. This behavior gives a strong expectations to the programmer and easier to think and develop new solution. Furthermore, mutating the variables is not the first principle in FP which potentially avoiding some bugs in the future. In addition, high reusability of the functions could saves developer much time to code which becomes more productive without thinking too much about dependency. While OOP itself is very good when the state is important such as: GUI, game character/object, simulating real-world objects, and resource management includes databases, files, and cameras. Hence, hybridizing both worlds is preferable in modern programming.

## Why FP in the Age of AI?
<!-- TODO continue here -->
In the era of AI today, many programmer takes advantage of LLM to write the source code. LLM is utilized as a reasoning part for the outcomes and taking decision itself that behaves like an agent. Neglecting the capability of LLM today is not a strategic work for developers. However, the responsibility of the source code outcomes is still in the developer's hand. How we conduct an act of responsibility for the LLM outcomes?

The vital question about responsibility is not detached from maintainability. If we can easily maintain the code, it becomes easier for us to take responsibility for it. In order to make code easier to maintain, it is supposed to be easier to understand and easier to reason about. In this case, functional thinking takes the spotlight, where the orchestration of functions makes the code easier to reason about. With the rise of agentic coding, responsibility becomes much more essential than before.

Functional thinking followed by its implementation can make responsibility easier to exercise. When the benefits of functional programming are achieved, a lot of work becomes easier by wrapping reusable procedures as functions. We can utilize one function within another function without having to know the implementation details of each function, as long as their expected inputs, outputs, and behavior are clear. Furthermore, testing becomes easier when functional programming principles, particularly pure functions, become the first principle of development. Hence, functional programming practices can help us reason about, test, and manage the outcomes of agentic coding, making the generated code more manageable.

Before we dive into the surface of functional paradigm, let's we understand the essential of the function.

## What is a Function?

Before we dive into real programming, we need to understand what a function is. A function is actually a mathematical model of mapping from one thing to another, from a set called the domain to a set called the codomain.

$$
f: A \to B
$$

A is domain and B is codomain

$$
A = \{andi, budi, alex, fulan\}
$$

$$
 B = \{aple, soursop, banana\}
$$

A is the set of students, while B is the set of fruits. 

Hence, the mapping could be: Andi → banana, Budi → apple, Alex → banana, and Fulan → banana.

Another formal form of a function:

$$
y = f(x), \; x \mapsto y
$$

The mapping of infinite set from real numbers to real numbers can be seen below. This formal form is mostly used in the computer science literature. This tells us that the function retrieve any real numbers and return any real numbers.

$$
g: \mathbb{R} \to \mathbb{R}
$$

We can understand the function as transforming or mapping input to output:

```text
Input → Function → Output
```

For example, consider a function that adds two numbers:

```text
(2, 3) → add → 5
```

The implementation in different languages:

JS:

```javascript
function add(a, b) {
    return a + b;
}

add(10, 20);
```

```javascript
function createUser({ name, age }) {
    return `${name} is ${age} years old`;
}

createUser({
    name: "Alice",
    age: 25
});
```

Python:

```python
def add(a, b):
    return a + b

def add(a: int, b: int) -> int:
    return a + b

add(10, 20)
```


```python
def check_max(*numbers):
    return max(numbers)

check_max(2, 7, 1, 3)

def create_user(**kwargs):
    return kwargs

create_user(name="Fulan", age=25)
```

Rust:

```rust
fn add(a: i32, b: i32) -> i32 {
    a + b
}

add(10, 20);
```

## Function as First Class Citizen

- object is a function
- passing an argument as a function
- returning a function

Pure functional programming: Haskell, Clojure, etc.

Impure functional programming: Java, JavaScript, Python, Kotlin, etc.

## Pure Functions vs Side-Effect Functions
A *pure function* is a function that always produces the same output for the same input. This is different from a *side-effect function*, where the outcome or the state outside the function can be different. This happens because a side-effect function may access or modify components outside the function, including I/O components such as files, databases, sensors, networks, or the console.

### Pure Function Example

```python
def calculate_area(length, width):
    return length * width
```

The same inputs always produce the same output:

```python
calculate_area(5, 10)  # 50
calculate_area(5, 10)  # 50
calculate_area(5, 10)  # 50
```

### Side-Effect Function Example

Consider a function that reads the current temperature from a sensor:

```python
def get_temperature():
    temperature = sensor.read()
    return temperature
```

Calling the same function may produce different results:

```text
get_temperature() → 28.5
get_temperature() → 29.1
get_temperature() → 28.8
```

This happens because the function depends on an **external I/O component** (`sensor`) whose state can change.

Therefore, it is a good practice to seperate the pure functions with the side-effect function.

Try: can you seperate the pure functions with side effect functions for user authentication?

> **Note:** A side effect does not necessarily mean that the function's return value must be different. Printing to the console, writing to a file, modifying global state, or sending data over a network are also side effects even if the function returns the same value.

## Benefits
- reusability and composition
- lazy evaluation
- encapsulation of a behaviour
- improved readibility and maintability
- mitigating bugs
- multi-processing

## Key Concepts
- function as first class citizen
- immutability
- higher-order function
- recursion

Example: 
- sum a list using imperative and functional paradigm.
- filter even number from a list and power each value.

## Further Reading

Example: MapReduce (Google)

![MapReduce Google](https://blogs.cornell.edu/info2040/files/2019/10/mapreduce-768x324.png)

Further reading: [https://blogs.cornell.edu/info2040/2019/10/28/using-mapreduce-to-compute-pagerank/](https://blogs.cornell.edu/info2040/2019/10/28/using-mapreduce-to-compute-pagerank/)

## Group Discussion and Exercise: Python

- Write an abstract function that take a list of numbers and return either only even number or odd numbers! Utilize the abstract function to form a function that return even and odd numbers.
- Write an abstract function that takes a list of strings and a condition function, then returns only the strings that satisfy the given condition. Utilize the abstract function to create functions that: Return strings with more than 5 characters and Return strings that start with a vowel.