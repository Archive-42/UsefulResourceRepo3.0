



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

# -Integer.MIN_VALUE == Integer.MIN_VALUE but -Byte.MIN_VALUE != Byte.MIN_VALUE

Somewhat surprisingly, these two expressions evaluate to true:

    -Integer.MIN_VALUE == Integer.MIN_VALUE   // true
    -Long.MIN_VALUE    == Long.MIN_VALUE      // true

Bytes and shorts however seem to behave as expected:

    -Byte.MIN_VALUE  == Byte.MIN_VALUE    // false
    -Short.MIN_VALUE == Short.MIN_VALUE   // false

What’s going on here?

## Explanation

Java uses two’s complement to represent integer values. In this representation the values are not symmetrical around origo. There's one more negative value than there are positive values. **The smallest value has no positive counterpart!** For example:

- `Integer.MIN_VALUE` equals −2<sup>31</sup>
- `Integer.MAX_VALUE` equals +2<sup>31</sup>−1

When you try to negate −2<sup>31</sup> you get 2<sup>31</sup>, which is larger than the the maximum int value, so it **overflows** and rolls over to the negative side.

Here’s an illustration:

MIN_VALUE 0 MAX_VALUE Overflow! roll over

In other words, `Integer.MIN_VALUE` **is its own negation**. This causes other surprises too, such as `Math.abs(Integer.MIN_VALUE)`, which is implemented as `x < 0 ? -x : x`, to return a negative value.

## What’s up with `byte` and `short`?

Byte and short values are also stored in two’s complement. Java however, does not do arithmetic directly on bytes and shorts. Instead, they are **promoted to `int`s**, and _then_ the unary minus is computed.

If `b` is a byte, then `-b` is equivalent to `-((int) b)`.

One way to illustrate this is to create two overloaded methods…

    void m(byte b) { System.out.println("A byte"); }
    void m(int i)  { System.out.println("An int"); }

…and call them as follows:

    byte b = 0;
    m(b);       // Prints "A byte"
    m(-b);      // Prints "An int"

So `-Byte.MIN_VALUE` equals 128, but in the form of an `int`. If we cast this result back to a `byte` (for which the maximum value is 127) it rolls over and becomes −128, just as in the case of ints and longs:

    (byte) -Byte.MIN_VALUE    == Byte.MIN_VALUE    // true
    (short) -Short.MIN_VALUE  == Short.MIN_VALUE   // true

Here’s an illustration:

ints 0 −128 128 bytes 0 cast promote −128 128 Overflow roll over

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
