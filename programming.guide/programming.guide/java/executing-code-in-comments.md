



## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)



## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  Executing code in comments?!
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

# Java: Executing code in comments?!

The following line surprisingly prints `"Hello World"`:

    // \u000d System.out.println("Hello World!");

This is because

- unicode decoding takes place before any other lexical translation, and
- `\u000d` corresponds to a newline character which terminates the comment.

The key benefit of this mechanism is that it makes it trivial to go back and forth between ASCII and any other encoding. You don't even need to figure out where comments begin and end!

As stated in the JLS this allows any ASCII based tool to process the source files:

> \[…\] The Java programming language specifies a standard way of transforming a program written in Unicode into ASCII that changes a program into a form that can be processed by ASCII-based tools. \[…\] <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-3.html#jls-3.3" class="quote-source">JLS §3.3</a>

This gives a fundamental guarantee for platform independence (independence of supported character sets) which has always been a key goal for the Java platform.

Being able to write any Unicode character anywhere in the file is a neat feature, and especially important in comments, when documenting code in non-latin languages. The fact that it can interfere with the semantics in such subtle ways is just an (unfortunate) side-effect.

There are many gotchas on this theme and [_Java Puzzlers_](http://www.javapuzzlers.com/) by Joshua Bloch and Neal Gafter included the following variant:

> Is this a legal Java program? If so, what does it print?
>
>     \u0070\u0075\u0062\u006c\u0069\u0063\u0020\u0020\u0020\u0020
>     \u0063\u006c\u0061\u0073\u0073\u0020\u0055\u0067\u006c\u0079
>     \u007b\u0070\u0075\u0062\u006c\u0069\u0063\u0020\u0020\u0020
>     \u0020\u0020\u0020\u0020\u0073\u0074\u0061\u0074\u0069\u0063
>     \u0076\u006f\u0069\u0064\u0020\u006d\u0061\u0069\u006e\u0028
>     \u0053\u0074\u0072\u0069\u006e\u0067\u005b\u005d\u0020\u0020
>     \u0020\u0020\u0020\u0020\u0061\u0072\u0067\u0073\u0029\u007b
>     \u0053\u0079\u0073\u0074\u0065\u006d\u002e\u006f\u0075\u0074
>     \u002e\u0070\u0072\u0069\u006e\u0074\u006c\u006e\u0028\u0020
>     \u0022\u0048\u0065\u006c\u006c\u006f\u0020\u0077\u0022\u002b
>     \u0022\u006f\u0072\u006c\u0064\u0022\u0029\u003b\u007d\u007d

(This program turns out to be a plain "Hello World" program.)

In the solution to the puzzler, they point out the following:

> More seriously, this puzzle serves to reinforce the lessons of the previous three: **Unicode escapes are essential when you need to insert characters that can’t be represented in any other way into your program. Avoid them in all other cases.**

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
