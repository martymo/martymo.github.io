---
layout: post
title: "My First Impression with Kotlin"
author: "Martym"
categories: learn-kotlin
tags: [kotlin]
---

I have been checking out Kolin for a few weeks. My first impression
with the language is that it works hard to offer rich expressiveness
akin to Ruby and make type safety easier for development.  In no
particular order, I write down the following language features that
interest me and I may add details later.

- Type safety

- Inferred types

- Lazy sequence

- Type definition after variable declaration

- Expressive akin to modern dynamic programming languages

- Tooling, sdkman, gradle

- Packaging

- First class functions

- Code blocks

- Rich LINQ style

Here is a quick comparison example between Kotlin and Ruby for solving
the following quiz:

``` mathematica

X, Y and Z are three non zero digits. Find the X, Y an Z that are XX +
YY + ZZ = XYZ

```

``` kotlin

(111..999).find {
  n -> n == "${n}".map { "${it}".toInt() }
                  .sumBy() { it * 10 + it }
}

```

``` ruby
(111..999).find do |n|
  n == n.to_s.split('')
        .map(&:to_i)
        .sum { |i| i * 10 + i }
end

```
