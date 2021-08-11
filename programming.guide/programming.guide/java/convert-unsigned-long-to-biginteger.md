



## Unsigned long operations

1.  Convert unsigned long to BigInteger
2.  [Convert BigInteger to unsigned long](convert-biginteger-to-unsigned-long.html)
3.  [Print an unsigned long](print-unsigned-long.html)
4.  [Parse an unsigned long](parse-unsigned-long.html)
5.  [Compare unsigned longs](compare-unsigned-longs.html)

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

# Convert unsigned long to BigInteger in Java

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

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
