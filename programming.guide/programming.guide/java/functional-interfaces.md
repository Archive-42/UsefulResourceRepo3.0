<span class="underline"></span>

<span class="underline"></span>

Featured Stack Overflow Post
----------------------------

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)  
  
[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  Functional Interfaces
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Java: Functional Interfaces
===========================

Functional interfaces are interfaces with a single method. This is a functional interface:

    interface MyInterface {
        void method();
    }

With lambdas
------------

The above interface can be used as follows:

    MyInterface o = () -> System.out.println("Hello World");
    o.method();

Or, if a `someMethod` accepts a `MyInterface` as argument, you can provide a lambda directly:

    someMethod(() -> System.out.println("Hello World"));

With method references
----------------------

Similarly, you can use method references. Given this class

    class Example {
        static void sayHello() {
            System.out.println("Hello World");
        }
    }

You can do

    MyInterface o = Example::sayHello;

or

    someMethod(Example::sayHello);

For more examples, including use of instance methods and constructor references, see the [Lambda Cheat Sheet](lambda-cheat-sheet.html).

Standard Functional Interfaces
------------------------------

A complete list of the functional interfaces provided by the Java API can be found here: [Lambda Cheat Sheet](lambda-cheat-sheet.html).

Default Methods
---------------

Apart from a single abstract method, a functional interface can have additional `default` methods. This for example, is still a functional interface:

    interface MyInterface {
        void method();

        default void methodX2() {
            method();
            method();
        }
    }

`@FunctionalInterface` annotation
---------------------------------

If you want to make sure you're not accidentally turning a functional interface into a non-functional interface, you can make your intention explicit by adding [`@FunctionalInterface`](https://docs.oracle.com/javase/8/docs/api/java/lang/FunctionalInterface.html). If you mess up, like below…

    @FunctionalInterface
    interface MyInterface {
        void method1();
        void method2(); // Can't have more than one abstract method!
    }

…the compiler will give the following error:

    MyInterface.java:1: error: Unexpected @FunctionalInterface annotation
    @FunctionalInterface
    ^
      MyInterface is not a functional interface
    1 error

Further Reading
---------------

-   [Javadoc for `@FunctionalInterface`](https://docs.oracle.com/javase/8/docs/api/java/lang/FunctionalInterface.html)
-   [Java Language Specification: 9.8 Functional Interfaces](https://docs.oracle.com/javase/specs/jls/se8/html/jls-9.html#jls-9.8)

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
