



## Types in Java

1.  [Java Basics: Types](types.html)
2.  [Primitive Types](primitive-types.html)
3.  [Primitives vs Objects and References](primitives-vs-objects-references.html)
4.  [Ranges of Primitive Types](primitive-ranges.html)
5.  Wrapper Types
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

# Java: Wrapper Types

Each primitive type (`int`, `byte`, `double`, …) has a corresponding **wrapper type** (`Integer`, `Byte`, `Double`, …).

    int i = 5;                   // primitive value
    Integer j = new Integer(5);  // "boxed" value

A wrapper type "wraps" a primitive type in a class. The [source code for `Integer`](http://hg.openjdk.java.net/jdk10/jdk10/jdk/file/777356696811/src/java.base/share/classes/java/lang/Integer.java) for example, looks like this:

    public final class Integer extends Number implements Comparable<Integer> {
        // ...
        private final int value;
        // ...
    }

There are many methods and static fields, but this is the gist of it.

The fundamental difference is that an `Integer` is a **reference type**, while an `int` is a **primitive type**. This is important so make sure you understand the difference:

<span class="pointer">[Primitives vs Objects and References](primitives-vs-objects-references.html)</span>

An object of wrapper type is often called a **boxed value**, and converting to and from wrapper types is called **boxing** and **unboxing**.

## All Wrapper Types

There are 8 primitive types, and therefore 8 wrapper types.

<table><thead><tr class="header"><th>Primitive</th><th>Wrapper</th></tr></thead><tbody><tr class="odd"><td><code>byte</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Byte.html"><code>java.lang.Byte</code></a></td></tr><tr class="even"><td><code>short</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Short.html"><code>java.lang.Short</code></a></td></tr><tr class="odd"><td><code>int</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html"><code>java.lang.Integer</code></a></td></tr><tr class="even"><td><code>long</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Long.html"><code>java.lang.Long</code></a></td></tr><tr class="odd"><td><code>float</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Float.html"><code>java.lang.Float</code></a></td></tr><tr class="even"><td><code>double</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Double.html"><code>java.lang.Double</code></a></td></tr><tr class="odd"><td><code>char</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html"><code>java.lang.Character</code></a></td></tr><tr class="even"><td><code>boolean</code></td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Boolean.html"><code>java.lang.Boolean</code></a></td></tr></tbody></table>

## Why boxed values?

Primitives are more efficient and have a smaller memory footprint. Why would you want to work with wrapper types?

The four primary reasons are:

### 1. Generics

You can't use a primitive as type argument for a generic class or method.

**Example:** Generic type arguments

    // error: Type argument cannot be of primitive type
    List<int> list1 = new ArrayList<>();

    // Works fine
    List<Integer> list2 = new ArrayList<>();

(Support for primitives with generics is under way. It _might_ become a reality in something like Java 11. See [JEP 218: Generics over Primitive Types](http://openjdk.java.net/jeps/218).)

### 2. A way to represent "undefined" (nullability)

As opposed to primitive types, a reference can be `null`. This means that using a wrapper type allows you to express things like _"The value is undefined"_, or, _"The value has not yet been loaded"_ without having to reserve a dummy value such as −1.

### 3. APIs requiring reference types

Some APIs require you to work with subtypes of [`Object`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html), i.e. with reference types. [`String.format`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#format-java.lang.String-java.lang.Object...-) and related methods for example.

**Example:**

    // Compiles but doesn't do what you want
    int[] arr1 = { 1, 2, 3 };
    System.out.printf("%d %d %d", arr1);

    // Works as intended
    Integer[] arr2 = { 1, 2, 3 };
    System.out.printf("%d %d %d", arr2);

### 4. The `Number` type

The numeric wrapper types extend [`Number`](https://docs.oracle.com/javase/8/docs/api/java/lang/Number.html):

Object Number Character Boolean Byte Short Integer Long Float Double

This allows you to, for instance, have heterogeneous collections of mixed numbers.

**Example:**

    List<Number> numbers = new ArrayList<>();
    numbers.add(new Integer(10));
    numbers.add(new Double(17.9));

    for (Number n : numbers) {
        System.out.printf("%.2f%n", n.doubleValue());
    }

Another use case is parsing where you don't know the appropriate numeric type in compile time. See for example [`NumberFormat.parse`](https://docs.oracle.com/javase/8/docs/api/java/text/NumberFormat.html#parse-java.lang.String-).

## Autoboxing and unboxing

If a primitive value is provided where a boxed value is expected, the compiler can automatically convert it. This is called **autoboxing**. Same applies if a boxed value is provided where a primitive is expected. This is called **unboxing**.

**Example:** Autoboxing and unboxing

    Integer i = 5;  // autoboxing
    int j = i;      // unboxing

Continue reading here:

<span class="pointer">[Java: Autoboxing and unboxing](autoboxing.html)</span>

## Boxed values and equality

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

To complicate matters further, autoboxing may **cache values**, which causes reference equality to “work” for some values, but not for others. Continue reading here:

<span class="pointer">[Java: Boxed values and equality](boxed-values-equality.html)</span>

## Boxed values are immutable

A boxed value can't be changed. (As seen at the top of this article, the `value` field in the `Integer` class is `final`!) If you want to change an `Integer` variable, you'll have to assign a new reference to it, which points at different boxed value.

**Example:**

    Integer i = new Integer(5);

    // Increment i
    i = new Integer(i.intValue() + 1);

You can in fact do things like `i++` and `i = i + 1`. This however, involves autoboxing/unboxing and in the end the result is semantically equivalent to the above.

The immutability aspect is important, as it makes boxed values safe to use as keys in hash tables.

If you're after the advantages that wrapper types provide, but need **mutability**, then [`AtomicBoolean`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/AtomicBoolean.html), [`AtomicInteger`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/AtomicInteger.html) or [`AtomicLong`](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/AtomicLong.html) _might_ be viable options. Note however that these classes aren't general purpose replacements for the corresponding wrapper classes. They don't, for example, override `equals`. See separate article: [AtomicInteger and equals / Comparable](atomicinteger-equals.html).

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
