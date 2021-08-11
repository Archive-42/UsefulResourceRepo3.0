<span class="underline"></span>

<span class="underline"></span>

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

Java: Switch Expression
=======================

**Note:** Not to be confused with [switch statements](switch-statement.html). (What's the [difference between statements and expressions?](../statements-vs-expressions.html))

Let's start with an example:

    int i = switch (someString) {
        case "one" -> 1;
        case "two" -> 2;
        case "three" -> 3;
        default -> -1;
    };

You can switch on integers, strings and enums.

Need to cover all cases
-----------------------

`int i =             1;`  
  

// Compiles

// error: does not cover all possible input values

`String str = switch (i)             {`  
`    case             1 ->             "one";`  
`    case             2 ->             "two";`  
`    case             3 ->             "three";`  

    <span class="keyword">default</span> -&gt; <span class="text_lit">"Something else"</span>;

`}`  

 

Multiple case expressions
-------------------------

You can have multiple case expressions in one case line:

    String str = switch (i) {
        case 1, 2, 3 -> "one, two, or three"
        default -> "Something else";
    }

Blocks statements and `break`
-----------------------------

You can use `break` to "return" values.

This allows for use of block statements.

    String str = switch (i) {

        case 1 -> "one";

        case 2 -> break "two";

        case 3 -> {
            System.out.println("Third case!");
            break "three";
        }

        default -> "Something else";
    };

Throw
-----

Statements must be wrapped in `{ ... }` **except** for a single `throw` statement.

    int i = switch (someString) {
        case "one" -> 1;
        case "two" -> 2;
        case "three" -> 3;
        default -> throw new IllegalArgumentException();
    };

Colon syntax
------------

Colon syntax allows for statements even without `{ ... }`.

Cases will **fall through**.

You must use **break**.

    String str = switch (i) {

        case 1:
            System.out.println("One");
            System.out.println("Falling through!");

        case 2:
            break "Two";

        default:
            break "Something else";
    };

You can **not** mix arrow and colon syntax in the same switch.

Enhanced Switch Statement
-------------------------

Switch **expressions** should not be confused with switch **statements**. (See [Statements vs Expressions](../statements-vs-expressions.html).)

The arrow syntax can be used in **switch statements** too, in which case fall through is disabled and `break` is disallowed.

See article [Switch Statement](switch-statement.html).

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
