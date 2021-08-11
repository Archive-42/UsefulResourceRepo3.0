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

Java: Wrong results for division?
=================================

When dividing two integers, Java uses **integer division**. In integer division, the result is **truncated** (fractional part thrown away) and **not rounded** to the closest integer. For example: `99 / 10 == 9`.

To get actual floating-point result
-----------------------------------

Cast the numerator (or denominator) to `double`:

    double r = (double) i / j;    // r == 1.66666…

Rounded result
--------------

Cast numerator as above, and use [`Math.round`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#round-double-):

    int r = (int) Math.round((double) i / j);

Why does the above work?
------------------------

`(double) i / j` is parsed as `((double) i) / j`. If one of the operands is a `double`, the other operand is promoted to a `double` as well. Then floating-point division is used, and the result is a floating-point value.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
