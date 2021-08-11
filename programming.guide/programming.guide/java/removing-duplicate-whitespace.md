



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

# Java: Remove duplicate whitespace in strings

    str = str.replaceAll("\\s+", " ");

## Examples

<table><thead><tr class="header"><th>Input</th><th>Result</th></tr></thead><tbody><tr class="odd"><td><code>"lorem    ipsum"</code></td><td><code>"lorem ipsum"</code></td></tr><tr class="even"><td><code>"lorem\nipsum"</code></td><td><code>"lorem\nipsum"</code></td></tr><tr class="odd"><td><code>"lorem  ipsum   dolor \n                     sit."</code></td><td><code>"lorem ipsum dolor sit"</code></td></tr></tbody></table>

## What does that `\s+` mean?

`\s+` is a regular expression. `\s` matches a space, tab, new line, carriage return, form feed or vertical tab, and `+` says "one or more of those". In other words the above code will replace all whitespace substrings with a single space character.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
