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

Java: Converting a char to an int
=================================

**Digits**: Converting character `'5'` to integer `5`:

    char c = '5';
    int i = c - '0';  // i == 5

**ASCII**: Converting `'A'` to `65`:

    char c = 'A';
    int i = c;        // i == 65

Ehm, what?!
-----------

In Java a `char` has a dual interpretation in the form of it's numerical ASCII value (or code point to be precise). We here use the fact that `'0'`, … `'9'` have sequential ASCII values (`'0'` has value 48, `'1'` has value 49, and so on). This means that <span class="no-wrap">`'n' -               '0'` = <span style="font-style: italic">n</span></span>.

-   `'0' -               '0'` = 48 - 48 = 0
-   `'1' -               '0'` = 49 - 48 = 1
-   `'2' -               '0'` = 50 - 48 = 2
-   …
-   `'9' -               '0'` = 57 - 48 = 9

Comments (3)
------------

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Also a standard [`Character.digit`](https://docs.oracle.com/javase/10/docs/api/java/lang/Character.html#digit(char,int)) method could be used. E.g. `Character.digit('9', 10) == 9` (`int`).

<span style="color: grey">by georgeek | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

What happens if you add a number, say 5 to `C` or any other character?

<span style="color: grey">by Anonymous | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

If you add 5 to `C` you'll get an `H` (or 72 if you look at it as an int). You can try running this yourself: `System.out.println('C' + 5);`.

<span style="color: grey">by Anonymous | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
