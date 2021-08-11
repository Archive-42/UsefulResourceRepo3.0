<span class="underline"></span>

<span class="underline"></span>

References
----------

[What does final mean, and are final variables always immutable?](final-variable.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[4.12.4. final Variables](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.12.4)  
<span style="color: grey; font-style: italic; font-size: smaller">JLS</span>

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

Java: What is effectively final?
================================

Prerequisit: [What does final mean, and are final variables always immutable?](final-variable.html)

**Effectively Final**

A variable is *effectively final* if you could mark it as `final` without introducing compilation errors.

Relevance to inner classes and lambdas
--------------------------------------

Unlike for example JavaScript, inner classes and lambdas can't access mutable variables in the enclosing scope. Such variables must be final or effectively final.

    int i = 0;        // Effectively final
    i++;              // No longer effectively final
    Runnable r = () -> System.out.println(i);
                                     Compile error

With the introduction of lambdas, closures became much more common. The notion of "effectively final" was introduced to alleviate the programmer from having to frequently mark variables as `final` to satisfy the compiler.

Formal definition
-----------------

Here's the formal definition from [JLS §4.12.4](https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.12.4):

> Certain variables that are not declared final are instead considered *effectively final*:
>
> -   A local variable whose declarator **has an initializer** ([§14.4.2](https://docs.oracle.com/javase/specs/jls/se8/html/jls-14.html#jls-14.4.2)) is *effectively final* if all of the following are true:
>     -   It is not declared `final`.
>     -   It never occurs as the left hand side in an assignment expression ([§15.26](https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.26)). (Note that the local variable declarator containing the initializer is *not* an assignment expression.)
>     -   It never occurs as the operand of a prefix or postfix increment or decrement operator ([§15.14](https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.14), [§15.15](https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.15)).
> -   A local variable whose declarator **lacks an initializer** is *effectively final* if all of the following are true:
>
>     -   It is not declared `final`.
>     -   Whenever it occurs as the left hand side in an assignment expression, it is definitely unassigned and not definitely assigned before the assignment; that is, it is definitely unassigned and not definitely assigned after the right hand side of the assignment expression ([§16, Definite Assignment](https://docs.oracle.com/javase/specs/jls/se8/html/jls-16.html)).
>     -   It never occurs as the operand of a prefix or postfix increment or decrement operator.
>
> -   A method, constructor, lambda, or exception parameter ([§8.4.1](https://docs.oracle.com/javase/specs/jls/se8/html/jls-8.html#jls-8.4.1), [§8.8.1](https://docs.oracle.com/javase/specs/jls/se8/html/jls-8.html#jls-8.8.1), [§9.4](https://docs.oracle.com/javase/specs/jls/se8/html/jls-9.html#jls-9.4), [§15.27.1](https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.27.1), [§14.20](https://docs.oracle.com/javase/specs/jls/se8/html/jls-14.html#jls-14.20)) is treated, for the purpose of determining whether it is effectively final, as a local variable whose declarator has an initializer.
>
> If a variable is effectively final, adding the final modifier to its declaration will not introduce any compile-time errors. Conversely, a local variable or parameter that is declared final in a valid program becomes effectively final if the final modifier is removed. <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-4.html#jls-4.12.4" class="quote-source">JLS §4.12.4</a>

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
