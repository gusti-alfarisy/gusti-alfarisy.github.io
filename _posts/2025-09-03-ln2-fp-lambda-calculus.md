---
title: "Lecture Notes 2: Introduction to Lambda Calculus"
date: 2025-09-03
last_modified_at: 2026-08-25
background: "https://www-codecademy-com.translate.goog/resources/blog/wp-content/uploads/2022/12/programming-languages.png"
comments: true
toc: true
---

A Turing machine is a computational model based on states. The machine reads the current state and, using its transition function (the instruction table), updates the state, optionally writes to the tape, and moves the tape head left or right. This model captures the essence of program execution.

Lambda calculus, introduced by Alonzo Church (1930), is another universal model of computation, equivalent in power to the Turing machine. It predates Turing's formulation and models computation using only functions, variable bindings, and substitution. Intersetingly, any code written for turing machine is equivalent to lambda calculus.

Lambda calculus is an important theoretical foundation for many functional-programming ideas used in languages such as Haskell and Lisp, and it influences concepts like iterators and higher-order functions in other languages.

## The Syntax

* variable: x, y, z
* abstraction: $$\lambda x. M$$ which is a function with a body M
* application: (M N), function M applied to argument N

Example:

$$
f(x) = x + 10
$$

$$
\lambda x. x+10
$$

Identity function

$$
\lambda x. x
$$

Example of lambda expressions in various programming languages (JavaScript, Python, and Rust):

JS:
```javascript
const add10 = x => x + 10;
console.log(add10(5)); // 15
```

Python:
```python
add10 = lambda x: x + 10
print(add10(5))  # 15
```

Rust:
```rust
let add10 = |x: i32| x + 10;
println!("{}", add10(5)); // 15
```

## Beta-reduction ($$\beta-reduction$$)

Beta-reduction is the operation that applies a function (an abstraction) to an argument. For example:

$$
(\lambda x. x + 10)\; 5
$$

We substitute `5` for `x` in the body:

$$
(x + 10)[x := 5]
$$

Which evaluates to

$$
5 + 10 = 15
$$

## Alpha-conversion ($$\alpha-conversion$$)

Alpha-conversion is the renaming of bound variables to avoid name-capture with free variables. Example of a potential name clash:

$$
(\lambda x. \lambda y. x)\; y
$$

Renaming the inner bound `y` to `z` avoids confusion:

$$
(\lambda x. \lambda z. x)\; y
$$


## Eta-Reduction ($$\eta$$-reduction)

Eta-reduction expresses the idea that a function which does nothing more than pass its argument to another function can be simplified to that function itself.

Formally,

$$
\lambda x.\; f\,x \;\xrightarrow{\eta}\; f
\qquad \text{if } x \notin FV(f)
$$

where $$FV(f)$$ denotes the set of **free variables** occurring in $$f$$.

For example,

$$
\lambda x.\; g\,x
\;\xrightarrow{\eta}\;
g
$$

The expression

$$
\lambda x.\; g\,x
$$

takes an argument $$x$$ and immediately passes it to $$g$$. It therefore has the same functional behavior as $$g$$ itself.

Eta-reduction is valid only when

$$
x \notin FV(f).
$$

This means that $$f$$ must not depend on the particular variable $$x$$ being removed.

For example,

$$
\lambda x.\; x\,x
$$

cannot be eta-reduced to

$$
x
$$

because in this case the first $$x$$ is part of the function being applied, and therefore $$x$$ occurs free in the corresponding $$f$$.

### Eta-Expansion

The inverse transformation is called **eta-expansion**:

$$
f
\;\xrightarrow{\eta^{-1}}\;
\lambda x.\; f\,x
\qquad \text{if } x \notin FV(f).
$$

Eta-expansion makes the argument of a function explicit without changing its functional behavior.

Therefore,

$$
f
\;\equiv_{\eta}\;
\lambda x.\;f\,x.
$$

### Intuition

Eta-reduction can be understood as:

> **Remove an unnecessary wrapper around a function.**

For example,

$$
\lambda x.\; \text{square}\;x
\;\xrightarrow{\eta}\;
\text{square}.
$$

Both expressions describe a function that receives an argument and applies `square` to it. The lambda abstraction adds no additional computation.


## Currying

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

## Defining TRUE and FALSE

In lambda calculus we encode booleans as functions that select one of two arguments:

$$
TRUE := \lambda x. \lambda y. x
$$

$$
FALSE := \lambda x. \lambda y. y
$$

Using these encodings we can define `NOT` as:

$$
NOT := \lambda b. b\; FALSE\; TRUE
$$

Evaluate `NOT TRUE`:

$$
NOT\; TRUE = (\lambda b. b\; FALSE\; TRUE)\; TRUE \to TRUE\; FALSE\; TRUE \to FALSE
$$

And `NOT FALSE`:

$$
NOT\; FALSE = (\lambda b. b\; FALSE\; TRUE)\; FALSE \to FALSE\; FALSE\; TRUE \to TRUE
$$

## AND operator

The encoding of `AND` is:

$$
AND := \lambda p. \lambda q. p\; q\; FALSE
$$

Check `AND TRUE FALSE`:

$$
AND\; TRUE\; FALSE = (\lambda p. \lambda q. p\; q\; FALSE)\; TRUE\; FALSE
	\to (\lambda q. TRUE\; q\; FALSE)\; FALSE \to TRUE\; FALSE\; FALSE \to FALSE
$$

`AND TRUE TRUE` reduces to `TRUE`, and `AND FALSE _` reduces to `FALSE`.

## Exercise

Try to create lambda expressions for `OR` and `XOR`. Remember, how you can get derive the lambda expression is much more important than the expression itself!