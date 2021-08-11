



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

# Where's the javadoc for values and valueOf methods on enums?!

The static `values()` and `valueOf(String name)` methods available on all enum types do not have ordinary javadocs. As opposed to for instance [`name()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Enum.html#name--) which is declared on the [`Enum`](https://docs.oracle.com/javase/8/docs/api/java/lang/Enum.html) class, the `values()` and `valueOf(String name)` methods are "magically" added by the Java compiler. In other words, these methods are not found in any `.java` file and therefore there's no place to put the javadoc!

This is described in JLS which in fact also includes the "hidden" javadoc:

> In addition, if `E` is the name of an enum type, then that type has the following implicitly declared `static` methods:
>
>     /**
>      * Returns an array containing the constants of this enum
>      * type, in the order they're declared.  This method may be
>      * used to iterate over the constants as follows:
>      *
>      *    for(E c : E.values())
>      *        System.out.println(c);
>      *
>      * @return an array containing the constants of this enum
>      * type, in the order they're declared
>      */
>      public static E[] values();
>
>     /**
>      * Returns the enum constant of this type with the specified
>      * name.
>      * The string must match exactly an identifier used to declare
>      * an enum constant in this type.  (Extraneous whitespace
>      * characters are not permitted.)
>      *
>      * @return the enum constant with the specified name
>      * @throws IllegalArgumentException if this enum type has no
>      * constant with the specified name
>      */
>     public static E valueOf(String name);
>
> <a href="http://docs.oracle.com/javase/specs/jls/se7/html/jls-8.html#jls-8.9.2" class="quote-source">JLS §8.9.2</a>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
