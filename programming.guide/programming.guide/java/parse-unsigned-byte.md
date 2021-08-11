



## Unsigned byte operations

1.  [Convert unsigned byte to short](convert-unsigned-byte-to-short.html)
2.  [Convert unsigned byte to int](convert-unsigned-byte-to-int.html)
3.  [Convert unsigned byte to long](convert-unsigned-byte-to-long.html)
4.  [Convert short to unsigned byte](convert-short-to-unsigned-byte.html)
5.  [Convert int to unsigned byte](convert-int-to-unsigned-byte.html)
6.  [Convert long to unsigned byte](convert-long-to-unsigned-byte.html)
7.  [Print an unsigned byte](print-unsigned-byte.html)
8.  Parse an unsigned byte
9.  [Compare unsigned bytes](compare-unsigned-bytes.html)

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

# Parse an unsigned byte in Java

    byte b = (byte) Integer.parseInt("150");

    System.out.println(Byte.toUnsignedInt(b)); // 150

Or, using Guava:

    byte b = UnsignedBytes.parseUnsignedByte("150");

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
