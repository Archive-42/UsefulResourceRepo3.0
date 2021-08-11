<span class="underline"></span>

<span class="underline"></span>

## Types in Java

1.  [Java Basics: Types](types.html)
2.  [Primitive Types](primitive-types.html)
3.  [Primitives vs Objects and References](primitives-vs-objects-references.html)
4.  [Ranges of Primitive Types](primitive-ranges.html)
5.  [Wrapper Types](wrapper-types.html)
6.  [Autoboxing and unboxing](autoboxing.html)
7.  Boxed values and equality
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

<span class="underline"></span>

## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all Java articles**](index.html)

# Java: Boxed values and equality

When comparing wrapper types such as `Integer`s, `Long`s or `Boolean`s using `==` or `!=`, you're **comparing them as references**, not as values.

If two variables point at different objects, they will not `==` each other, **even if the objects represent the same value**.

**Example:** Comparing different `Integer` objects using `==` and `!=`.

    Integer i = new Integer(10);
    Integer j = new Integer(10);
    System.out.println(i == j); // false
    System.out.println(i != j); // true

The solution is to compare the values using `equals()`…

**Example:** Compare objects using `.equals(…)`

    Integer i = new Integer(10);
    Integer j = new Integer(10);
    System.out.println(i.equals(j)); // true

…or to unbox the operands explicitly.

**Example:** Force unboxing by casting:

    Integer i = new Integer(10);
    Integer j = new Integer(10);
    System.out.println((int) i == (int) j); // true

### Other operators

Arithmetic (`+`, `*`, …), logical (`&&`, `||`, …), bitwise (`&`, `<<`, …) and commparison operators other than `==` and `!=` (`<`, `<=`, …) are only defined for primitive types, so when applied to boxed types the compiler will **automatically unbox** the operands.

**Example:** Operands are unboxed.

    Integer i = new Integer(10);
    Integer j = new Integer(10);
    System.out.println(i <= j); // true

## Caching

To complicate matters further, autoboxing **reuses cached objects** for values between −128 and 127. This causes reference equality to "work" for some boxed values but not for others.

**Example:** 1 is **within** caching range, thus `i` and `j` refer to the **same object**:

    Integer i = 1; // = Integer.valueOf(1)
    Integer j = 1; // = Integer.valueOf(1) - result cached
    System.out.println(i == j); // true

**Example:** 300 is **not within** caching range, thus `k` and `l` refer to **different objects**:

    Integer k = 300; // = Integer.valueOf(300)
    Integer l = 300; // = Integer.valueOf(300) - result not cached
    System.out.println(k == l); // false

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
