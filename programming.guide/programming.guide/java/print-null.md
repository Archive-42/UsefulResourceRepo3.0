<span class="underline"></span>

<span class="underline"></span>

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

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

# Java: Print null

What happens if you try to print a null pointer in Java? It depends.

The following line will not compile:

    System.out.println(null);

This is the message from my compiler:

    reference to println is ambiguous, both
    method println(char[]) in java.io.PrintStream and
    method println(java.lang.String) in java.io.PrintStream match

In fact, `println(java.lang.Object)` in `java.io.PrintStream` is yet another match, but Java has a way of chosing between that one and each of the two methods above. It’s just the string and the character array parameters that cause ambiguity; character arrays and objects can happily coexist.

The following lines will compile:

    Object o = null;
    String s = null;
    System.out.println(o);
    System.out.println(s);

Here is the output:

    null
    null

The following will also compile:

    char[] a = null;
    System.out.println(a);

But this actually throws an exception in runtime:

    Exception in thread "main" java.lang.NullPointerException
            at java.io.Writer.write(Writer.java:127)
            at java.io.PrintStream.write(PrintStream.java:470)
            at java.io.PrintStream.print(PrintStream.java:620)
            at java.io.PrintStream.println(PrintStream.java:759)
            ...

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
