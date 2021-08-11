<span class="underline"></span>

<span class="underline"></span>

Types in Java
-------------

1.  Java Basics: Types
2.  [Primitive Types](primitive-types.html)
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

Java Basics: Types
==================

A computer only knows about ones and zeros (*bits*). Still, it's able to tell you 1+1 equals **2**. How is that possible?

`11100010010011011001010011111010001010`  
`10001100101001111111110111000101000110`  
`10010010010001101110110101100110011100`  
`10110110110010011101111000201100110111`  
`10001000101000100110111010011110110101`

The answer is that it can put many bits together and **interpret** them as something else. `1100001` for example can be interpreted as a number in base 2: `97`. The curious part is that the same bits can just as well be interpreted as an ASCII character, in which case they represent the letter `a`!

So, if I have a variable containing `1100001`, what does it represent? The letter `a` or `97`?!

Here's where **types** come in. Each variable has a type associated with it, which specifies how its data should be interpreted.

**Example:** Declaration of two variables: `i` and `c`

    int  i = 0b1100001; // interpret as an integer
    char c = 0b1100001; // interpret as a character

    System.out.println(i); // prints 97
    System.out.println(c); // prints 'a'

Type Checking
-------------

Since the computer knows how to interpret the data, it can check whether or not the program treats the data sensibly. For example, multiplying an integer with a boolean value (true/false) doesn't make sense. If you try to do so you get a **type error**.

**Example:** A type error

    int i = 5;
    boolean b = true;
    System.out.println(i * b);

    // Error: Operator '*' cannot be
    // applied to 'int', 'boolean'

Parts of the Java type system is quite complicated. Some type errors are in fact so complicated that even experienced programmers have trouble deciphering the meaning.

Dynamic vs Static Typing
------------------------

Some programming languages (Python, JavaScript, PHP, …) lets you run code containing type errors, and doesn't complain unless the faulty instruction is actually executed. This is called **dynamic typing**. Others, like Java (and C, C++, Scala, …), refuses to even start executing code that contain a type error. This is called **static typing**.

**Example:** Valid Python code

    print("Begin")
    if False:
        print("2" / 2)
    print("End")

**Example:** Invalid Java code

    System.out.println("Begin");
    if (false)
        System.out.println("2" / 2);
    System.out.println("End");

The static approach trades some flexibility for robustness: It's more restrictive in terms of what's acceptable to write, but a program that passes compilation is guaranteed to be free of a whole class of common errors.

Weak vs Strong Typing
---------------------

In some programming languages (like JavaScript or Perl) the type of a value is determined by how it's used. If you for instance do `if (x) …`, then `x` is treated as a boolean, but if you do `y = x * 5`, then `x` is treated as a number. This is called **weak typing**.

In other languages, like Java, it's the other way around: The type determines what you can do with a value. If, for example, the type of `x` is a number, then `if (x) …` will result in a compilation error. This is called **strong typing**.

Primitive vs Reference Types
----------------------------

Java provides 8 built-in **primitive types** and lets you define your own custom **reference types**.

### Primitive Types

The primitive types are:

-   Integers
    -   `byte` (−128–127)
    -   `short` (±32 thousand)
    -   `int` (±2 billion)
    -   `long` (±9 quintillion)
-   Reals
    -   `float` (~6 digits precision)
    -   `double` (~15 digits precision)
-   `char` (unicode characters: `a` `5`, `ξ`, `♪`, …)
-   `boolean` (true/false)

Java is able to convert between some of these types automatically, but apart from that, they have nothing in common.

Further details: [Java: Primitive Types](primitive-types.html)

### Reference Types

Sometimes simple numbers and characters aren't enough. You may want your data to represent products, people, buttons, etc. For these situations we have **classes**. Classes can be thought of as blueprints for **objects**. Classes and objects are the foundation of what is called Object Oriented Programming and is a whole topic of it's own. In this article we'll just cover the basics and refer to other articles for details.

**Example:** Here's a `Person` class with variables, or *fields*, for name and age

    class Person {
        String name;
        int age;
    }

This class can be used as follows:

    Person me = new Person();
    me.name = "Andreas";
    me.age = 34;

In the above snippet the type of the `me` variable is `Person` which means it contains references to `Person` objects. Doing something like `me = new Banana();` would give a type error.

What's important in regards to Javas type system is the fact that all classes are arranged in a **class hierarchy**. Classes like `Banana` or `Apple` could for example be subclasses of `Fruit`. The `Fruit` class could in turn be a subclass of something like `Edible`.

Object Edible Banana Apple

At the top of this hierarchy we have a class called `Object` which has special status in the language. It is for example what you implicitly subclass if you don't explicitly specify anything else. Unlike C++, the hierarchy forms a proper tree; Each class has precisely one "parent" class.

