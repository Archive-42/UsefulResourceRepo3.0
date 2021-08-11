



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

# Java: Convert from Number to int

Use [`Number.intValue`](https://docs.oracle.com/javase/8/docs/api/java/lang/Number.html#intValue--):

    Number n = ...
    int i = n.intValue()

Note that this simply **discards all but the lowest 32 bits**. If the `Number` is outside of the range −2,147,483,648…2,147,483,647 the conversion my have unexpected results.

<table><thead><tr class="header"><th>Number</th><th>intValue()</th></tr></thead><tbody><tr class="odd"><td>1,000</td><td>1,000</td></tr><tr class="even"><td>2,147,483,647</td><td>2,147,483,647</td></tr><tr class="odd"><td>2,147,483,648</td><td>−2,147,483,648</td></tr><tr class="even"><td>2,147,483,649</td><td>−2,147,483,647</td></tr><tr class="odd"><td>4,294,967,296</td><td>0</td></tr><tr class="even"><td>10,000,000,000</td><td>1,410,065,408</td></tr><tr class="odd"><td>−10,000,000,000</td><td>−1,410,065,408</td></tr></tbody></table>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
