## Types in Java

1.  [Java Basics: Types](types.html)
2.  [Primitive Types](primitive-types.html)
3.  [Primitives vs Objects and References](primitives-vs-objects-references.html)
4.  [Ranges of Primitive Types](primitive-ranges.html)
5.  [Wrapper Types](wrapper-types.html)
6.  Autoboxing and unboxing
7.  [Boxed values and equality](boxed-values-equality.html)
8.  [No byte or short literals?](byte-short-literals.html)
9.  [Byte (class) vs byte (primitive)](byte-vs-byte.html)
10. [Short (class) vs short (primitive)](short-vs-short.html)
11. [Integer vs int](integer-vs-int.html)
12. [Long (class) vs long (primitive)](long-vs-long.html)
13. [Float (class) vs float (primitive)](float-vs-float.html)
14. [Double (class) vs double (primitive)](double-vs-double.html)
15. [Character vs char](character-vs-char.html)
16. [Boolean (class) vs boolean (primitive)](boolean-vs-boolean.html)

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

## External Resources

[Autoboxing and Unboxing](https://docs.oracle.com/javase/tutorial/java/data/autoboxing.html)  
<span style="color: grey; font-style: italic; font-size: smaller">The Java™ Tutorials</span>

[Boxing Conversion](https://docs.oracle.com/javase/specs/jls/se9/html/jls-5.html#jls-5.1.7)  
<span style="color: grey; font-style: italic; font-size: smaller">Java Language Specification</span>

[Unboxing Conversion](https://docs.oracle.com/javase/specs/jls/se9/html/jls-5.html#jls-5.1.8)  
<span style="color: grey; font-style: italic; font-size: smaller">Java Language Specification</span>

## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all Java articles**](index.html)

# Java: Autoboxing and unboxing

If a value of primitive type (`int`, `double`, `boolean`, …) is provided where a value of wrapper type (a “boxed value” such as `Integer`, `Double`, `Boolean`, …) is expected, the compiler will automatically convert it. This is called **autoboxing**.

**Example:** Autoboxing in its simplest form

    Integer i = 5;  // int turned into an Integer

The opposite conversion is called **unboxing**.

**Example:** Unboxing in its simplest form

    int i = new Integer(5);  // Integer turned into an int

Without these automatic conversions, code would quickly get cluttered, especially when working with collections.

## Unboxing a null reference

If you try to unbox a `null` reference, a `NullPointerException` will be thrown.

**Example:** Compiles but throws a `NullPointerException` when executed

    Integer i = null;
    int j = i;

## Behind the scenes

The Java Language Specification does not specify exactly how the conversion should be done, but the `javac` reference implementation uses the following methods:

<table><colgroup><col style="width: 33%" /><col style="width: 33%" /><col style="width: 33%" /></colgroup><thead><tr class="header"><th>Type</th><th>Boxing</th><th>Unboxing</th></tr></thead><tbody><tr class="odd"><td><p><code>byte</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#valueOf-byte-"><code>Byte.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#byteValue--"><code>Byte.byteValue</code></a></td></tr><tr class="even"><td><p><code>short</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#valueOf-short-"><code>Short.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#shortValue--"><code>Short.shortValue</code></a></td></tr><tr class="odd"><td><p><code>int</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#valueOf-int-"><code>Integer.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#intValue--"><code>Integer.intValue</code></a></td></tr><tr class="even"><td><p><code>long</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#valueOf-long-"><code>Long.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#longValue--"><code>Long.longValue</code></a></td></tr><tr class="odd"><td><p><code>float</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#valueOf-float-"><code>Float.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#floatValue--"><code>Float.floatValue</code></a></td></tr><tr class="even"><td><p><code>double</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#valueOf-double-"><code>Double.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#doubleValue--"><code>Double.doubleValue</code></a></td></tr><tr class="odd"><td><p><code>char</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#valueOf-char-"><code>Character.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#charValue--"><code>Character.charValue</code></a></td></tr><tr class="even"><td><p><code>boolean</code></p></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html#valueOf-boolean-"><code>Boolean.valueOf</code></a></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html#booleanValue--"><code>Boolean.booleanValue</code></a></td></tr></tbody></table>

**Example:** These two snippets are equivalent

    Integer i = 1;
    Integer j = 2;
    Integer k = i + j;

    Integer i = Integer.valueOf(1);
    Integer j = Integer.valueOf(2);
    Integer k = Integer.valueOf(i.intValue() + j.intValue());

## Caching

The `valueOf` methods of `Byte`, `Short`, `Integer`, `Long` and `Character` **caches values** between −128 and 127. This means that two calls to `Integer.valueOf(5)` will return **the same** reference, while two calls to `Integer.valueOf(5000)` **may not**.

This can give rise to some surprising semantics when comparing boxed values using `==` and `!=`.

Recommended reading: [Java: Boxed values and equality](boxed-values-equality.html).

## Comments

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