If you have a variable of type `Fruit`, you could assign a `Banana`, or an `Apple` reference to it.

**Example:**

    Fruit toEat = new Banana();

    // Changed my mind
    toEat = new Apple();

It would however be an error to try to assign a `Car` reference to the `toEat` variable, since a `Car` is not a `Fruit`.

**Example:**

    Fruit toEat = new Car();
    // error: incompatible types: Car cannot be converted to Fruit

Finally, a slighly more intricate example:

**Example:**

    Edible e = new Banana();
    Fruit toEat = e;
    // error: incompatible types: Edible cannot be converted to Fruit

Looking at the snippet as a whole, it's clear that the second assignment is safe. The type checker however has a quite narrow field of view, and looks at each assignment in isolation. In the last assignment it refuses to let us assign an arbitrary `Edible` to a `Fruit`. It basically want's to play it safe and make sure we don't assign something like a `Cake` reference to a `Fruit` variable.

What's different here compared to the example where we tried to assign a `Car` to a `Fruit` is that an `Edible` *could conceivably* contain a valid `Fruit` reference. While the type checker won't allow it by default, you can force it through with a **cast** as explained in the next section.

  
**Further Reading:** [Java: Primitives vs Objects and References](primitives-vs-objects-references.html).

Conversions
-----------

Java allows you to convert between types that are similar. There are different ways such conversions can be expressed.

### Explicit Casts

You can tell the compiler to reinterpret the data by doing an explicit cast. The syntax is `(TargetType) expression`.

**Example:** Reinterpret an `int` as a `char`

    int i = 97;
    char c = (char) i; // cast from int to char
    // c == 'a'

Perhaps more common is to use casts with reference types. As mentioned earlier, it might for example make sense to force an `Edible` into a `Fruit`.

**Example:** Downcast

    Edible e = …
    if (e instanceof Fruit) {
        Fruit fruit = (Fruit) e;
        System.out.println(fruit.getNumSeeds());
    }

If the cast is illegal, i.e. if you try to cast a `Cake` into a `Fruit` you would get a `ClassCastException`.

**Example:** Illegal cast (runtime)

    Edible e = new Cake();
    Fruit f = (Fruit) e;

Result:

    Exception in thread "main" java.lang.ClassCastException: Cake cannot be cast to Fruit

If the `e` variable was of type `Integer` the compiler would even reject the program, since it's *guaranteed* that it would give an error when executed.

**Example:** Illegal cast (compile time)

    Integer e = 5;
    Fruit f = (Fruit) e;
    // incompatible types: Integer cannot be converted to Fruit

### Implicit Widening

A `long` can store all `int` values and then some. It has a "wider" range. Therefore it's always safe to assign an `int` value to a `long` variable, thus the compiler will do some conversion implicitly for you.

**Example:** <span markdown="1">Widening from `int` to `long`</span>

    int i = 1147;
    long l = i; // no explicit cast needed

Similarly, a `byte` can be widened to a `short` or an `int`, a `float` to a `double` and so on.

### Narrowing

In cases where it's clearly safe, the compiler will implicitly perform the opposite conversion as well. A numeric literal such as `7` is for example strictly speaking an `int`. Since it fits in a `byte` the compiler converts it for you.

**Example:** <span markdown="1">Narrowing from `int` to `byte`</span>

    byte b = 7; // no explicit cast needed

### Boxing

Each primitive type (`byte`, `int`, `double`, …) has a corresponding wrapper class called the boxed type (`Byte`, `Integer`, `Double`, …). Java can automatically convert between the two forms. This is called **autoboxing** and **unboxing**

**Example:** Autoboxing / unboxing

    int i = 7;

    // Automatically box an int into an Integer
    Integer j = i;

    // Unbox j, perform addition, box result
    Integer k = j + 5;

Continue reading here:

<span class="pointer">[Java: Autoboxing / unboxing](autoboxing.html)</span>

### Promotion

Promotion is a collective name for widening and unboxing conversions. For example, `+` is defined for `int`, `float` and `double` operands. If you add two `byte` variables together, they are first **promoted** to `int` values.

**Example:** Promotion of variables:

    Byte b1 = 7;
    byte b2 = 8;
    int i = b1 + b2; // i == 15

    short s1 = 5;
    short s2 = 7;
    short s3 = s1 + s2; // error: incompatible types: possible
                        // lossy conversion from int to short

Summary
-------

-   Types give meaning to data
-   All variables (and expressions) have a type
-   The entire program must be free of type errors for it to be compiled and executed
-   There are 8 different primitive types representing numbers, characters and booleans
-   Classes are arranged in a hierrachy
-   Sometimes you're allowed to convert the type of the data from one type to another

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
