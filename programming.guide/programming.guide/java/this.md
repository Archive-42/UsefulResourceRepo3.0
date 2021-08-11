<span class="underline"></span>

<span class="underline"></span>

Java Keywords
-------------

1.  this
2.  [catch](catch.html)
3.  [finally](finally.html)
4.  [throw](throw.html)
5.  [throws](throws.html)
6.  [try](try.html)

Featured Stack Overflow Post
----------------------------

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)  
  
[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
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

Java Keyword: this
==================

The `this` keyword has **two uses** in a Java program.

1. As a reference to the current object
---------------------------------------

The syntax in this case usually looks something like

    this.someVariable = someVariable;

☞

Continue here: [The 'this' reference (with examples)](this-reference-with-examples.html)

2. To call a different constructor
----------------------------------

The syntax in this case typically looks something like

    MyClass() {
        this(DEFAULT_VALUE); // delegate to other constructor
    }

    MyClass(int value) {
        // ...
    }

☞

Continue here: [this(…) constructor call (with examples)](this-constructor-call-with-examples.html)

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
