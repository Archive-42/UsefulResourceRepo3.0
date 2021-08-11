<span class="underline"></span>

<span class="underline"></span>

Loops in Java
-------------

1.  [while loop](while-loop.html)
2.  for loop
3.  [for each loop](for-each-loop.html)
4.  [do…while loop](do-while-loop.html)
5.  [break](break-loop.html)
6.  [continue](continue.html)
7.  [Beware of accidental semicolons in while and for loops!](beware-of-accidental-semicolons-in-while-and-for-loops.html)

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

Java: for loop
==============

    // Traditional, print 0 to 9
    for (int i = 0; i < 10; i++) {
        System.out.println(i);
    }

    // Enhanced, iterate over collection
    for (String s : listOfStrings) {
        System.out.println(s);
    }

Traditional `for` loops
-----------------------

The following code runs `instructions` repeatedly until `condition` becomes false:

    for (initialization; condition; step) {
        instructions
    }

-   `initialization` runs **before the first** iteration
-   `condition` is evaluated **before each** iteration
-   If it evaluates to true, `instructions` are executed
-   `step` runs **after each** iteration

for (initialization; condition; step) { false true instructions }

**Example:** Add integers between 1 and 100

    int sum = 0;
    for (int i = 1; i <= 100; i++) {
        sum += i;
    }
    System.out.println("1 + 2 + ... + 100 = " + sum);

**Example:** Iterate over a linked list

    for (Node n = list.head; n != null; n = n.next) {
        // process n
    }

The scope of variables declared in the loop initialization (such as `int i` and `Node n` in the examples above) is limited to the loop.

**Example:**

    for (int i = 0; i < 10; i++) {
        // ...
    }
    i = 123;  // Error: 'i' out of scope

Each component is optional.

**Example:** Omitting initialization and step components as follows…

    for (; cond;) {
        ...
    }

…is equivalent to `while (cond) { ... }`

If `condition` is left empty it defaults to true.

**Example:** Infinite loop

    for (;;) {
        System.out.println("Looping forever!");
    }

For each loop ("Enhanced for loop")
-----------------------------------

The following code iterates over the elements in `iterable`:

    for (Type elem : iterable) {
        // process elem
    }

Where `iterable` can be

-   An array, such as a `String[]`, or
-   An implementation of [`Iterable`](https://docs.oracle.com/javase/8/docs/api/java/util/Iterable.html) such as an `ArrayList` or a `HashSet`.

### Behind the scenes

In case `iterable` is an array, the above snippet is equivalent to

    for (int i = 0; i < iterable.length; i++) {
        Type elem = iterable[i];
        // process elem
    }

In case `iterable` is an [`Iterable`](https://docs.oracle.com/javase/8/docs/api/java/lang/Iterable.html), it's equivalent to

    Iterator<Type> iter = iterable.iterator();
    while (iter.hasNext()) {
        Type elem = iter.next();
        // process elem
    }

### Auto boxing

Thanks to auto (un)boxing, you can for instance use an `int` to iterate over a list of `Integer`:

**Example:**

    List<Integer> ints = new ArrayList<>();
    // ...
    for (int i : ints) {
        // ...
    }

Optional Braces
---------------

For single statement bodies, the **braces are optional**, just as with `if` and `while` statements.

These two snippets are equivalent:

    for (int i : arr) {
        System.out.println(i);
    }
    System.out.println("done");

    for (int i : arr)
        System.out.println(i);

    System.out.println("done");

The official style guide does however madate the use of braces for safety.

Accidental semicolon
--------------------

There should **not** be a semicolon after the loop declaration:

    for (…); { … }

See [*Beware of accidental semicolons in while and for loops!*](beware-of-accidental-semicolons-in-while-and-for-loops.html)

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
