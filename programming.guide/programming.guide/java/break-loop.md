



## Loops in Java

1.  [while loop](while-loop.html)
2.  [for loop](for-loop.html)
3.  [for each loop](for-each-loop.html)
4.  [do…while loop](do-while-loop.html)
5.  break
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

# Java Loops: break

`break` can be used to exit a loop in the middle of an iteration:

while (…) { … if (condition) { break ; } … }

**Example:** Simple REPL

    while (true) {
        String command = System.console().readLine();
        if (command.equals("quit")) {
            break;
        }
        process(command);
    }

`break` works precisely the same in `for` and `do`…`while` loops.

## Nested Loops

By default `break` only breaks the **immediately enclosing loop**. To break out of an outer loop, used labelled statements.

**Example:** Breaking out of an inner vs an outer loop.

while (…) { … while (…) { break ; } … }

outer: while (…) { … while (…) { break outer; } … }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
