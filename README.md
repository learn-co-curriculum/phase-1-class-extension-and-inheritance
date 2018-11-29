# Class Extensions and Inheritance

## Learning Goals

- Use the `extends` keyword
- Use the `super` method

## Introduction

In JavaScript, as in other Object Oriented languages, we've learned
that you can create `class`es and build methods that can perform
actions on instance data, or specific to the `class`. What if you have
`class`es that exhibit many of the same behaviors, such as `Cat`, `Dog`,
and `Bird`, which all have a method for `speak`? In JavaScript, you can
create "child" object `class`es (constructors) that inherit features
from their "parent" `class`es. In this lesson, we'll discuss 2 ways of
_extending_ functionality to other `class`es.

## Use the `extend` Keword

To get started with inheriting `class` functionality, we utilize a method
called `extends`. The `extends` keyword is used in `class` declarations to
create a `class` which is a _child_ of another `class`. 


```js
class Pet {
  constructor(name) {
    this.name = name;
  }
}

// Inherits from Pet
class Dog extends Pet {
  speak() {
    return `${this.name} says woof!`
  }
}

let dog = new Dog("Shadow");

dog.speak(); // Shadow says woof!
```

## Use the `super` Method

In our code, we have 2 JavaScript `class`es: `Pet` and `Dog`. The `Dog` class
is a _subclass_ or _child_ `class` of `Pet` and it uses the `extends` keyword
to inherit methods from the parent `class`. With `super`, we can inherit
functionality from the parent `class` in two different ways:

```js
class Pet {
  constructor(name) {
    this.name = name;
  }

  speak() {
    return `${this.name} speaks!`
  }
}

// Inherits from Pet
class Dog extends Pet {
  constructor(name) {
    super(name)
  }
  speak() {
    return `${super.speak()} ${this.name} says woof!`;
  }
}

let dog = new Dog("Spot");

dog.speak(); // Spot speaks! Spot says woof!
```
In `Dog`s `constructor`, `super` is used as a `method`. Whereas, `Dog`'s `speak()`
method used `super` as an `object`. When the `super` keyword is used as method, it
calls the parent `class` `Pet` with the parameters passed to `Dog`. This is to ensure
that `Dog` is an instance of `Pet`. When `super` is used as an `object` that refers to
a `Pet` instance, it can calls methods of the parent `class` `Pet` explicitly.

## Conclusion

## Resources
