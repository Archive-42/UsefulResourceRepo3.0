



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

# Java: Removing trailing comma from comma separated string

Here's how:

    str = str.replaceAll(", $", "");

This handles the empty list (empty string) gracefully, as opposed to `lastIndexOf` / `substring` solutions which requires special treatment of such case.

Note that this assumes that the string ends with `,` (comma followed by space).

<table><thead><tr class="header"><th>If your input looks like…</th><th>Use…</th></tr></thead><tbody><tr class="odd"><td><code>"a,b,c,"</code></td><td><code>",$"</code></td></tr><tr class="even"><td><code>"a, b, c, "</code></td><td><code>", $"</code></td></tr><tr class="odd"><td><code>"a , b , c , "</code></td><td><code>" , $"</code></td></tr><tr class="even"><td>Any of the above</td><td><code>"\\s*,\\s*$"</code></td></tr></tbody></table>

## Full example

    String str = "lorem, ipsum, dolor, ";
    str = str.replaceAll(", $", "");
    System.out.println(str);  // "lorem, ipsum, dolor"

## What does `", $"` mean?

`, $` is a regular expression that means "comma, followed by a space, followed by end of string". `\s*` means "0 or more white spaces".

## Comments (2)

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Useful.

<span style="color: grey">by Mythul | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/cfab4cafe2ffbaf08071b3e08139f35d?d=mp)

Awesome!! You have the best article on this topic. You're doing a great job. Thanks for sharing.

Cheers

<span style="color: grey">by Pooja Malhothra | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
