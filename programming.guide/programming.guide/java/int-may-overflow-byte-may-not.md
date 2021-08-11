



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

# Java: Integers may overflow, but bytes may not?

Why are `int` expressions allowed to overflow, but not `byte` expressions?

    int i = Integer.MAX_VALUE + 1;  // allowed to overflow
    byte b = possible lossy conversion from int to byteByte.MAX_VALUE + 1;    // not allowed to overflow

Before you shout _"`Byte.MAX_VALUE + 1` is an `int` expression! This is a simple type error!"_ note that this **does compile**:

    byte b = Byte.MAX_VALUE + 0;

## The + Operator

The `+` operator is indeed only defined for `int`, `long`, `float`, `double` and `String` operands. In our snippet `Byte.MAX_VALUE` will therefore be promoted to an `int` and the **result of the addition will be of type `int`**.

**Example:** A `byte` plus a `byte` is an `int`:

    String type(byte b) { return "byte"; }
    String type(int i)  { return "int"; }
    …
    byte a = 10, b = 20;
    System.out.println(type(a + b)); // "int"

But as we saw earlier, there's something else at play here…

## Something about that overflow…

The compile error only occurs when there's a byte overflow, which reveals that the computation is performed at compile time. The JLS refers to this as a compile-time **constant expression**:

> **15.28 Constant Expression**
>
> A compile-time _constant expression_ is an expression denoting a value of primitive type or a <span class="mono">String</span> that does not complete abruptly and is composed using only the following:
>
> - …
> - Literals of primitive type and literals of type <span class="mono">String</span> (§3.10.5)
> - The additive operators <span class="mono">+</span> and <span class="mono">-</span>
> - Qualified names of the form _TypeName.Identifier_ that refer to constant variables (§4.12.4) <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.28" class="quote-source">JLS §15.28</a>

A constant variable is a variable that is **final** and **initialized with a compile-time constant expression**. `Byte.MAX_VALUE` happens to be a constant variable. (If it wasn’t `byte b = Byte.MAX_VALUE + 0` would not have compiled!)

**Example:** Making a variable final makes it a constant expression.

final

<span class="keyword">byte</span> a = <span class="num_lit">1</span>;

<span class="keyword">byte</span> b = a + <span class="num_lit">1</span>;

<span class="err-squiggly"><span class="keyword">byte</span> b = a + <span class="num_lit">1</span>;</span> <span class="comment">// can't convert from int to byte</span>

## Why is a byte not allowed to overflow like an int?

There are some special language rules for so called **assignment contexts**. Constant expressions that fit in the type of the variable (`byte` in our case) will be automatically converted by the compiler.

> **5.2. Assignment Context**
>
> \[…\]
>
> A <span class="highlight">narrowing primitive conversion</span> may be used if the type of the variable is <span class="mono highlight">byte</span>, <span class="mono">short</span>, or <span class="mono">char</span>, and the value of the constant expression is representable in the type of the variable. <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-5.html#jls-5.2" class="quote-source">JLS §5.2</a>

So here’s the actual reason the snippet at the top doesn’t compile: Constant expressions **that do not fit does not get converted**, and thus the expression remains as an `int` and **a typing error occurs** since an `int` cannot be stored in a `byte` variable.

## An even funnier case

During evaluation of constant expressions, the compiler follows the rules of 2’s complement 2 arithmetic. This means that an `int` expression can overflow and wrap back into the range of a `byte`!

    byte a = Integer.MAX_VALUE;      // Does not compile.
    byte b = Integer.MAX_VALUE * 2;  // Does compile!

The `b` variable will contain the value −2.

## Similar article

There are literals for all primitive types (`int`, `long`, `char`, `float`, `double`, `char`, and `boolean`) **except** `byte` and `short`. [No byte or short literals?](byte-short-literals.html) discusses this oddity.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
