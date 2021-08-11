<span class="underline"></span>

<span class="underline"></span>

Related
-------

[The most copied StackOverflow snippet of all time is flawed!](../worlds-most-copied-so-snippet.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Binary prefix](https://en.wikipedia.org/wiki/Binary_prefix)  
<span style="color: grey; font-style: italic; font-size: smaller">Wikipedia</span>

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

Java: Formatting byte size to human readable format
===================================================

☞

The code in the first version of this article was flawed. The code below is now the recommended solution. See the following article for details:

[The most copied StackOverflow snippet of all time is flawed!](../worlds-most-copied-so-snippet.html)

SI (1 k = 1,000)
----------------

    public static String humanReadableByteCountSI(long bytes) {
        if (-1000 < bytes && bytes < 1000) {
            return bytes + " B";
        }
        CharacterIterator ci = new StringCharacterIterator("kMGTPE");
        while (bytes <= -999_950 || bytes >= 999_950) {
            bytes /= 1000;
            ci.next();
        }
        return String.format("%.1f %cB", bytes / 1000.0, ci.current());
    }

Binary (1 K = 1,024)
--------------------

    public static String humanReadableByteCountBin(long bytes) {
        long absB = bytes == Long.MIN_VALUE ? Long.MAX_VALUE : Math.abs(bytes);
        if (absB < 1024) {
            return bytes + " B";
        }
        long value = absB;
        CharacterIterator ci = new StringCharacterIterator("KMGTPE");
        for (int i = 40; i >= 0 && absB > 0xfffccccccccccccL >> i; i -= 10) {
            value >>= 10;
            ci.next();
        }
        value *= Long.signum(bytes);
        return String.format("%.1f %ciB", value / 1024.0, ci.current());
    }

Examples
--------

<table><thead><tr class="header"><th>Input</th><th>SI<br />
<span class="small-detail">1k = 1000</span></th><th>Binary<br />
<span class="small-detail">1k = 1024</span></th></tr></thead><tbody><tr class="odd"><td>0</td><td><code>0 B</code></td><td><code>0 B</code></td></tr><tr class="even"><td>27</td><td><code>27 B</code></td><td><code>27 B</code></td></tr><tr class="odd"><td>999</td><td><code>999 B</code></td><td><code>999 B</code></td></tr><tr class="even"><td>1000</td><td><code>1.0 kB</code></td><td><code>1000 B</code></td></tr><tr class="odd"><td>1023</td><td><code>1.0 kB</code></td><td><code>1023 B</code></td></tr><tr class="even"><td>1024</td><td><code>1.0 kB</code></td><td><code>1.0 KiB</code></td></tr><tr class="odd"><td>1728</td><td><code>1.7 kB</code></td><td><code>1.7 KiB</code></td></tr><tr class="even"><td>1855425871872</td><td><code>1.9 TB</code></td><td><code>1.7 TiB</code></td></tr><tr class="odd"><td>Long.MAX_VALUE</td><td><code>9.2 EB</code></td><td><code>8.0 EiB</code></td></tr></tbody></table>

Comments (6)
------------

![User avatar](https://www.gravatar.com/avatar/6bcae4335d9d7beac1c9163d686c4a31?d=mp)

These are the international standard symbols used for describing the values you calculate. You should use them and not strings like GiB

-   kB, kilo
-   MB, mega
-   GB, giga
-   TB, tera
-   PB, peta
-   EB, exa
-   ZB zetta
-   YB, yotta

<span style="color: grey">by Doug Blake | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

GB and GiB are two different notations. `G` is the SI variant and stands, as you say, for giga (1000<sup>3</sup>). `Gi` is the [IEC standard](https://en.wikipedia.org/wiki/Binary_prefix) and stands for gibi (1024<sup>3</sup>).

But I agree, if I were to pick one, I'd go with the SI standard.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/4ebf5213b42b18c17abfc2e9aa5eb006?d=mp)

For the binary can't you use the shift operator ? like `b < 1<<10 ? String.format("%.1f KiB",                     bytes>>10)`

<span style="color: grey">by Pino | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

Unfortunately no. The unit should for example go from KiB to MiB as soon as the number of bytes is closer to 1024<sup>3</sup> than it is to 1023.9×1024<sup>2</sup>. This happens *between* these two values.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/054fa97d6824f0d52c39149254a4b7fb?d=mp)

Why use `0xfffccccccccccccL`?

<span style="color: grey">by Ma | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

Because that is the point at which one should transition from PB to EB. Think of it like this: `0xfffccccccccccccL` is to 2<sup>50</sup> what 999,950,000 is to 10<sup>9</sup>.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
