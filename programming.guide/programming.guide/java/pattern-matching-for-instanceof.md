<span class="underline"></span>

<span class="underline"></span>

Featured Stack Overflow Post
----------------------------

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)  
  
[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

Related
-------

[JEP draft: Pattern Matching for instanceof (Preview 2)](https://openjdk.java.net/jeps/8235186)  
<span style="color: grey; font-style: italic; font-size: smaller">by Brian Goetz</span>

[JEP 305: Pattern Matching for instanceof (Preview)](https://openjdk.java.net/jeps/305)  
<span style="color: grey; font-style: italic; font-size: smaller">by Brian Goetz</span>

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

Java: Pattern Matching for instanceof
=====================================

☞

This article describes a preview feature, [JEP draft: Pattern Matching for instanceof (Preview 2)](https://openjdk.java.net/jeps/8235186). If you want to play around with this, download and install JDK 15 available [here](https://openjdk.java.net/projects/jdk/15/) and use the `--enable-preview`. This article will be updated as the specification evolves.

Pattern matching for `instanceof` allows you to **bind a new variable** as part of the expression:

    if (obj instanceof String New variable declared…str) {



        System.out.println("obj is a String of length " + str.length()…that can be used as a String);

    }

Scope of instanceof variable
----------------------------

The scope of the the bound variable depends on the context in which the expression is written. The compiler performs a (simple) flow analysis and allows you to use the variable where the `instanceof` check holds true.

In the `if` statement in the example above, the scope of `str` is the true-branch.

`    if (obj               instanceof String str) {`

<span style="
                  position: absolute;
                  top: 0;
                  right: 0;
                  padding: 0.1em 0.3em;
                  font-size: smaller;
                  font-weight: bold;
                  color: blue;
                ">scope of str</span>

`        …`

`    ` `}`

By negating the check, the scope becomes the false branch:

`    if (!(obj               instanceof String str)) {`

`        …`

`    }               else {`

<span style="
                  position: absolute;
                  top: 0;
                  right: 0;
                  padding: 0.1em 0.3em;
                  font-size: smaller;
                  font-weight: bold;
                  color: blue;
                ">scope of str</span>

`        …`

`    ` `}`

The variable is also used in the part of the expression where it is true. This means that you can implement a simple `equals` method without explicit casting:

    boolean equals(Object o) {
        return o instanceof Point p && p.x == x && p.y == y;
    }

Similarity to local variable initialization
-------------------------------------------

Being able to introduce a variable as part of an expression like this is a unique feature. The scoping rules however, follow the same principles as the local variable initialization analysis performed by the compiler. Compare for example the first example in this article with this snippet:

    String str;
    if (obj instanceof String && (str = (String) obj) != null) {
        // str accessible
    }
    // str not accessible (str may not have been initialized)

As you can see, the accessibility of `str` is in practice the same, although the error message is ofcourse different.

Future functionality
--------------------

What’s described in this article can barely be classified as pattern matching. As described in the [JEP](https://openjdk.java.net/jeps/8235186) however, this new `instanceof` functionality will be expanded to support nested matching for record types ([JEP 359](https://openjdk.java.net/jeps/359)), and possibly other patterns.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
