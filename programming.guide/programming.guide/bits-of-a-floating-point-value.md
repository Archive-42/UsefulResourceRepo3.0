



## Floating Point Values

1.  Bits of a Floating Point Value
2.  [Normal vs Subnormal Floats](normal-vs-subnormal-floats.html)
3.  [Why is it called Floating Point? And what is Fixed Point?](why-is-it-called-floating-point-and-what-is-fixed-point.html)

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

# Bits of a Floating Point Value

The IEEE 754 representation of a floating point value:

Single Precision

Single Precision bit representation

31 1 bit sign 60 23 8 bits exponent 22 0 23 bits significand

Double Precision

Double Precision bit representation

63 1 bit sign 62 52 11 bits exponent 51 0 52 bits significand

- <span style="color: #22e">Sign bit</span> is 0 for positive and 1 for negative.
- <span style="color: #e22">The exponent</span> is stored with an offset. +127 for single precision and +1023 for double precision.
- <span style="color: #0c0">The significand</span> implicitly starts with a 1 followed by the binary point.

The value represented is:

<span style="color: #22e">±</span> <span style="color: #999">1.</span><span style="color: #0c0">significand</span> <span style="color: #999">× 2</span><sup>exponent</sup>

**Example:** Decoding a single precision float:

0 1 0 0 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1. 1 1 0 0 0 0 0 1 0 1 means negative convert to base 10 add implicit 1. 130 adjust offset, −127 3 − × 2 3 = −1010.01 convert to base 10 −10.25

## Special Cases

- If all the exponent bits are zero, then −126 (or −1023 for a double) is the actual exponent, and the implicit leading bit of the significand is 0 (instead of 1). See [Normal vs Subnormal Floats](normal-vs-subnormal-floats.html).

- If all the exponent bits are ones, then the value is infinity (if all the significand bits are zero) and NaN (if any significand bit is one).

- The sign of a zero value is ignored by all comparison operations (but may still have significance in other situations).

- For NaN the sign bit is always ignored.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
