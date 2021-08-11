<span class="underline"></span>

<span class="underline"></span>

Types in Java
-------------

1.  [Java Basics: Types](types.html)
2.  [Primitive Types](primitive-types.html)
3.  Primitives vs Objects and References
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

Java: Primitives vs Objects and References
==========================================

**Examples of primitive values**

-   The integer 5
-   The floating point value 3.2
-   true
-   The character 'c'

**Examples of objects**

-   A person
-   A date
-   The string "Hello"
-   A list

You could view primitive values as actual data, and objects as containers of data. If primitive values where atoms, objects would be molecules.

Objects and primitive values have types. There are 8 **primitive types** in Java:

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

All other types (`String`, `List`, `YourCustomClass`, …) are **reference types**.

**Important:** Note that it's called *reference types* and not *object types*. In Java you never work with objects directly; you always work with references (“pointers”) to objects.

Example
-------

By running this snippet of code…

    int i = 17;
    Person p = new Person();
    p.age = 34;

…you would end up with memory looking something like:

i 17 p … … age 34 …

`i`, which is of primitive type `int` holds some data, and `p`, which is of reference type, holds a reference to some data.

How data is passed around
-------------------------

<span class="small">The topic discussed below is a source of a lot of confusion, yet very important to fully understand. Read carefully!</span>

First, two examples of what is meant by data being "passed around":

    someMethod(x); // content of x is passed to someMethod
    y = x;         // content of x is passed (copied) to y

There are three separate things involved here:

-   Primitive values
-   References to objects
-   Objects

When you create an object all you get is a reference to it. There's no way to "pull the thread" and get hold of the actual object it points at. Since you can't get hold of objects, you can't pass them around! That's right, you can never pass an object as argument to a method! When people (sloppily) say that an object is passed to a method, what they mean is that *a reference pointing at an object* is passed to the method.

**Key fact 1:**  
Objects aren't passed around at all.

Primitive values and references on the other hand *are* passed around, and both are treated the same way. If you call `method(x)` it behaves precisely the same regardless if `x` is of primitive type or of reference type: The content of `x` (whether it's an integer, a boolean value or a reference to an object) is copied and passed as argument to the method.

In programming lingo, "passing a copy of the content of a variable" is called *pass by value*.

**Key fact 2:**  
Primitives and references are passed by value.

So, if someone says to you *"Objects are passed by reference"* (which is indeed a common misconception), you should reply with, *"No, objects aren't passed around at all. **References** are passed around, and they are passed around **by value**."*

If they continue to argue with you, just say you learned it first hand from someone with a PhD in theoretical computer science that have spent three years at Oracle developing the Java compiler.

That being said, there's an important final point to be made. When a reference is passed to a method, only the reference is copied, *not the object*. In other words, you'll have two references pointing at the same object. If you for instance have the following method…

    void someMethod(Person x) {
        x.name = "Andreas";
    }

…and do…

    Person p = new Person();
    p.name = "John";
    someMethod(p);
    System.out.println(p.name);

…it will print `Andreas`. If this surprises you, recall that `p` contains a reference to the `Person` object, and that when you call `someMethod(p)` this reference is passed on, and when the method uses it, it still points at the original object.

**Key fact 3:**  
If a method modifies an object, the modification is visible outside that method.

Comparison to C/C++
-------------------

Objects can *only* be created using the `new` keyword. Primitive types such as `int` can *not* be created using the `new` keyword.

Semantically Java references are similar to C/C++ pointers.

Syntactically Java references are similar to C++ references.

<table><thead><tr class="header"><th></th><th>Java references</th><th>C/C++ pointers</th><th>C++ references</th></tr></thead><tbody><tr class="odd"><td>Points at objects</td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: green">Yes</span></td></tr><tr class="even"><td>Initialized with <code>new</code></td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: red">No</span></td></tr><tr class="odd"><td>Can be null</td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: red">No</span></td></tr><tr class="even"><td>Can be updated to point at a different object</td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: red">No</span></td></tr><tr class="odd"><td>Pass by value</td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: red">No</span></td></tr><tr class="even"><td>Is called "reference"</td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: red">No</span></td><td><span style="font-weight: bold; color: green">Yes</span></td></tr><tr class="odd"><td>Is implicitly dereferenced</td><td><span style="font-weight: bold; color: green">Yes</span></td><td><span style="font-weight: bold; color: red">No</span></td><td><span style="font-weight: bold; color: green">Yes</span></td></tr></tbody></table>

Comments (2)
------------

![User avatar](https://www.gravatar.com/avatar/e8696ad98ef2a6410755faafd35e9d0d?d=mp)

Thank you! Very helpful! Could you give a code example of a method which accepts not a `Person` reference, but a primitive data type `someMethod(int a)`. Is the value going to change outside the method?

<span style="color: grey">by Ktisin | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

The argument would *not* be changed outside the method. The method would work with a copy of the argument. (See paragraph below Key Fact 1.) Note that this is true also for references; references are copied too.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
