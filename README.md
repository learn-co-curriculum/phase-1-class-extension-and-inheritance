# Class Extensions and Inheritance

## Learning Goals

- Use the `extends` keyword
- Use the `super` method
- Explain when `class` inheritance should be used in JavaScript

## Introduction

In JavaScript, as in other Object Oriented languages, we've learned
that you can create `class`es and build methods that can perform
actions on instance data, or specific to the `class`. What if you have
`class`es that exhibit many of the same behaviors, such as `Cat`, `Dog`,
and `Bird`, which all have a method for `speak`? In JavaScript, you can
create "child" object `class`es (constructors) that inherit features
from their "parent" `class`es. In this lesson, we'll discuss 2 ways of
_extending_ functionality to other `class`es.

## Use the `extend` Keyword

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

## Explain When `class` Inheritance Should Be Used in JavaScript

JavaScript can be a bit confusing since it is a dynamic language that uses syntactical
sugar to leverage `class` implementations and inheritance similar to classic programming
languages. However, JavaScript's inheritance model is quite powerful and fairly trivial
to build on top of like when using a classic programming language model. As the popular
phrase goes: "With power comes great responsibility." It can be tempting to overuse these
features. When creating "child" `class`es, we defer to _subtyping_ relation principles
called _(strong) behavioral subtyping_ in programming language theory. 

- You probably won't use inheritance often, but as your code bases get larger, you are more
likely to find a need for it. If you're creating a number of objects that have similar
features, then creating a generic object type to contain all the shared functionality,
and inheriting those features in more specialized objects can be convenient and useful.

- When creating a parent-child `class` relation, it is _semantic_ rather than merely
_syntactic_. Let's use `Vehicle` as a parent `class` with `Car` as a child
`class` of `Vehicle` as an example. In _classical_ inheritance, it creates a _copy_ of the
behavior from parent. However, in JavaScript when we create the object it does not copy the
properties or behavior, it creates a _link_. `class`es should _never_ be extended unless it
is for the sake of compatibility with newer JavaScript features. This is due to the way
inheritance works on top of vanilla JavaScript code.

- When using inheritance, it is advised to not have too many levels of inheritance, and to keep
careful track of where you define your methods and properties. Too much inheritance can lead
to confusion and difficulties trying to debug code.

## Conclusion

In this lesson, we learned about more functionality in JavaScript that allows us to leverage
Object Orientation concepts: `class` extensions and inheritance. With `extends` and `super`
we can create custom `constructor` functions and pass down property and method values.
Understanding inheritance in JavaScript compared to classic programming languages will help
avoid unnecessary code complexity or performance issues.

## Resources

* [Inheritance in JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)
* [Extends](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends)
* [“Super” and “Extends” In JavaScript ES6 - Understanding The Tough Parts](https://medium.com/beginners-guide-to-mobile-web-development/super-and-extends-in-javascript-es6-understanding-the-tough-parts-6120372d3420)
* [Class inheritance, super](https://javascript.info/class-inheritance)
* [Liskov substitution principle] (https://en.wikipedia.org/wiki/Liskov_substitution_principle)
* [Subtyping (programming language theory)](https://en.wikipedia.org/wiki/Subtyping)
* [Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* [JavaScript — Inheritance, delegation patterns and Object linking](https://codeburst.io/javascript-inheritance-25fe61ab9f85)
* [Understanding Prototypes and Inheritance in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-prototypes-and-inheritance-in-javascript)