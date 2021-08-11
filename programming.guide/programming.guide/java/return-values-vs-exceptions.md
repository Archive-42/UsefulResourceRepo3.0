<span class="underline"></span>

<span class="underline"></span>

## External Resources

[Effective Java, Item 69: Use exceptions only for exceptional conditions](https://books.google.se/books?id=BIpDDwAAQBAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by Joshua Bloch</span>

## Java Exceptions

1.  [Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  [Java Exception Types](exception-types.html)
3.  [Chained Exceptions](chained-exceptions.html)
4.  [Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  Return Values vs Exceptions
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

# Java: Return Values vs Exceptions

You should only use exceptions for exceptional situations. An exceptional situation is an unexpected situation that is out of the ordinary. A situation is _not_ exceptional just because it's _less common_ than other situations. In a non-exceptional situation you should use return values instead of exceptions.

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><tbody><tr class="odd"><td><strong>Exceptional Examples</strong></td><td><strong>Non-exceptional Examples</strong></td></tr><tr class="even"><td><ul><li>An attempt to open a file failed</li><li>Computer ran out of memory</li><li>Program tried to divide by 0</li></ul></td><td><ul><li>Requested username already taken</li><li>A text string was entered in a numeric field</li><li>User does not have permission to change the data</li></ul></td></tr></tbody></table>

Exceptional control flow is more complicated than ordinary `if` statements. In other words, by chosing exceptions for non-exceptional control flow you're making the code more complicated than it needs to be.

**Example:** Instead of this…

    try {
        foo();
        // then...
    } catch (FooException ex) {
        // else...
    }

…let `foo()` return true on success:

    if (foo()) {
        // then...
    } else {
        // else...
    }


Or, if the return value of `foo()` is reserved for normal operation:

**Example:** Instead of this…

    try {
        value = foo();
        // then...
    } catch (FooException ex) {
        // else...
    }

…let `foo()` return `FooResult`…

    FooResult result = foo();
    if (result.success()) {
        value = result.getValue();
        // then...
    } else {
        // else...
    }

…or use a separate method

    if (isFooAvailable()) {
        value = foo();
        // then...
    } else {
        // else...
    }


In the last two snippets, it's perfectly fine to let `result.getValue()` / `foo()` to throw an unchecked exception if `result.success()` / `isFooAvailable()` returns false.

If all you want to do is to skip the remaining part of a sequence of statements:

**Example:** Instead of this…

    try {
        if (!initFoo()) throw AbortInit();
        // ...
        if (!initBar()) throw AbortInit();
        // ...
    } catch (AbortInit e) {
    }

…use a separate method…

    void init() {
        if (!initFoo()) return;
        // ...
        if (!initBar()) return;
        // ...
    }

…or use a labeled block and `break`:

    init: {
        if (!initFoo()) break init;
        // ...
        if (!initBar()) break init;
        // ...
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
