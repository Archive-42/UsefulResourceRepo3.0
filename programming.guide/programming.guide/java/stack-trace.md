<span class="underline"></span>

<span class="underline"></span>

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
11. Stack Traces
12. [Suppressed Exceptions](suppressed-exceptions.html)
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

# Java: Stack Traces

A stack trace is the list of methods that the program was in the middle of when the stack trace was printed. It's typically printed to the console when an unexpected error occurs (an exception is thrown but never caught). A stack trace is very useful for debugging: not only do you see where the error happened, but also how the program arrived in this place.

## Example

    Exception in thread "main" java.lang.NumberFormatException: For input string: "3.1415"
        at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
        at java.lang.Integer.parseInt(Integer.java:580)
        at ExampleCli.parseNumericArgument(ExampleCli.java:47)
        at ExampleCli.parseCliOptions(ExampleCli.java:27)
        at ExampleCli.main(ExampleCli.java:11)

The stack trace can be read from the bottom up:

- `main` has called `parseCliOptions`
- ...which has called `parseNumericArgument`
- ...which has called `parseInt`
- ...which has called `forInputString`
- ...which threw a `NumberFormatException`

The trailing `(ExampleCli.java:11)` part tells the source file and line number of the method call.

## Caused By

A stack trace may have "caused by" sections. An exception in the database layer could for instance be the _cause_ for an exception in the service layer.

See [Java: Chained Exceptions](chained-exceptions.html).

## Suppressed Exceptions

A stack trace may include _suppressed_ exceptions. In rare circumstances two or more exceptions may be created separately. Since Java only allows for one exception to propagate, the other exceptions are suppressed.

See [Java: Suppressed Exceptions](suppressed-exceptions.html).

## Print a stack trace

Use [`Thread.dumpStack`](https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html#dumpStack--) to print a stacktrace without throwing an exception.

You can also examine the current stack trace programatically by calling [`Thread.getStackTrace`](https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html#getStackTrace--) which returns an array of [`StackTraceElement`](https://docs.oracle.com/javase/8/docs/api/java/lang/StackTraceElement.html).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
