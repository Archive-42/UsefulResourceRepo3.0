<span class="underline"></span>

<span class="underline"></span>

Floating Point Values
---------------------

1.  [Bits of a Floating Point Value](bits-of-a-floating-point-value.html)
2.  Normal vs Subnormal Floats
3.  [Why is it called Floating Point? And what is Fixed Point?](why-is-it-called-floating-point-and-what-is-fixed-point.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

Normal vs Subnormal Floats
==========================

-   A **normal** value has a 1 before the binary point: <span style="white-space: nowrap">1.<span style="font-style: italic">significand bits</span> × 2<sup>exp</sup></span>
-   A **subnormal** value has a 0 before the binary point: <span style="white-space: nowrap">0.<span style="font-style: italic">significand bits</span> × 2<sup>exp</sup></span>

What does this mean?
--------------------

Computers store floating point values similar to how we write numbers in **scientific notation**:

1.2325 × 10<sup>2</sup>

Or, as computers prefer it, in base 2:

1.11101101 × 2<sup>110</sup>

See [Bits of a Floating Point Value](bits-of-a-floating-point-value.html) for details.

The exponent (2 and 110 in the decimal and binary examples above) are not chosen arbitrarily. They are chosen so that there is **precisely one non-zero digit** in front of the decimal (or binary) point. This is called the **normal form**.

Leading bit is implicit
-----------------------

Since 1 is the only non-zero digit in binary, values will normally (pun intended) start with 1 followed by a binary point. This is taken advantage of in the IEEE 754 format: The leading bit is implicit, i.e. only the bits after the binary point are stored explicitly.

Smallest normal value
---------------------

While keeping the initial bit implicit saves one bit, it means that the **smallest normal value** is

1.

00000000000000000000000

explicitly stored  
significand bits

 × 2

<sup>−126</sup>

smallest exponent

This is for single precision (`float`) values where the exponent is 8 bits. For double precision (`double`) values the exponent has 11 bits.

Smallest subnormal value
------------------------

To allow for even smaller values, IEEE 754 specifies that if all exponent bits are zero, the implicit leading bit is 0. This means that the **smallest subnormal non-zero value** is

0.

00000000000000000000001

explicitly stored  
significand bits

 × 2

<sup>−126</sup>

smallest exponent

Precision
---------

Subnormal numbers give up significant digits in order to push the first non-zero digit away from the decimal point. Normal values always have 24 bits of significant digits (53 for doubles), while in the (extreme) example above, there's only 1 significant digit. In other words, beware of the loss of precision when dealing with subnormal values.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
