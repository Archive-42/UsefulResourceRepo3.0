



## Uses of super in Java

1.  Calling super()
2.  [Calling super.someMethod()](super-method-call.html)
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

# Java: Calling super()

`super()` calls the constructor of the base class.

... new Dog(); class Dog extends Animal { Dog() { super (); } } class Animal { Animal() { } }

☞

Not to be confused with `super.someMethod()`. See [Calling super.someMethod()](super-method-call.html).

## Another Example

Here's an expanded version with **printouts** and **constructor arguments**.

    class Animal {
        public Animal(String arg) {
            System.out.println("Constructing an animal: " + arg);
        }
    }

    class Dog extends Animal {
        public Dog() {
            super("From Dog constructor");
            System.out.println("Constructing a dog.");
        }
    }

    public class Test {
        public static void main(String[] a) {
            new Dog();
        }
    }

Prints the following:

    Constructing an animal: From Dog constructor
    Constructing a dog.

## The Fine Print

- The call to `super()` must be **the first** statement in the constructor.
- If you give arguments to `super("hello", 5)`, it will invoke the base constructor that accepts a `String` and an `int`.
- `super()` without arguments calls the base class' no-arg constructor. Such constructor only exists if A) you have not defined any constructor, or B) you have explicitly defined a no-arg constructor. If neither of these are true, then `super()` will fail with a compile error.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
