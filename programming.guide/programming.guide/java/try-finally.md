



## Java Exceptions

1.  [Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  [Java Exception Types](exception-types.html)
3.  [Chained Exceptions](chained-exceptions.html)
4.  [Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  [Return Values vs Exceptions](return-values-vs-exceptions.html)
9.  try + finally
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

# Java: try + finally

A `finally` block is **always** executed after the code in the preceeding `try` block. It doesn't matter if the `try` block throws an exception, whether or not the exception is caught, or if it executes a `return` statement. (The only way to prevent a `finally` block from running is by terminating the VM through `System.exit` or killing it manually.)

It's often used to restore some state after an operation, such as freeing up resources.

## Without `catch`, no exception thrown

statement try { } finally { }

## Without `catch`, exception thrown

Exception is thrown, finally block is executed, exception propagates:

try { throw new SomeException(); } finally { }

## With `catch`, no exception thrown

try { } catch (SomeException e) { } finally { }

## With `catch`, exception thrown

try { throw new SomeException(); } catch (SomeException e) { } finally { }

## With `return` statement in `try` block

The `return` statement is executed, finally block runs, method actually returns.

try { return ; } finally { }

## With `return` in both `try` and finally blocks

In the snippet below, `return 0` is executed, then the finally block kicks in and `return 1` is executed. The second return overrides the first return which means that the 0 return value is discarded, and the method **returns 1**.

try { return 0 ; } finally { return 1 ; }

## With `throw` in both `try` and `finally` block

The `try` block throws `SomeException`, the finally block kicks in and throws `SomeOtherException`. The second throw "wins" and the first exception is discarded.

try { throw new SomeException(); } finally { throw new SomeOtherException(); }

Similarly a `return` in a `finally` block will cause an exception thrown from a `try` block to be discarded and `throw` in a `finally` block will cause a normal return value from a `try` block to be discarded.

**Note:** The examples are notional and only meant to illustrate the semantics. Some of them wouldn't actually compile due to unreachable code.

## Comments (3)

![User avatar](https://www.gravatar.com/avatar/9345bde1426871f0839fc75d34bfc784?d=mp)

Thanks a lot. In my opinion, it couldn't be explained better.

<span style="color: grey">by Luis Iglesias | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Excellent article

<span style="color: grey">by Emiliano | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/eb4973cdb30a0acf79b800836c771c66?d=mp)

+1 very good visualization

<span style="color: grey">by Valentin Kovalenko | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
