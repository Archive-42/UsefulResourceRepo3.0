



## Java Exceptions

1.  [Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  [Java Exception Types](exception-types.html)
3.  [Chained Exceptions](chained-exceptions.html)
4.  [Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  [Return Values vs Exceptions](return-values-vs-exceptions.html)
9.  [try + finally](try-finally.html)
10. [try-with-resources](try-with-resources.html)
11. [Stack Traces](stack-trace.html)
12. Suppressed Exceptions
13. [throw vs throws vs Throwable](throw-vs-throws-vs-throwable.html)
14. [List of Java Exceptions](list-of-java-exceptions.html)

## Exception Related Keywords

1.  [throw](throw.html)
2.  [throws](throws.html)
3.  [catch](catch.html)
4.  [try](try.html)
5.  [finally](finally.html)

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

# Java: Suppressed Exceptions

Suppressed exceptions were introduced at the same time as the try-with-resource feature. This is because in a try-with-resource two exceptions may be thrown (one from the `try` block and one from the implicit call to `close()`), and since a method can throw at most one exception, the other exception must be **suppressed**.

Suppressed exceptions can be used manually as well. To add an exception as suppressed by another exception, you call [`Throwable.addSuppressed`](https://docs.oracle.com/javase/8/docs/api/java/lang/Throwable.html#addSuppressed-java.lang.Throwable-). To retrieve the suppressed exceptions you call [`Throwable.getSuppressed`](https://docs.oracle.com/javase/8/docs/api/java/lang/Throwable.html#getSuppressed--).

**Example:** Adding and retrieving suppressed exceptions.

    Exception exc = new Exception();
    exc.addSuppressed(new Exception("Sup. 1"));
    exc.addSuppressed(new Exception("Sup. 2"));

    System.out.println(Arrays.toString(exc.getSuppressed()));

**Output:**

    [java.lang.Exception: Suppressed 1, java.lang.Exception: Suppressed 2]

Stack traces includes suppressed exceptions, similarly to how they print "caused by" exceptions.

**Example:** `exc.printStackTrace()` would in the previous example print:

    java.lang.Exception
            at Example.main(Example.java:5)
            Suppressed: java.lang.Exception: Sup. 1
                    at Example.main(Example.java:6)
            Suppressed: java.lang.Exception: Sup. 2
                    at Example.main(Example.java:7)

<span class="small">Suppressed exceptions should not be confused with chained exceptions, also known as wrapped exceptions. See article on [Chained Exceptions](chained-exceptions.html) for details.</span>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
