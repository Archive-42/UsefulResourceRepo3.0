



## Exception Related Keywords

1.  [throw](throw.html)
2.  [throws](throws.html)
3.  [catch](catch.html)
4.  [try](try.html)
5.  finally

## Java Exceptions

1.  [Java Exceptions: Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  [Java Exception Types](exception-types.html)
3.  [Java: Chained Exceptions](chained-exceptions.html)
4.  [Java: Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  [Java: Return Values vs Exceptions](return-values-vs-exceptions.html)
9.  [Java: try + finally](try-finally.html)
10. [Java: try-with-resources](try-with-resources.html)
11. [Java: Stack Traces](stack-trace.html)
12. [Java: Suppressed Exceptions](suppressed-exceptions.html)
13. [Java: throw vs throws vs Throwable](throw-vs-throws-vs-throwable.html)
14. [List of Java Exceptions](list-of-java-exceptions.html)

## Java Keywords

1.  [this](this.html)
2.  [catch](catch.html)
3.  finally
4.  [throw](throw.html)
5.  [throws](throws.html)
6.  [try](try.html)

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

# Java Keyword: finally

The `finally` keyword is used to open a block of code that executes after the preceeding `try` block, regardless of whether an exception was thrown or not.

    try {
        // code that may throw an exception
    } finally {
        // executed regardless if the above
        // code threw an exception or not
    }

A `finally` block is often used to restore state, for instance by releasing resources aquired in the preceeding `try` block.

It can also be used together with `catch` blocks and try-with-resources. See [Java: try + finally](try-finally.html) for details and examples.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
