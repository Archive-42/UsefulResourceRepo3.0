



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

# Java: Finding the Nth occurrence of a substring in a String

    public static int ordinalIndexOf(String str, String substr, int n) {
        int pos = -1;
        do {
            pos = str.indexOf(substr, pos + 1);
        } while (n-- > 0 && pos != -1);
        return pos;
    }

`ordinalIndexOf(s, ss, 0)` is equivalent to `s.indexOf(ss)`

`ordinalIndexOf(s, ss, 1)` is equivalent to `s.indexOf(ss, s.indexOf(ss) + 1)`

and so on...

## Example input / output

<table><thead><tr class="header"><th>Expression</th><th>Result</th><th>Explanation</th></tr></thead><tbody><tr class="odd"><td><code>ordinalIndexOf("abcd abcd", "bc", 0)</code></td><td>1</td><td>The 0th occurrence is found at index 1</td></tr><tr class="even"><td><code>ordinalIndexOf("abcd abcd",                   "bc", 1)</code></td><td>6</td><td>The 1st (zero-based) occurrence is found at index 6</td></tr><tr class="odd"><td><code>ordinalIndexOf("abcd abcd", "bc", 2)</code></td><td>-1</td><td>There's no 2nd (zero-based) occurrence, hence -1 is returned</td></tr><tr class="even"><td><code>ordinalIndexOf("aaaaa", "aaa", 1)</code></td><td>1</td><td>Matches may overlap</td></tr></tbody></table>

## Apache Commons Lang

See [`StringUtils.ordinalIndexOf`](https://commons.apache.org/proper/commons-lang/javadocs/api-release/org/apache/commons/lang3/StringUtils.html#ordinalIndexOf%28java.lang.CharSequence,%20java.lang.CharSequence,%20int%29)

## Comments (3)

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Thanks, this was exactly what I wanted!

<span style="color: grey">by Daniel | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/2b625e7df8fd8ce05617a00e93a6d30d?d=mp)

This is resulting in -1

<span style="color: grey">by Ritu | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

-1 indicates that the n:th (zero-based!) occurrence wasn't found. For example `ordinalIndexOf("abab", "ab", 10)` returns -1.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
