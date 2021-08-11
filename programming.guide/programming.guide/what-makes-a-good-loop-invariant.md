<span class="underline"></span>

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  What makes a good loop invariant?
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

<span class="underline"></span>

Top Java Articles
-----------------

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

What makes a good loop invariant?
=================================

Let's break down the question a bit...

What makes a *valid* loop invariant?
------------------------------------

A loop invariant should hold

1.  Before the loop
2.  At the top of the loop body
3.  At the bottom of the loop body
4.  After the loop

It's indeed the case that `true` is a *valid* loop invariant, but it's rarely *useful*...

What makes a *useful* loop invariant?
-------------------------------------

When annotating code with Hoare logic assertions, the invariant `φ` appears as follows:

    {φ}
    while (c)
        {φ ∧ c}
        ...loop body...
        {φ}
    {φ ∧ ¬c}

These code annotations give rise to so called *proof obligations*: If two assertions end up next to each other

    ...
    {α}
    {β}
    ...

then you're obliged to show that `α → β`. So, in the example above, you'll presumably know what's true before the loop and what needs to be true after the loop. For the loop invariant `φ` to be *useful* you thus need to make sure the following implications hold:

-   `<whatever comes before the loop> → φ`, and
-   `φ → <whatever comes after the loop>`.

The second implication disqualifies `true` as a useful loop invariant, as `true → something` only holds if `something` holds by itself. (Put differently, if we choose `true` as our loop invariant, we have no "help" from it when reasoning about the code below the loop.)

Finally: What makes a *good* loop invariant?
--------------------------------------------

Apart from being valid and useful, it's nice if it's

-   As simple as possible
-   As intuitive as possible (Does it reflect the actual algorithm, or does it work by "chance"?)
-   Cause the proof obligations to be as simple as possible

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
