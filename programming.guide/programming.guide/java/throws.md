



## Exception Related Keywords

1.  [throw](throw.html)
2.  throws
3.  [catch](catch.html)
4.  [try](try.html)
5.  [finally](finally.html)

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
3.  [finally](finally.html)
4.  [throw](throw.html)
5.  throws
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

# Java Keyword: throws

    class Example {
        String readUtf8(Path file) throws"This method may throw IOException" IOException {



            byte[] bytes = Files.readAllBytes(file);
            return new String(bytes, StandardCharsets.UTF_8);
        }
    }

The `throws` keyword (not to be confused with the [`throw` keyword](throw.html)) is used in method declarations to indicate that the given exception type may be thrown by the method. If you call the `readUtf8` method in the example above, the `throws` declarations tells you that you should be prepared to catch exceptions of type `IOException`.

Multiple exception types can be specified as follows:

    int m() throws IOException, InterruptedException, TimeOutException {
        // ...
    }

**Checked exceptions** that are thrown in the method **must** be declared in the `throws` clause unless they are caught within the method. Unchecked exceptions do not have this requirement and should therefore **not** be mentioned in `throws` declaration (although the language does not prohibit it). See [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html).

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
