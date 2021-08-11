<span class="underline"></span>

<span class="underline"></span>

External Resources
------------------

[The Catch or Specify Requirement](https://docs.oracle.com/javase/tutorial/essential/exceptions/catchOrDeclare.html)  
<span style="color: grey; font-style: italic; font-size: smaller">The Java Tutorials</span>

[Unchecked Exceptions — The Controversy](http://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html)  
<span style="color: grey; font-style: italic; font-size: smaller">The Java Tutorials</span>

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Difference between Checked and Unchecked Exceptions
===================================================

A **checked exception** must either be

-   caught within the method, *or*
-   declared to be thrown by the method

This is enforced ("checked") by the compiler.

**Example:** [`Exception`](https://docs.oracle.com/javase/8/docs/api/java/lang/Exception.html) is a checked exception, so this does **not compile**:

    class Example {
        void method() {
            throw"error: Exception must be caught or declared to be thrown" new Exception();
         }
    }

Here a `throws` declaration has been added, so this **does compile**:

    class Example {
        void method() throws Exception {
            throw new Exception();
        }
    }

Here the exception is caught within the method, so this **does compile**:

    class Example {
        void method() {
            try {
                throw new Exception();
            } catch (Exception e) {
                // ...
            }
        }
    }

An **unchecked exception** does **not** have this requirement.

**Example:** [`RuntimeException`](https://docs.oracle.com/javase/8/docs/api/java/lang/RuntimeException.html) is an unchecked exception, so this **does compile**:

    class Example {
        void method() {                    // No throws declaration
            throw new RuntimeException();  // No try/catch
        }
    }

Checked exceptions are often used as "alternative return values" for unpredictable errors from which client can recover. Unchecked exceptions are usually an indication of a programming error or other condition from which the client can't be expected to recover.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
