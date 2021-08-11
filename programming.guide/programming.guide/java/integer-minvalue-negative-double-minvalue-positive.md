<span class="underline"></span>

<span class="underline"></span>

## Related Articles

[Double.MIN_VALUE vs Double.MIN_NORMAL](double-min-value-vs-double-min-normal.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Floating Point Values

1.  [Bits of a Floating Point Value](../bits-of-a-floating-point-value.html)
2.  [Normal vs Subnormal Floats](../normal-vs-subnormal-floats.html)
3.  [Why is it called Floating Point? And what is Fixed Point?](../why-is-it-called-floating-point-and-what-is-fixed-point.html)

<span class="underline"></span>

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

# Java: Why's Double.MIN_VALUE is positive? Integer.MIN_VALUE is negative!

Curiously, `Double.MIN_VALUE` holds the value 2<sup>-1074</sup>. This is a positive value, as opposed to `Integer.MIN_VALUE` which holds the negative value -2147483648.

The reason is most likely that the smallest double value is easily expressed as `-Double.MAX_VALUE`. The IEEE 754 format has one bit reserved for the sign and the remaining bits representing the magnitude. This means that it is symmetrical around origo (as opposed int values, which have one more negative value).

## So what's up with 2<sup>-1074</sup>?

This value is the smallest value greater than 0 that the IEEE 754 allows you to express. So `Double.MIN_VALUE` (and `Double.MAX_VALUE`) should be thought of as the minimum (and maximum) positive magnitudes.

Finally, the same constant is called [`Double.EPSILON`](https://msdn.microsoft.com/en-us/library/system.double.epsilon.aspx) in .NET, which is arguably a better name.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
