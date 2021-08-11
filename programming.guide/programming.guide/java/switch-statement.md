



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

# Java: Switch Statement

**Note:** Not to be confused with [switch expressions](switch-expression.html). (What's the [difference between statements and expressions?](../statements-vs-expressions.html))

## Arrow syntax (Java 12+)

    switch (myInt) {
        case 1 -> System.out.println("One");
        case 2 -> {
            System.out.println("Two");
            System.out.println("No fall through");
        }
        default -> System.out.println("Something else");
    }

No [fall through](switch-statement.html#fall-through).

Multiple statements require `{ ... }`

## Colon syntax

    switch (myInt) {
        case 1:
            System.out.println("One");
            break;
        case 2:
            System.out.println("Two");
            System.out.println("Falling through");
        default:
            System.out.println("Something else");
    }

[Falls through](switch-statement.html#fall-through) if there's no `break`.

Multiple statements don't require `{ ... }`

## Multiple case constants

Both colon and arrow variants allow for multiple constants in each case:

    switch (myInt) {
        case 1, 2, 3:
            System.out.println("One, two or three");
            break;
        default:
            System.out.println("Something else");
    }

## Can't mix colons and arrows

You can't have both cases with colon syntax and cases with arrow syntax in the same switch statement.

## Fall through

Fall through is what happens when execution proceeds from the bottom of one case to the top of the subsequent case.

First case falls through. Output: "Hello World"

    switch (1) {
        case 1:
            System.out.print("Hello ");
            // Fall through to next case
        case 2:
            System.out.println("World");
            break;
        default:
            System.out.println("Not executed");
    }

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
