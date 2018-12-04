# Class Extensions and Inheritance

## Learning Goals

- Use the `extends` keyword
- Use the `super` method
- Explain when `class` inheritance should be used in JavaScript

## Introduction

(KG: i love that you're playing by the rules, but don't over-generalize: use ``
for code-words `class` is what you type...versus "classes exist in OO
languages")

In JavaScript, as in other Object Oriented languages, we've learned that you
can create classes and build methods that can perform actions on instance data,
or specific to the class.

What if you have several classes that exhibit many of the same behaviors, such
as `Cat`, `Dog`, and `Bird`, all of which have a method for `speak`? In
JavaScript, you can create "child" classes that inherit methods from their
"parent" classes.

In this lesson, we'll discuss 2 ways of _extending_ functionality from a
"parent" class to another "child" `class`es.

## Use the `extend` Keyword

To get started with inheriting functionality, we utilize the `extends`
keyword. `extends` is used in `class` declarations to create a class which
is a _child_ of another class.

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

( KG: Code like this needs a post-game explanation of what it is doing.)

In our code, we have 2 `class`es: `Pet` and `Dog`. The `Dog` class is a
_subclass_ or _child_ `class` of `Pet` and it uses the `extends` keyword to
inherit methods (in this case the `constructor`) from the parent `class`.
Because the child (`Dog`) class extends the parent (`Pet`), `Dog`'s constructor
is `Pet`'s constructor.

## Use the `super` Method

(KG: I think this is overloaded, too big. Maybe we can turn this Readme into 3
smaller readmes labs (still using the Pet and Dog and Bird domain) but discuss and
then test the following

* Child gets something from parent
* Child overrides something from parent
* Child adds onto something from parent

For the student using super is 'who cares' learning to type less / share
behavior is a 'whoa!' moment)


With `super`, we can inherit
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

People new to Object oriented languages tend to go off the deep end when they
first see the glory of inheritance: Animals extend MulticellularLife which
extends Matter. Whoa! Settle down. A good rule of thumb is to never have
inheritance hierarchies with more than 2, _maybe_ 3 levels.

> **MASTER TIP**: Always start with the simplest solution and progress to more
> complex solutions only as-needed.

(cut to Prototypal OO topic later)

(cut to an OO  best practices? topic to be added later, Max?)

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
* [Object prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)
* [Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* [JavaScript — Inheritance, delegation patterns and Object linking](https://codeburst.io/javascript-inheritance-25fe61ab9f85)
* [Javascript ‘Classes’ and Prototypal Inheritance](https://medium.com/code-monkey/javascript-classes-and-prototypal-inheritance-2a53ed7343d8)
* [Understanding Prototypes and Inheritance in JavaScript](https://www.digitalocean.com/community/tutorials/understanding-prototypes-and-inheritance-in-javascript)
* [Master the JavaScript Interview: What’s the Difference Between Class & Prototypal Inheritance](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9)
* [Why Composition is Harder with Classes](https://medium.com/javascript-scene/why-composition-is-harder-with-classes-c3e627dcd0aa)
