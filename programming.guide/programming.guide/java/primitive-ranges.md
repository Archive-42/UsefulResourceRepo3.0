



## Types in Java

1.  [Java Basics: Types](types.html)
2.  [Primitive Types](primitive-types.html)
3.  [Primitives vs Objects and References](primitives-vs-objects-references.html)
4.  Ranges of Primitive Types
5.  [Wrapper Types](wrapper-types.html)
6.  [Autoboxing and unboxing](autoboxing.html)
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



## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all Java articles**](index.html)

# Java: Ranges of Primitive Types

Ranges are **inclusive** in both ends.

byte

−128

127

−2<sup>7</sup>

2<sup>7</sup>−1

[`Byte.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#MIN_VALUE)

[`Byte.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#MAX_VALUE)

short

−32,768

32,767

−2<sup>15</sup>

2<sup>15</sup>−1

[`Short.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#MIN_VALUE)

[`Short.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#MAX_VALUE)

int

−2,147,483,648

2,147,483,647

−2<sup>31</sup>

2<sup>31</sup>−1

[`Integer.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MIN_VALUE)

[`Integer.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MAX_VALUE)

long

−9,223,372,036,854,775,808

9,223,372,036,854,775,807

−2<sup>63</sup>

2<sup>63</sup>−1

[`Long.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#MIN_VALUE)

[`Long.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#MAX_VALUE)

float

−3.40282347×10<sup>38</sup>

3.40282347×10<sup>38</sup>

−1.111…1×2<sup>127</sup>

1.111…1×2<sup>127</sup>

`-`[`Float.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#MAX_VALUE)

[`Float.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#MAX_VALUE)

double

−1.7976931348623157×10<sup>308</sup>

1.7976931348623157×10<sup>308</sup>

−1.111…1×2<sup>1023</sup>

1.111…1×2<sup>1023</sup>

`-`[`Double.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#MAX_VALUE)

[`Double.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#MAX_VALUE)

char

`\u0000`

`\uFFFF`

0

65,535

0

2<sup>16</sup>−1

[`Character.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#MIN_VALUE)

[`Character.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#MAX_VALUE)

For more details: [Java: Primitive Types](primitive-types.html).

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
