<span class="underline"></span>

<span class="underline"></span>

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

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

# Java: Is it wrong to use deprecated methods or classes?

Let's look at the documentation of [`@Deprecated`](https://docs.oracle.com/javase/8/docs/api/java/lang/Deprecated.html):

> A program element annotated `@Deprecated` is one that programmers are discouraged from using, typically because it is dangerous, or because a better alternative exists.

The authors doesn't say it's _wrong_ but it's discouraged. Wheather or not it's reasonable to continue using a deprecated API even though it's discouraged boils down the reason for the deprecation.

## When it's wrong

If the API has been discovered to be broken by design you should do your best to avoid using it. An example from the standard API is [`Thread.stop`](https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html#stop--) which has been deemed dangerous due to memory consistency issues. Using this method is indeed _wrong_.

## When it's not

If the API has been deprecated simply because there's a newer and shinier way of solving the task, the existing API will most likely continue to function as advertised and you may deal with it according to your own discretion. Sooner or later you may want to address it, but it's it's definitely not wrong to prioritize other tasks.

To give an example on the low end of the scale: The [`FontMetrics.getMaxDecent`](http://java.sun.com/j2se/1.5.0/docs/api/java/awt/FontMetrics.html#getMaxDecent%28%29). Reason for deprecation: Spelling error.

> **Deprecated.** _As of JDK version 1.1.1, replaced by getMaxDescent()._

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
