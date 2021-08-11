



## Java Exceptions

1.  Throw, Try and Catch
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

# Java Exceptions: Throw, Try and Catch

Exceptions are used when writing code for "exceptional situations" such as:

- The user tried to open a file that doesn't exist
- There's an error in a configuration file
- A server could not be reached due to a network problem

When such event occur, it's appropriate to **throw** an exception. The statements below a `throw` statement are skipped:

statement throw new SomeException();

Execution will continue as normal when the exception is **caught**. You catch an exception using `try` and `catch` in the following way:

try { throw new SomeException(); } catch (SomeException e) { }

If the exception isn't caught within the method, it will **propagate** to the previous method:

void foo() { try { bar(); } catch (Ex e) { } } void bar() { baz(); } void baz() { throw new Ex(); }

## Checked vs Unchecked Exceptions

If the exception being thrown is _checked_, the method needs to include a `throws` declaration to allow it to propagate. See [Java Exception Types](exception-types.html) and [Java Keyword: `throws`](throws.html).

## Uncaught Exceptions

If the exception is **never caught** a stack trace will be printed and the program (or at least the thread) will crash. For an example of how this might look, see [Java: Stack trace](stack-trace.html).

## Other Ways of Throwing

Apart from an explicit `throw` statement, an exception can be thrown due to programming errors, or calling an API method that throws an exception. A few examples:

**Example:** Invalid use of a `null` reference

    String text = null;
    text.length();

This will throw a [`NullPointerException`](https://docs.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html).

**Example:** Calling an API method in a bad way

    String text = "abc";
    Integer.parseInt(text);

This will throw a [`NumberFormatException`](https://docs.oracle.com/javase/8/docs/api/java/lang/NumberFormatException.html).

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
