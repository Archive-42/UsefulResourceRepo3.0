



## Uses of super in Java

1.  [Calling super()](super-call.html)
2.  Calling super.someMethod()
3.  [Calling super method of outer class from inner class](calling-super-method-of-outer-class-from-inner-class.html)
4.  [Calling a default interface method from implementing class](calling-default-interface-method-implementation-from-implementing-class.html)

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)



## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

# Java: Calling super.someMethod()

`super.someMethod()` calls `someMethod` of the base class. It is often used in an overriding method.

Here's an example:

dog.beHappy(); class Dog extends Animal { void beHappy() { super .beHappy(); print("Wag tail"); } } class Animal { void beHappy() { print("Smile"); } }

You can of course call `super.someMethod()` anywhere from the subclass. This will "bypass" any overridden version of the method.

You can **not** reach in to the base class of the base class by doing `super.super.someMethod()`.

???

Not to be confused with

- `super()`, see [Calling super()](super-call.html), or
- `SomeClass.super.someMethod()`, see [Calling super method of outer class from inner class](calling-super-method-of-outer-class-from-inner-class.html)

## Comments



?? 2016???2021 Programming.Guide, [Terms??and??Conditions](../terms-and-conditions.html)
