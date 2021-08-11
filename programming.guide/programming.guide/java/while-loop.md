



## Loops in Java

1.  while loop
2.  [for loop](for-loop.html)
3.  [for each loop](for-each-loop.html)
4.  [do…while loop](do-while-loop.html)
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

# Java: while loop

    while (awake) {
        writeCode();
        drinkCoffee();
    }

A `while` loop executes instructions repeatedly until the condition becomes false.

while ( condition ) { true false instructions }

Unless you want the loop to run indefinitely, it's important that `instructions` eventually make `condition` false.

**Example:**

    int i = 3;
    while (i >= 0) {
        System.out.println("Count down: " + i);
        i--;
    }

    Count down: 3
    Count down: 2
    Count down: 1
    Count down: 0

**Example:** Infinite loop

    while (true) {
        System.out.println("Looping forever!");
    }

If the condition is initially false the body will not execute at all.

**Example:**

    while (false) {
        System.out.println("Never printed");
    }

<span class="small">(Doesn't even compile due to <span style="font-style: italic">"Unreachable statement"</span>.)</span>

## Optional Braces

For single statement bodies, the **braces are optional**, just as with `if` and `for` statements.

**Example:** These two snippets are equivalent:

    while (!successful) {
        tryAgain();
    }
    System.out.println("Success!");

    while (!successful)
        tryAgain();

    System.out.println("Success!");

The official style guide does however madate the use of braces for safety.

## Accidental semicolon

There should **not** be a semicolon after the loop declaration:

    while (…); { … } // bad!

See [_Beware of accidental semicolons in while and for loops!_](beware-of-accidental-semicolons-in-while-and-for-loops.html)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
