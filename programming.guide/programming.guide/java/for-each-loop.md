



## Loops in Java

1.  [while loop](while-loop.html)
2.  [for loop](for-loop.html)
3.  for each loop
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

# Java: for each loop

The following code iterates over the elements in `iterable`:

    for (Type elem : iterable) {
        // process elem
    }

Where `iterable` can be

- An array, such as a `String[]`, or
- An implementation of [`Iterable`](https://docs.oracle.com/javase/8/docs/api/java/util/Iterable.html) such as an `ArrayList` or a `HashSet`.

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

## Optional Braces

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

## Accidental semicolon

There should **not** be a semicolon after the loop declaration:

    for (…); { … }

See [_Beware of accidental semicolons in while and for loops!_](beware-of-accidental-semicolons-in-while-and-for-loops.html)

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
