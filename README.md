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
create "child" object `class`es that inherit features from their "parent"
`class`es. In this lesson, we'll discuss 2 ways of _extending_ functionality
to other `class`es.

## Use the `extend` Keyword

To get started with inheriting `class` functionality, we utilize the `extends`
keyword. `extends` is used in `class` declarations to create a `class` which
is a _child_ of another `class`. 

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
method used `super` as an `object`. When the `super` keyword is used as a method, it
calls the parent `class` `Pet` with the parameters passed to `Dog`. This is to ensure
that `Dog` is an instance of `Pet`. When `super` is used as an `object` that refers to
a `Pet` instance, it can call methods of the parent `class` `Pet` explicitly.

## Explain When `class` Inheritance Should Be Used in JavaScript

You probably won't use inheritance often, but as your code bases get larger, you are more
likely to find a need for it. If you're creating a number of objects that have similar
features, then creating a generic object type to contain all the shared functionality,
and inheriting those features in more specialized objects can be convenient and useful.

JavaScript can be a bit confusing since it is a dynamic language that uses syntactic
sugar to leverage `class` implementations and inheritance similar to classic programming
languages. However, JavaScript's inheritance model is quite powerful and fairly trivial
to build on top of like when using a classic programming language model. As the popular
phrase goes: "With power comes great responsibility." It can be tempting to overuse these
features.

When creating child `class`es, we defer to _subtyping_ relation principles
called _(strong) behavioral subtyping_ in programming language theory. A parent-child 
`class` relation is _semantic_ rather than merely _syntactic_. Let's use `Vehicle` as
a parent `class` with `Car` as a child `class` of `Vehicle` as an example. 

In _classical_ inheritance, it creates a _copy_ of the behavior from parent. However, in
JavaScript when we create the object it does not copy the properties or behavior, it creates
a _link_. This is called _prototypal_ inheritance. Copies of `class`es become separate entities,
no longer directly associated with the parent.

> Every object in JavaScript has an internal property called `prototype`. `prototype`s are what
allows JavaScript objects to inherit features from one another. This is often referred to as a
_prototype chain_. Methods and properties are not copied from one object to another in the
prototype chain--they are accessed by _walking up_ the chain.

While on the surface may look like it does the same thing, `class`es that are _linked_ and *not*
_copied_ are fundamentally a code reuse mechanism--a way for objects to share code. The way that
the code is shared matters. `Car`looks to the parent as a reference, and does not
have all `Vehicle`'s properties and behaviors without it. When you attempt to access a property
or method of an object, JavaScript will continue searching through the object/`class` and its
`prototype` until the end of the `prototype` chain is reached. It can create performance and
code maintenance issues when misapplied.

```js
class Vehicle { // Parent class
  constructor(name) {
    this.name = name;
  }

  start() { // Parent class method
    return "Engine of "+this.name + " starting...";
  };
}

class Car extends Vehicle { // Child class
 constructor(name) {
    super(name);
  }

  run() { // Child class method
    return `Hello! ${super.speak()} It has 4 Cylinders.`; // Calling on a method inherited from parent class
  }
}

let car1 = new Car("Camry");
let car2 = new Car("Civic");

// Accessing the child class method which accesses the parent's method
car1.run();   // "Hello! Engine of Camry starting... It has 4 Cylinders."
car2.run();   // "Hello! Engine of Civic starting... It has 4 Cylinders."
```

It it advised that `class`es should _never_ be extended unless it is for the sake of compatibility
with newer JavaScript features, like in building UI components frameworks like React and Angular.
This is due to the way inheritance works on top of vanilla JavaScript code, and could create
a multitude of unforseen headaches down the road. Always start with the simplest solution
and progress to more complex solutions only as-needed.

If you do choose to use inheritance, it is advised to not have too many levels of inheritance, and
to keep careful track of where you define your methods and properties. Too much inheritance can
lead to confusion and difficulties when trying to debug code.

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
* [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)
* [Subtyping (programming language theory)](https://en.wikipedia.org/wiki/Subtyping)
* [Object prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)
* [Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* [JavaScript — Inheritance, delegation patterns and Object linking](https://codeburst.io/javascript-inheritance-25fe61ab9f85)
* [Understanding Prototypes and Inheritance in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-prototypes-and-inheritance-in-javascript)
* [Master the JavaScript Interview: What’s the Difference Between Class & Prototypal Inheritance](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9)
* [Why Composition is Harder with Classes](https://medium.com/javascript-scene/why-composition-is-harder-with-classes-c3e627dcd0aa)