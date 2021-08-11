<span class="underline"></span>

<span class="underline"></span>

Loops in Java
-------------

1.  [while loop](while-loop.html)
2.  [for loop](for-loop.html)
3.  [for each loop](for-each-loop.html)
4.  [do…while loop](do-while-loop.html)
5.  [break](break-loop.html)
6.  [continue](continue.html)
7.  Beware of accidental semicolons in while and for loops!

Featured Stack Overflow Post
----------------------------

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)  
  
[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

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

Java: Beware of accidental semicolons in while and for loops!
=============================================================

The following code…

    while(cond); {
        // ...
    }

…is actually interpreted as

    while(cond)
        ; // <-- loop body!

    {
        // Separate block statement, not part of the loop!
    }

This is because `;` is treated as a no-op statement, and braces are optional if the loop body consists of a single statement.

This can have catastrophic consequences, since the block statement is only executed once.

**Example:** Program enters an infinite loop since `i++` is never executed

    int i = 0;
    while (i < 10); {
        i++;
    }

Same issue applies for `for` loops.

**Example:** `"Hello"` printed once since the print statement is not part of the loop body

    for (int i = 0; i < 10; i++); {
        System.out.println("Hello");
    }

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
