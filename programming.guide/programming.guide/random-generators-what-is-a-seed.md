<span class="underline"></span>

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
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

Random Generators: What is a seed?
==================================

Computers can't by themselves generate truly random numbers. It's therefore common to use *pseudorandom* number generators.

A pseudorandom number generator generates the **same number sequence** over and over. It's in fact semantically equivalent to

    // Seemingly random, but fixed, list of numbers
    numbers ← { 8651, 1932, 18626, 77, 8524 }
    while true
        for n in numbers
            print n

In reality `numbers` obviously corresponds to a much longer array (typically 2<sup>32</sup> numbers) and the implementation doesn't store the numbers explicitly.

**The seed is simply the index at which the generator starts reading numbers.**

To get *truly* random numbers, the computer needs some source of [entropy](https://en.wikipedia.org/wiki/Entropy_(computing)). Examples of such sources are keyboard/mouse readings or the system clock.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
