## Unsigned int operations

1.  Convert unsigned int to long
2.  [Convert long to unsigned int](convert-long-to-unsigned-int.html)
3.  [Print an unsigned int](print-unsigned-int.html)
4.  [Parse an unsigned int](parse-unsigned-int.html)
5.  [Compare unsigned ints](compare-unsigned-ints.html)

## Unsigned integers in Java

1.  [Unsigned byte](unsigned-byte.html)
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

# Convert unsigned int to long in Java

Use [`Integer.toUnsignedLong`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#toUnsignedLong-int-) to avoid [sign extension](https://en.wikipedia.org/wiki/Sign_extension).

    int i = 0b10000011001000010101011000000000;  // -2094967296 or 2200000000

    long signed = i;                             // -2094967296 (with sign extension)
    long unsigned = Integer.toUnsignedLong(i);   //  2200000000 (without sign extension)

Or, equivalently:

    long unsigned = i & 0xffffffffL;

## Comments

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
