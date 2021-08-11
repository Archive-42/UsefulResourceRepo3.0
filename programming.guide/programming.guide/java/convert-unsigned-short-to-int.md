



## Unsigned short operations

1.  Convert unsigned short to int
2.  [Convert unsigned short to long](convert-unsigned-short-to-long.html)
3.  [Convert int to unsigned short](convert-int-to-unsigned-short.html)
4.  [Convert long to unsigned short](convert-long-to-unsigned-short.html)
5.  [Print an unsigned short](print-unsigned-short.html)
6.  [Parse an unsigned short](parse-unsigned-short.html)
7.  [Compare unsigned shorts](compare-unsigned-shorts.html)

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

# Convert unsigned short to int in Java

Use [`Short.toUnsignedInt`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#toUnsignedInt-short-) to avoid [sign extension](https://en.wikipedia.org/wiki/Sign_extension).

    short s = (short) (Short.MAX_VALUE + 7233);  // -25536 or 40000

    int signed = s;                         // -25536 (with sign extension)
    int unsigned = Short.toUnsignedInt(s);  //  40000 (without sign extension)

Or, equivalently:

    int unsigned = s & 0xffff;

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
