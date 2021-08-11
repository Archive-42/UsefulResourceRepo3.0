<span class="underline"></span>

<span class="underline"></span>

Types in Java
-------------

1.  [Java Basics: Types](types.html)
2.  [Primitive Types](primitive-types.html)
3.  [Primitives vs Objects and References](primitives-vs-objects-references.html)
4.  [Ranges of Primitive Types](primitive-ranges.html)
5.  [Wrapper Types](wrapper-types.html)
6.  [Autoboxing and unboxing](autoboxing.html)
7.  [Boxed values and equality](boxed-values-equality.html)
8.  No byte or short literals?
9.  [Byte (class) vs byte (primitive)](byte-vs-byte.html)
10. [Short (class) vs short (primitive)](short-vs-short.html)
11. [Integer vs int](integer-vs-int.html)
12. [Long (class) vs long (primitive)](long-vs-long.html)
13. [Float (class) vs float (primitive)](float-vs-float.html)
14. [Double (class) vs double (primitive)](double-vs-double.html)
15. [Character vs char](character-vs-char.html)
16. [Boolean (class) vs boolean (primitive)](boolean-vs-boolean.html)

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

[**See all Java articles**](index.html)

Java: No byte or short literals?
================================

According to JLS, a literal such as `123` is an `int`. You can turn it into a `long`, a `float`, a `double` or a `char` literal by writing `123L`, `123f`, `123d` or `'{'` respectively, but there’s **no way to turn it into a `byte` or a `short` literal**.

Look mom, no casting!
---------------------

Still, there’s no casting required here:

    byte b = 123;

This is because the language allows for implicit **compile-time narrowing** of constants.

> **5.2. Assignment Context**
>
> \[…\]
>
> A narrowing primitive conversion may be used if the type of the variable is <span class="mono">byte</span>, <span class="mono">short</span>, or <span class="mono">char</span>, and the value of the constant expression is representable in the type of the variable. <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-5.html#jls-5.2" class="quote-source">JLS §5.2</a>

So, technically speaking there’s no `byte` or `short` literals. However, a regular `int` literal (that fits in a `byte` or a `short`) can be used as such since it’s implicitly converted to a byte in complie-time.

Similar article
---------------

[Integers may overflow, but bytes may not?](int-may-overflow-byte-may-not.html) discusses the situation below:

    int i = Integer.MAX_VALUE + 1;  // allowed to overflow
    byte b = Byte.MAX_VALUE + 1;    // not allowed to overflow

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
