<span class="underline"></span>

<span class="underline"></span>

Unsigned integers in Java
-------------------------

1.  [Unsigned byte](unsigned-byte.html)
2.  [Unsigned short](unsigned-short.html)
3.  [Unsigned int](unsigned-int.html)
4.  Unsigned long

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

Unsigned long in Java
=====================

Java does not have unsigned data types. Your options are:

-   Use a [`BigInteger`](https://docs.oracle.com/javase/8/docs/api/java/math/BigInteger.html)
-   Use an [`UnsignedLong`](https://guava.dev/releases/20.0/api/docs/com/google/common/primitives/UnsignedLong.html) from Guava
-   Use a `long` as described below.

An unsigned `long`
------------------

A `long` is always signed in Java, but nothing prevents you from viewing a `long` simply as 64 bits and interpret those bits as a value between 0 and 2<sup>64</sup>.

<table><thead><tr class="header"><th style="text-align: center;">Java long value</th><th style="text-align: center;">Bits</th><th style="text-align: center;">Interpreted as unsigned</th></tr></thead><tbody><tr class="odd"><td style="text-align: center;">0</td><td style="text-align: center;"><code>00000000…00000000</code></td><td style="text-align: center;">0</td></tr><tr class="even"><td style="text-align: center;">1</td><td style="text-align: center;"><code>00000000…00000001</code></td><td style="text-align: center;">1</td></tr><tr class="odd"><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td></tr><tr class="even"><td style="text-align: center;">2<sup>63</sup> − 1</td><td style="text-align: center;"><code>01111111…11111111</code></td><td style="text-align: center;">2<sup>63</sup> − 1</td></tr><tr class="odd"><td style="text-align: center;">−2<sup>63</sup></td><td style="text-align: center;"><code>10000000…00000000</code></td><td style="text-align: center;">2<sup>63</sup></td></tr><tr class="even"><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td></tr><tr class="odd"><td style="text-align: center;">−2</td><td style="text-align: center;"><code>11111111…11111110</code></td><td style="text-align: center;">2<sup>64</sup> − 2</td></tr><tr class="even"><td style="text-align: center;">−1</td><td style="text-align: center;"><code>11111111…11111111</code></td><td style="text-align: center;">2<sup>64</sup> − 1</td></tr></tbody></table>

Keep in mind that there’s nothing you can do to force your interpretation upon someone else’s method. If a method accepts a `long`, then that method accepts a value between −2<sup>63</sup> and <span class="nowrap">2<sup>63</sup> − 1</span> unless explicitly stated otherwise.

Here are a couple of useful conversions / manipulations.

Printing an unsigned `long`
---------------------------

Use [`Long.toUnsignedString`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#toUnsignedString-long-):

    System.out.println("Value of my unsigned long: " + Long.toUnsignedString(i));

Converting from `BigInteger` to unsigned `long`
-----------------------------------------------

`BigInteger.longValue()` throws away all but the lowest 64 bits.

    BigInteger bigInteger = BigInteger.valueOf(Long.MAX_VALUE)
                                      .add(BigInteger.valueOf(24193));
    long lng = bigInteger.longValue();

    System.out.println(Long.toUnsignedString(lng));  // 9223372036854800000

Converting from unsigned `long` to `BigInteger`
-----------------------------------------------

From the [OpenJDK implementation of `Long`](https://github.com/AdoptOpenJDK/openjdk-jdk11/blob/master/src/java.base/share/classes/java/lang/Long.java#L241):

    /**
     * Return a BigInteger equal to the unsigned value of the argument.
     */
    private static BigInteger toUnsignedBigInteger(long i) {
        if (i >= 0L) {
            return BigInteger.valueOf(i);
        } else {
            int upper = (int) (i >>> 32);
            int lower = (int) i;
             // return (upper << 32) + lower
            return BigInteger.valueOf(Integer.toUnsignedLong(upper))
                    .shiftLeft(32)
                    .add(BigInteger.valueOf(Integer.toUnsignedLong(lower)));
        }
    }

Parsing an unsigned `long`
--------------------------

    long lng = Long.parseUnsignedLong("10000000000000000000");

    System.out.println(Long.toUnsignedString(lng)); // 10000000000000000000

**Note:** [`Long.parseLong`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#parseLong-java.lang.String-) would throw a [`NumberFormatException`](https://docs.oracle.com/javase/8/docs/api/java/lang/NumberFormatException.html) for the above input.

Comparing unsigned `long`s
--------------------------

    int cmp = Long.compareUnsigned(l1, l2);
    // cmp = -1  =>  l1 < l2
    // cmp =  0  =>  l1 = l2
    // cmp =  1  =>  l1 > l2

Arithmetics
-----------

The 2-complement representation “just works” for addition, subtraction and multiplication.

    // two unsigned longs
    long l1 = Long.parseUnsignedLong("10000000000000000000");
    long l2 = 999;

    long sum  = l1 + l2;  // 10000000000000000999
    long diff = l1 - l2;  // 9999999999999999001
    long prod = l2 * l2;  // 998001

For division and remainder, use [`Long.divideUnsigned`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#divideUnsigned-long-long-) and [`Long.remainderUnsigned`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#remainderUnsigned-long-long-).

    long q = Long.divideUnsigned(l1, l2);
    long r = Long.remainderUnsigned(l1, l2);

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
