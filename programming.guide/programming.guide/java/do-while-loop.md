



## Loops in Java

1.  [while loop](while-loop.html)
2.  [for loop](for-loop.html)
3.  [for each loop](for-each-loop.html)
4.  do…while loop
5.  [break](break-loop.html)
6.  [continue](continue.html)
7.  [Beware of accidental semicolons in while and for loops!](beware-of-accidental-semicolons-in-while-and-for-loops.html)

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

# Java: do…while loop

    do {
        tryConnect();
    } while (!isConnected());

In a `do`…`while` loop the loop body is executed once before the condition is checked.

do { instructions } while (condition); true false // ...

This loop construct is far less common than ordinary [`while` loops](while-loop.html) and [`for` loops](for-loop.html).

## Equivalent `while` loop

The `while` loop below is equivalent to the `do`…`while` loop at the top of this article:

    tryConnect();
    while (!isConnected()) {
        tryConnect();
    }

**Note:** In a `do`…`while` loop, the `while (…)` part must be followed by a `;`.

Adding a `;` in an ordinary `while` loop is however a grave mistake. See [Beware of accidental semicolons in while and for loops!](beware-of-accidental-semicolons-in-while-and-for-loops.html)

## Optional Braces

For single statement bodies, the **braces are optional**, just as with `if` statements and other loop constructs.

**Example:** These two snippets are equivalent:

    do {
        guess();
    } while (!correctAnswer());

    do
        guess();
    while (!correctAnswer());

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
