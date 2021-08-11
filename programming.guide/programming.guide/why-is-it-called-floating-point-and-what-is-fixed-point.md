



## Floating Point Values

1.  [Bits of a Floating Point Value](bits-of-a-floating-point-value.html)
2.  [Normal vs Subnormal Floats](normal-vs-subnormal-floats.html)
3.  Why is it called Floating Point? And what is Fixed Point?

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)



## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Why is it called Floating Point? And what is Fixed Point?

In a floating point value, the radix point "floats around". The value is determined by the significand, and the position of the radix point is determined by the exponent:

sign

0

exponent

significand

This way extremely small and extremely large values can be represented, without sacrificing any significant digits. Put differently: One does not have to include lots of leading or trailing zeroes to indicate the magnitude.

## Fixed Point Representation

In some applications the floating point representation is not suitable. For example, some architectures do not have hardware support for floating point arithmetics. In these situations, it's common to use fixed-point arithmetic. A fixed-point value is essentially an integer scaled by an implicit constant factor.

Here's a fixed-point value with scale 10<sup>−6</sup>.

integer bits



.

fractional bits

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
