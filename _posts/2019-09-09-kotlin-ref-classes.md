---
layout: post
title: "Kotlin - Classes and Objects"
author: "Martym"
categories: learn-kotlin
tags: [kotlin]
---

When I learn a new programming language, I find an authoritative book,
read it from cover to cover to learn it holistically, and distil the
language's concepts and features into excerpts.

Here are my excerpts for reading the Kotlin reference.

# Classes and Objects

## Classes and Inheritance

### Classes

- `class Invoice { ... }`

- An empty class `class Empty`

- Primary constructor, `class Person(val name: String)`

- The default generated primary constructor is `val invoice = Invoice()`,
  if none is defined and it's `public`

- Use `class DontCreateMe private constructor() {...}` to avoid a public contructor

- Secondary constructors

- Property initializers

- initializer blocks `init() {...}`. There can be multiple blocks and
  they are called in contextual order and interleaved with property
  initializers

- An example

``` kotlin
class Person(val name: String) { // Primary constructor
    val normalizedName = name.toUpperCase() // property initializers

    init {
        // initializer block
        // you can use normalizedName here not, before it appears
    }

    // This is a secondary constructor
    constructor(name: String, parent: Person) : this(name) {
    }
}
```

- Create an instance of a class `val invoice = Invoice()`

### Inheritance

- `Any` is the base class of all classes and it has three methods:
  `equals()`, `hashCode()`, and `toString()`

- Use the `open` modifier to define a super class `open class Base(p:
  Int)`

- Without `open`, a class is said to be a final class

- Use `:` in the class header to inherit from a super class
  `class Derived(p: Int) : Base(p) {}`

- The super class must be initialised before the derived class

- Use `super` to refer the base class in a derived class

- Use `override` to override an `open` method, and both are required
  keywords for overriding

- Use `final` to prevent re-overriding `final override fun draw()`

- [Move this Properties and Fields] Override properties work similarly, both `open` and `override` are
  required

- Overriding `val` with `var` is allowed, but not `var` to `val`. This
  is because under the hood, `var` is to introduce a new `set` method,
  whilst `var` to `val` would result in deleting the `set` method,
  which is not allowed in the language

- `override` can appear in a primary constructor, `class
  Rectangle(override val vertexCount: Int = 4)`

- From an inner class, use `super@Outer` to refer to the super class
  of its outer class

- The compiler will throw errors when methods clash in the inheritance
  hierarchy according to the _overriding rules_

- `abstract`

# Properties and Fields
# Interfaces
# Visibility Modifiers

- `public` is the default
- `private`
- `protected`
- `internal` and modules

# Extensions

- Extension functions

- Extensions are resolved statically

- Member always wins

- Nullable receiver

``` kotlin
fun any?.toString(): String {
    if (this == null) return "null"

    return toString()
}
```

- Most of the time we define extensions on the top level - directly
  under packages. They need to be imported at the call site

# Data Classes

- `data class Point(val x: Int, val y: Int)`

- In the above case, `x` is `component1()` and `y` is `component2()`

- Overriding `copy` is not allowed

# Sealed Classes

``` kotlin
fun eval(expr: Expr): Double = when(expr) {
    is Const -> expr.number
    is Sum -> eval(expr.e1) + eval(expr.e2)
    NotANumber -> Double.NaN
    // the `else` clause is not required because we've covered all the cases
}
```

# Generics
# Nested Classes
# Enum Classes
# Objects

- Use object expressions to create an object of an anonymous class

- Or just an object

``` kotlin
val ahHoc = object {
    var x: Int
    var y: Int
}
```

- If an anonymous object is exposed via a public interface, it loses
  its anonymous class type. It can only be exposed either as one of
  its super types or `Any`

- The code in object expressions can access variables from the
  enclosing scope

- Use object declaration to define a singleton

``` kotlin
object ProviderManager {
    fun register(provider: Provider) {}
}

```

- The singleton can be referred directly,
  `ProviderManager.register(provider)`

- Object declarations can't be local (i.e. be nested directly inside
   a function)

- Object declarations can be nested into other object declarations or
  non-inner classes

- An object declaration inside a class can be marked with the
  `companion` keyword

- Understand this

``` kotlin
interface Factory<T> {
    fun create(): T
}

class MyClass {
    companion object : Factory<MyClass> {
        override fun create(): MyClass = MyClass()
    }
}

val f: Factory<MyClass> = MyClass

```

# Type Aliases

- Use `typealias` to shorten long generic types

- Use `typealias` for inner and nested classes

# Inline Classes
# Delegation
# Delegated Properties
