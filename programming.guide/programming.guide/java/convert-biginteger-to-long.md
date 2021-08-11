



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

# Java: Convert from BigInteger to long

Use [`Number.longValue`](https://docs.oracle.com/javase/8/docs/api/java/lang/Number.html#longValue--):

    BigInteger bigInt = ...
    long l = bigInt.longValue()

Note that this simply **discards all but the lowest 64 bits**. If the `BigInteger` is outside of the range −9,223,372,036,854,775,808…9,223,372,036,854,775,807 the conversion my have unexpected results.

<table><thead><tr class="header"><th>BigInteger</th><th>longValue()</th></tr></thead><tbody><tr class="odd"><td>1,000</td><td>1,000</td></tr><tr class="even"><td>9,223,372,036,854,775,807</td><td>−1</td></tr><tr class="odd"><td>9,223,372,036,854,775,808</td><td>0</td></tr><tr class="even"><td>9,223,372,036,854,775,809</td><td>1</td></tr><tr class="odd"><td>18,446,744,073,709,551,616</td><td>0</td></tr><tr class="even"><td>10,000,000,000,000,000,000</td><td>−1,981,284,352</td></tr><tr class="odd"><td>−10,000,000,000,000,000,000</td><td>1,981,284,352</td></tr></tbody></table>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
