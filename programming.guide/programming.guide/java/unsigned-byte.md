



## Unsigned integers in Java

1.  Unsigned byte
2.  [Unsigned short](unsigned-short.html)
3.  [Unsigned int](unsigned-int.html)
4.  [Unsigned long](unsigned-long.html)

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

# Unsigned byte in Java

Java does not have unsigned data types. Your options are:

- Use a wider datatype such as `short`, `char` or `int`
- Use a `byte` and “manually” interpret it as unsigned (described below)

## An unsigned `byte`

A `byte` is always signed in Java, but nothing prevents you from viewing a `byte` simply as 8 bits and interpret those bits as a value between 0 and 255.

<span class="caption">Java‘s interpretation vs. your interpretation.</span>

<table><thead><tr class="header"><th style="text-align: center;">Java byte value</th><th style="text-align: center;">Bits</th><th style="text-align: center;">Interpreted as unsigned</th></tr></thead><tbody><tr class="odd"><td style="text-align: center;">0</td><td style="text-align: center;"><code>00000000</code></td><td style="text-align: center;">0</td></tr><tr class="even"><td style="text-align: center;">1</td><td style="text-align: center;"><code>00000001</code></td><td style="text-align: center;">1</td></tr><tr class="odd"><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td></tr><tr class="even"><td style="text-align: center;">127</td><td style="text-align: center;"><code>01111111</code></td><td style="text-align: center;">127</td></tr><tr class="odd"><td style="text-align: center;">−128</td><td style="text-align: center;"><code>10000000</code></td><td style="text-align: center;">128</td></tr><tr class="even"><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td><td style="text-align: center;">⋮</td></tr><tr class="odd"><td style="text-align: center;">−2</td><td style="text-align: center;"><code>11111110</code></td><td style="text-align: center;">254</td></tr><tr class="even"><td style="text-align: center;">−1</td><td style="text-align: center;"><code>11111111</code></td><td style="text-align: center;">255</td></tr></tbody></table>

Keep in mind that there’s nothing you can do to force your interpretation upon someone else’s method. If a method accepts a `byte`, then that method accepts a value between −128 and 127 unless explicitly stated otherwise.

Here are a couple of useful conversions / manipulations.

## Printing an unsigned `byte`

Use [`Byte.toUnsignedInt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#toUnsignedInt-byte-) and print the resulting `int`:

    byte b = (byte) 0b10010110; // -106 signed, or 150 unsigned

    System.out.println("Value of my unsigned byte: " + Byte.toUnsignedInt(b));  // 150

## Converting from `int` to unsigned `byte`

Casting to `byte` throws away all but the lowest 8 bits.

    int i = 150;        // 00000000 00000000 00000000 10010110
    byte b = (byte) i;  //                            10010110

    System.out.println(b);                      // -106
    System.out.println(Byte.toUnsignedInt(b));  //  150

## Converting from unsigned `byte` to `int`

Use [`Byte.toUnsignedInt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#toUnsignedInt-byte-) to avoid [sign extension](https://en.wikipedia.org/wiki/Sign_extension).

    byte b = (byte) 0b10010110;           // -106 or 150

    int signed = b;                       // -106 (with sign extension)
    int unsigned = Byte.toUnsignedInt(b); //  150 (without sign extension)

Or, equivalently:

    int unsigned = b & 0xff;

## Parsing an unsigned `byte`

    byte b = (byte) Integer.parseInt("150");

    System.out.println(Byte.toUnsignedInt(b)); // 150

Or, using Guava:

    byte b = UnsignedBytes.parseUnsignedByte("150");

## Compare unsigned `byte`s

Convert to `int` and compare.

    int cmp = Integer.compare(Byte.toUnsignedInt(b1), Byte.toUnsignedInt(b2))
    // cmp = -1  =>  b1 < b2
    // cmp =  0  =>  b1 = b2
    // cmp =  1  =>  b1 > b2

Or, using Guava

    int cmp = UnsignedBytes.compare(b1, b2);

## Arithmetics

The 2-complement representation “just works” for addition, subtraction and multiplication.

    // two unsigned bytes
    byte b1 = (byte) 200;
    byte b2 = (byte) 15;

    byte sum  = (byte) (b1 + b2);  // 215
    byte diff = (byte) (b1 - b2);  // 185
    byte prod = (byte) (b2 * b2);  // 225

Division requires conversion of operands, and then convertion of result back to `byte`.

    byte ratio = (byte) (Byte.toUnsignedInt(b1) / Byte.toUnsignedInt(b2));

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
