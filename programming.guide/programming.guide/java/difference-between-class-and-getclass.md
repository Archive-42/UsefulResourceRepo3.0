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

Java: Difference between a.getClass() and A.class
=================================================

`a.getClass()` returns the **runtime type** of `a`. If you for example have `A a = new B();` then `a.getClass()` will return the `B` class.

`A.class` evaluates to the `A` class **statically**.

Use `a.getClass()` only if you need the runtime type of `a` but don't know it in advance.

Example 1: `getClass`
---------------------

To for instance decide if a given `Object` is of a class in the default package, you could do

    boolean isDeclaredInDefaultPkg(Object o) {
        // Type of 'o' unknown. Use getClass.
        return o.getClass().getPackage() == null;
    }

Example 2: `A.class`
--------------------

Use `A.class` if you know in advance (when writing the code) which class object you're interested in. In example below, we're clearly interested in the `DayOfWeek` class object.

    Set<DayOfWeek> allDays = EnumSet.allOf(DayOfWeek.class);

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
