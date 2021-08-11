<span class="underline"></span>

<span class="underline"></span>

Related Articles
----------------

[Why's Double.​MIN\_VALUE is positive? Integer.​MIN\_VALUE is negative!](integer-minvalue-negative-double-minvalue-positive.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

Floating Point Values
---------------------

1.  [Bits of a Floating Point Value](../bits-of-a-floating-point-value.html)
2.  [Normal vs Subnormal Floats](../normal-vs-subnormal-floats.html)
3.  [Why is it called Floating Point? And what is Fixed Point?](../why-is-it-called-floating-point-and-what-is-fixed-point.html)

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

Java: Double.MIN\_VALUE vs Double.MIN\_NORMAL
=============================================

[`Double.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#MIN_VALUE) represents the value 2<sup>−1074</sup>. This is a **subnormal** value, and it is the overall smallest possible value that a `double` can represent.

A **subnormal** value has a 0 before the binary point: <span style="white-space: nowrap">0.<span style="font-style: italic">significand bits</span> × 2<sup>exp</sup></span>

[`Double.MIN_NORMAL`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#MIN_NORMAL) represents the value 2<sup>−1022</sup>. This is the smallest possible **normal** value that a `double` can represent.

A **normal** value has a 1 before the binary point: <span style="white-space: nowrap">1.<span style="font-style: italic">significand bits</span> × 2<sup>exp</sup></span>

For details, see full article here: [Normal vs Subnormal Floats](../normal-vs-subnormal-floats.html)

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
