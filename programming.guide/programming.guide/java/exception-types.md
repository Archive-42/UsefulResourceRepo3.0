



## Java Exceptions

1.  [Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  Java Exception Types
3.  [Chained Exceptions](chained-exceptions.html)
4.  [Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  [Return Values vs Exceptions](return-values-vs-exceptions.html)
9.  [try + finally](try-finally.html)
10. [try-with-resources](try-with-resources.html)
11. [Stack Traces](stack-trace.html)
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

# Java Exception Types

[`Throwable`](https://docs.oracle.com/javase/8/docs/api/java/lang/Throwable.html), [`Error`](https://docs.oracle.com/javase/8/docs/api/java/lang/Error.html), [`Exception`](https://docs.oracle.com/javase/8/docs/api/java/lang/Exception.html) and [`RuntimeException`](https://docs.oracle.com/javase/8/docs/api/java/lang/RuntimeException.html) are classes with special meaning in the Java language. The compiler imposes different constraints on these classes when used in `throw` statements and `catch` blocks. The classes have the following inheritance hierarchy:

![Illustration of Exception Hierarchy](exception-types/hierarchy.svg)

## Throwable

In Java you can only `throw` and `catch` objects of type, or subtype of, [`Throwable`](https://docs.oracle.com/javase/8/docs/api/java/lang/Throwable.html).

The only `Throwable` subclasses provided by the Java API are `Error` and `Exception`.

`Throwable` is regarded as a [checked exception](difference-between-checked-and-unchecked-exceptions.html).

## Error

An [`Error`](https://docs.oracle.com/javase/8/docs/api/java/lang/Error.html) is thrown to indicate a serious problem that the application should not try to resolve.

`Error` and all its subclasses are regarded as [unchecked exceptions](difference-between-checked-and-unchecked-exceptions.html).

**Example Errors**

- [`StackOverflowError`](https://docs.oracle.com/javase/8/docs/api/java/lang/StackOverflowError.html), typically due to infinite recursion
- [`OutOfMemoryError`](https://docs.oracle.com/javase/8/docs/api/java/lang/OutOfMemoryError.html)
- [`AssertionError`](https://docs.oracle.com/javase/8/docs/api/java/lang/AssertionError.html)
- [`NoClassDefFoundError`](https://docs.oracle.com/javase/8/docs/api/java/lang/NoClassDefFoundError.html), typically due to a classpath configuration error
- [`NoSuchMethodError`](https://docs.oracle.com/javase/8/docs/api/java/lang/NoSuchMethodError.html)/[`NoSuchFieldError`](https://docs.oracle.com/javase/8/docs/api/java/lang/NoSuchFieldError.html), typically due to wrong version of a class being loaded

## Exception

[`Exception`](https://docs.oracle.com/javase/8/docs/api/java/lang/Exception.html)s are used for conditions that a reasonable application might want to catch.

`Exception` and all it's subclasses (except `RuntimeException`) are regarded as [checked exceptions](difference-between-checked-and-unchecked-exceptions.html).

**Example Exceptions**

- [`InterruptedException`](https://docs.oracle.com/javase/8/docs/api/java/lang/InterruptedException.html), thread was interrupted while in a blocking call
- [`IOException`](https://docs.oracle.com/javase/8/docs/api/java/io/IOException.html), top level exception for all I/O related errors
- [`EOFException`](https://docs.oracle.com/javase/8/docs/api/java/io/EOFException.html)
- [`FileNotFoundException`](https://docs.oracle.com/javase/8/docs/api/java/io/FileNotFoundException.html)
- [`UnknownHostException`](https://docs.oracle.com/javase/8/docs/api/java/net/UnknownHostException.html), check your internet connection :)

## RuntimeException

The [`RuntimeException`](https://docs.oracle.com/javase/8/docs/api/java/lang/RuntimeException.html) is a subclass of `Exception`. It is special because it is an [unchecked exception](difference-between-checked-and-unchecked-exceptions.html).

`RuntimeException`s are used for conditions that an application typically don't catch, such as programming errors.

**Example RuntimeExceptions**

- [`ClassCastException`](https://docs.oracle.com/javase/8/docs/api/java/lang/ClassCastException.html), invalid cast
- [`NullPointerException`](https://docs.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html)
- [`ArithmeticException`](https://docs.oracle.com/javase/8/docs/api/java/lang/ArithmeticException.html), typically due to a division by zero
- [`IndexOutOfBoundsException`](https://docs.oracle.com/javase/8/docs/api/java/lang/IndexOutOfBoundsException.html)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
