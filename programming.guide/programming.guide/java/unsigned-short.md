<span class="underline"></span>

<span class="underline"></span>

Unsigned integers in Java
-------------------------

1.  [Unsigned byte](unsigned-byte.html)
2.  Unsigned short
3.  [Unsigned int](unsigned-int.html)
4.  [Unsigned long](unsigned-long.html)

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

Unsigned short in Java
======================

Java does not have unsigned data types. Your options are:

-   Use a `char`
-   Use an `int`
-   Use a `short` and “manually” interpret the bits unsigned (described below)

Using a `char`
--------------

A `char` variable is meant to store characters (16-bit unicode code points), but can also be used for numerical values between 0 and 65,535.

    char i = 65000;
    char j = 10;
    char sum  = (char) (i + j);  // 65010
    char diff = (char) (i - j);  // 64990
    char prod = (char) (j * j);  // 100
    char quot = (char) (i / j);  // 6500

The casting is required, since a `char` is implicitly widened to an `int` during computations.

As expected, it wrapps around to 0 upon overflow:

    char c = Character.MAX_VALUE;  // 65535
    c++;
    System.out.println((int) c);  // 0

An unsigned `short`
-------------------

A `short` is always signed in Java, but nothing prevents you from viewing a `short` simply as 16 bits and interpret those bits as a value between 0 and 65,535.

<table><thead><tr class="header"><th style="text-align: center;">Java short value</th><th style="text-align: center;">Bits</th><th style="text-align: center;">Interpreted as unsigned</th></tr></thead><tbody><tr class="odd"><td style="text-align: center;">0</td><td style="text-align: center;"><code>0000000000000000</code></td><td style="text-align: center;">0</td></tr><tr class="even"><td style="text-align: center;">1</td><td style="text-align: center;"><code>0000000000000001</code></td><td style="text-align: center;">1</td></tr><tr class="odd"><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td></tr><tr class="even"><td style="text-align: center;">32,767</td><td style="text-align: center;"><code>0111111111111111</code></td><td style="text-align: center;">32,767</td></tr><tr class="odd"><td style="text-align: center;">−32,768</td><td style="text-align: center;"><code>1000000000000000</code></td><td style="text-align: center;">32,768</td></tr><tr class="even"><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td></tr><tr class="odd"><td style="text-align: center;">−2</td><td style="text-align: center;"><code>1111111111111110</code></td><td style="text-align: center;">65,534</td></tr><tr class="even"><td style="text-align: center;">−1</td><td style="text-align: center;"><code>1111111111111111</code></td><td style="text-align: center;">65,535</td></tr></tbody></table>

Keep in mind that there’s nothing you can do to force your interpretation upon someone else’s method. If a method accepts a `short`, then that method accepts a value between −32,768 and 32,767 unless explicitly stated otherwise.

Here are a couple of useful conversions / manipulations.

Printing an unsigned `short`
----------------------------

Use [`Short.toUnsignedInt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#toUnsignedInt-short-) and print the resulting `int`:

    System.out.println("Value of my unsigned short: " + Short.toUnsignedInt(s));

Converting from `int` to unsigned `short`
-----------------------------------------

Casting to `short` throws away all but the lowest 16 bits.

    int i = 65000;        // 00000000 00000000 11111101 11101000
    short s = (short) i;  //                   11111101 11101000

    System.out.println(s);                       // -536
    System.out.println(Short.toUnsignedInt(s));  // 65000

Converting from unsigned `short` to `int`
-----------------------------------------

Use [`Short.toUnsignedInt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#toUnsignedInt-short-) to avoid [sign extension](https://en.wikipedia.org/wiki/Sign_extension).

    short s = (short) (Short.MAX_VALUE + 7233);  // -25536 or 40000

    int signed = s;                         // -25536 (with sign extension)
    int unsigned = Short.toUnsignedInt(s);  //  40000 (without sign extension)

Or, equivalently:

    int unsigned = s & 0xffff;

Parsing an unsigned `short`
---------------------------

    short s = (short) Integer.parseInt("65000");

    System.out.println(Short.toUnsignedInt(s)); // 65000

Comparing unsigned `short`s
---------------------------

Convert to `int` and compare.

    int cmp = Integer.compare(Short.toUnsignedInt(s1), Short.toUnsignedInt(s2));
    // cmp = -1  =>  s1 < s2
    // cmp =  0  =>  s1 = s2
    // cmp =  1  =>  s1 > s2

Arithmetics
-----------

The 2-complement representation “just works” for addition, subtraction and multiplication.

    // two unsigned shorts
    short s1 = (short) 65000;
    short s2 = 100;

    short sum  = (short) (s1 + s2);  // 65100
    short diff = (short) (s1 - s2);  // 64900
    short prod = (short) (s2 * s2);  // 10000

For division and remainder, convert operands to `int`, and then convert the result back to `short`:

    short q = (short) (Short.toUnsignedInt(s1) / Short.toUnsignedInt(s2));
    short r = (short) (Short.toUnsignedInt(s1) % Short.toUnsignedInt(s2));

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
