



## Loops in Java

1.  [while loop](while-loop.html)
2.  [for loop](for-loop.html)
3.  [for each loop](for-each-loop.html)
4.  [do…while loop](do-while-loop.html)
5.  [break](break-loop.html)
6.  continue
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

# Java Loops: continue

`continue` can be used to immediately continue to the next iteration of the loop (or exit the loop if the loop condition no longer holds).

while (…) { … if (something) { continue ; } … }

In `for` loops, a `continue` statement jumps directly to the update statement and then on to the next iteration of the loop (or exits the loop if the loop condition no longer holds).

for ( init ; cond ; step ) { … if (something) { continue ; } … }

**Example:** At iteration 3, skip print statement

    for (int i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;
        }
        System.out.println(i);
    }

**Output:**

    1
    2
    4
    5

In enhanced `for` loops the behavior is similar: the loop variable is updated to point to the next element and the next iteration runs.

**Example:** Process all unprocessed orders

    for (Order order : orders) {
        if (order.isProcessed()) {
            // Continue to next order
            continue;
        }
        process(order);
    }

## Nested Loops

By default `continue` only applies to the **immediately enclosing loop**. To make an outer loop continue, use labelled statements.

**Example:** Continuing an inner vs an outer loop

while (…) { … while (…) { … continue ; … } … }

outer: while (…) { … while (…) { … continue outer; … } … }

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
