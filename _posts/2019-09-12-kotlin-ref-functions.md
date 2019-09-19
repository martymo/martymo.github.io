---
layout: post
title: "Kotlin - Functions and Lambdas"
author: "Martym"
categories: learn-kotlin
tags: [kotlin]
---

# Functions and Lambdas

## Functions

- `fun double(x: Int = 0): Int { return 2 * x }`, where `x` is a
  parameter and its default argument is 0

- Single-expression functions, `fun double(x: Int) = x * 2`

- The overriding `fun` use the default arguments and cannot override
  default arguments

- Named arguments (what a lifesaver!) and positional arguments work
  similar to Python

- `lambda` has to be the last argument if exists

- `vararg` and `spread` operation `*`

``` kotlin
fun foo(vararg strings: String) { /*...*/ }

foo(strings = *arrayOf("a", "b", "c"))
```

- Infix notion, calling a `func` without the dot and parentheses if
  the `fun` is a member function or extension function, a single
  parameter, not `vararg`, and no default value

- Infix function calls have lower precedence than the arithmetic, type
  casts, and the RangeTo operator. And use parentheses!

- Functions can be declared at the top level

- Functions support closure

- Generic functions `fun <T> foo(item: T): List<T> { /*...*/  }`

- `tailrec` optimises out tail recursions

## Lambdas

- First-class functions, meaning functions can be stored in variables
  and data structures

- A higher-Order function is a function that takes functions as
  parameters, or returns a function

- Function types (`->`), e.g. `(R, T) -> R`

## Inline Functions
