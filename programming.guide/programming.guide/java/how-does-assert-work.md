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

Java: How does the assert keyword work?
=======================================

By default, an assert statement does nothing at all. However, if you launch your program with the VM option `-enableassertions` (or `-ea` for short):

    $ java -ea com.example.Main

Then this statement

    assert cond;

is equivalent to

    if (!cond)
        throw new AssertionError();

For example, `assert i == 0;` is equivalent to

    if (i != 0)
        throw new AssertionError();

The Java Language Specification states the following:

> **14.10. The `assert` Statement**  
> An assertion is an `assert` statement containing a boolean expression. An assertion is **either enabled or disabled**. If the assertion is enabled, execution of the assertion causes evaluation of the boolean expression and **an error is reported** if the expression evaluates to `false`. If the assertion is disabled, execution of the assertion has no effect whatsoever. <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-14.html#jls-14.10" class="quote-source">JLS §14.10</a>

Where *"enabled or disabled"* is controlled with the `-ea` switch and *"An error is reported"* means that an `AssertionError` is thrown.

Adding an error message
-----------------------

A lesser known feature of `assert` is that you can append an error message. For example:

    assert o != null : "o is null";

The message is passed to the `AssertionError` constructor and is for instance printed along with the stacktrace.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
