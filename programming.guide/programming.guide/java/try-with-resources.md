



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
10. try-with-resources
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

# Java: try-with-resources

A try-with-resource statement automatically closes a "resource" after it has been used. A resource could for instance be a file, stream, reader, writer or socket. Technically it's anything implementing the [`AutoCloseable`](https://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html) interface.

    try (FileWriter w = new FileWriter("file.txt")) {
        w.write("Hello World");
    }
    // w.close() is called automatically

In the above example, `w.close()` is called regardless if `w.write(...)` throws an exception or not. Conceptually it's similar to adding `w.close()` in a [`finally` block](try-finally.html).

## Multiple Resources

You can use multiple resources in a single try-with-resource by separating the declarations with `;` as follows:

    // Copy one byte from src.txt to dst.txt
    try (FileReader fr = new FileReader("src.txt");
         FileWriter fw = new FileWriter("dst.txt")) {
        fw.write(fr.read());
    }

The resources are closed in the reversed order of declarations. In the example above, `fw` would be closed first, then `fr`.

## Exceptions

In the example at the top of this article an `IOException` may be thrown by

- `new FileWriter("file.txt")`
- `w.write("Hello World")`
- The implicit call to `w.close()`

**If the constructor throws an exception**, there will be no object to call `close` on, so the exception propagates without further action:

try (FileWriter w = new FileWriter( "file.txt" )) { w.write( "Hello World" ); } // no call to w.close()

**If the call to `w.write` throws an exception**, `w.close()` will be called, and then the exception will propagate:

try (FileWriter fw = new FileWriter( "file.txt" )) { w.write( "Hello World" ); } // Implicit call to w.close()

**If the implicit call to `w.close()` throws an exception** then this exception propagates:

try (FileWriter fw = new FileWriter( "file.txt" )) { w.write( "Hello World" ); } // Implicit call to w.close()

## Suppressed Exceptions

Another possibility is that `w.write` throws an exception, and then the implicit call to `w.close` **also** throws an exception. In this case the first exception "wins" and the second exception is **suppressed**.

try (FileWriter fw = new FileWriter( "file.txt" )) { w.write( "Hello World" ); } // Implicit call to w.close() w.close exception suppressed w.write exception propagates

For details, se separate article: [Suppressed Exceptions](suppressed-exceptions.html).

## Custom `AutoCloseable` implementation

You can roll your own [`AutoCloseable`](https://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html) implementation as well:

    class MyResource implements AutoCloseable {
        @Override
        public void close() {
            System.out.println("Closing resource");
        }
    }

    class Example {
        public static void main(String[] args) {
            try (MyResource r = new MyResource()) {
                System.out.println("Using resource");
            }
        }
    }

**Output:**

    Using resource
    Closing resource

Since [`AutoCloseable`](https://docs.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html) is a [functional interface](functional-interfaces.html), you can initialize it using a lambda:

    try (AutoCloseable r = () -> System.out.println("Closing")) {
        // ...
    }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
