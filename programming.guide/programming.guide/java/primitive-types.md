<span class="underline"></span>

<span class="underline"></span>

Types in Java
-------------

1.  [Java Basics: Types](types.html)
2.  Primitive Types
3.  [Primitives vs Objects and References](primitives-vs-objects-references.html)
4.  [Ranges of Primitive Types](primitive-ranges.html)
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

Java: Primitive Types
=====================

`byte`

Description

8-bit signed integer

Range

−128

 … 

127

−2<sup>7</sup>

 … 

2<sup>7</sup>−1

[`Byte.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#MIN_VALUE)

 … 

[`Byte.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html#MAX_VALUE)

Format

Two’s complement

Default Value

0

Boxed Type

[`java.lang.Byte`](https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html)

Example Literals

[None](byte-short-literals.html)

`short`

Description

16-bit signed integer

Range

−32,768

 … 

32,767

−2<sup>15</sup>

 … 

2<sup>15</sup>−1

[`Short.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#MIN_VALUE)

 … 

[`Short.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html#MAX_VALUE)

Format

Two’s complement

Default Value

0

Boxed Type

[`java.lang.Short`](https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html)

Example Literals

[None](byte-short-literals.html)

`int`

Description

32-bit signed integer

Range

−2,147,483,648

 … 

2,147,483,647

−2<sup>31</sup>

 … 

2<sup>31</sup>−1

[`Integer.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MIN_VALUE)

 … 

[`Integer.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MAX_VALUE)

Format

Two’s complement

Default Value

0

Boxed Type

[`java.lang.Integer`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html)

Example Literals

`0`   `1`   `2147483648`

Binary: `0b1001`   `0b1111`

Octal: `010`   `0777`   `0111`

Hex: `0x1E3C`   `0xFFFFFF`   `0xCAFEBABE`

With underscores: `1_000_000`   `0xFFFF_FFFF`

`long`

Description

64-bit signed integer

Range

<span class="dynamic-font-size">−9,223,372,036,854,775,808</span>

 … 

<span class="dynamic-font-size">9,223,372,036,854,775,807</span>

−2<sup>63</sup>

 … 

2<sup>63</sup>−1

[`Long.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#MIN_VALUE)

 … 

[`Long.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html#MAX_VALUE)

Format

Two’s complement

Default Value

0

Boxed Type

[`java.lang.Long`](https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html)

Example Literals

`0L`   `123456L`

Binary: `0b10101010L`

Octal: `010L`   `0777L`

Hex: `0x1E3CL`   `0xFFFFFFL`   `0xCAFEBABEL`

With underscores: `1_000_000L`   `0xFFFF_FFFFL`

`float`

Description

32-bit real

Range

± 3.40282347×10<sup>38</sup>

± 1.11111111111111111111111×2<sup>127</sup>

± [`Float.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#MAX_VALUE)

Precision

~6 digits

Format

IEEE 754

Default Value

0

Boxed Type

[`java.lang.Float`](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html)

Special Values

[`Float.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#MIN_VALUE)

The smallest value greater than zero

[`Float.NaN`](https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html#NaN)

\\

Example Literals

`1.0f`   `3.1415f`   `.5f`

`1e5f`   `1.1e-20f`   `1.1e+003f`

Hex: `0x1.8p2f`   `0x1.FFFFFEp+127f`

`double`

Description

64-bit real

Range

± 1.7976931348623157×10<sup>308</sup>

± 1.11111111111111111…111×2<sup>1023</sup>

± [`Double.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#MAX_VALUE)

Precision

~15 digits

Format

IEEE 754

Default Value

0

Boxed Type

[`java.lang.Double`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html)

Special Values

[`Double.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#MIN_VALUE)

The smallest value greater than zero

[`Double.NaN`](https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html#NaN)

\\

Example Literals

`1.0`   `3.1415`   `.5`

`1e5`   `1.1e-20`   `1.1e+003`

Hex: `0x1.8p2`   `0x1.FFFFFFFFFFFFFp+1023`

With suffix: `1.0d`   `1.1e-20d`

`char`

Description

Unicode character (or 16-bit unsigned integer)

Range

`\u0000`

 … 

`\uFFFF`

0

 … 

65,535

0

 … 

2<sup>16</sup>−1

[`Character.MIN_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#MIN_VALUE)

 … 

[`Character.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html#MAX_VALUE)

Format

UTF-16

Default Value

`\u0000` (0)

Boxed Type

[`java.lang.Character`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html)

Example Literals

`'a'`   `'\n'`   `'"'`   `'\\'`   `'\''`   `'π'`   `'д'`

`boolean`

Description

True or false

Format

undefined

Default Value

false

Boxed Type

[`java.lang.Boolean`](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html)

Special Values

[`Boolean.TRUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html#TRUE)

Boxed true

[`Boolean.FALSE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html#FALSE)

Boxed false

Example Literals

`true`   `false`

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
