<span class="underline"></span>

<span class="underline"></span>

Java Arrays
-----------

1.  [Java Arrays (with examples)](arrays.html)
2.  [Maximum length of array](array-maximum-length.html)
3.  [ArrayIndexOutOfBoundsException](arrayindexoutofboundsexception.html)
4.  Arrays vs ArrayLists (and other Lists)
5.  [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)
6.  [Appending to an array](array-append.html)
7.  [Copying an array](array-copy.html)
8.  [Inserting an element in an array at a given index](array-insert-at-index.html)
9.  [Testing array equality](testing-array-equality.html)

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

[**See all 190 Java articles**](index.html)

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

Java: Arrays vs ArrayLists (and other Lists)
============================================

An array (something like `int[]`) is a **built in type** while [`ArrayList`](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html) is a regular class part of the **Java standard library**.

When to use which?
------------------

Sometimes you **must** use an array. For example:

-   An API method takes an array as argument or returns an array
-   You need to work with primitives for performance reasons

Unless you have a specific reason to use an array (such as those mentioned above), use a [`List`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html), such as an [`ArrayList`](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html).

Resizing
--------

Once you've created an array, it **can't be resized**. You can for instance not append an element to the end of an array, or remove an element.

Most list types (including `ArrayList`) provide [`List.add`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html#add-E-) and [`List.remove`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html#remove-int-) which allows it to **grow and shrink**.

Insertion
---------

Both arrays and lists allow you to update the content at a specific index.

    arr[5] = 17;
    list.set(5, 17);

Lists however, also allows you to **insert** an element in the middle, shifting all subsequent elements from index *i* to *i* + 1.

    list.add(5, 17);  // insert 17 at index 5

Primitives
----------

An arrray can store primitive values. Lists can not. You can have a `List` of integers, but you'll have to use `List<Integer>`. `List<int>` doesn't work. (Support for this is under way and *might* be available in something like Java 13. See [JEP 218: Generics over Primitive Types](http://openjdk.java.net/jeps/218).)

**Autoboxing:** Luckily there's something called *autoboxing* which silently transforms an `int` to an `Integer` behind the scenes. So despite the fact that a `List` can only hold `Integer` values, we can still use `list.add(5)`, i.e. we don't have to write `list.add(new Integer(5))`.

Generic elements
----------------

You can't create an array of generic elements. This won't compile:

    // Error: generic array creation
    Set<String>[] sets = new Set<String>[3];

This however works fine:

    List<Set<String>> sets = new ArrayList<Set<String>>();

There is however a simple workaround for the array case. See [Java: Generic array creation](generic-array-creation.html).

Immutability
------------

There's no way to make the elements of an array "final". If you write for instance

    final int[] arr = { 1, 2, 3 };

Something like `arr[1] = 77` is still allowed.

Element immutability can be achieved for lists by doing:

    List<Integer> list = Collections.unmodifiableList(Arrays.asList(1, 2, 3));

Covariance
----------

A `String[]` is a subtype of `Object[]`. This allows us to write:

    String[] strings = new String[1];
    Object[] objects = strings;
    objects[0] = new Object();

Although it throws an exception when executed!

A `List<String>` is however **not** a subtype of a `List<Object>`. This for example does not compile:

    List<String> strings = new ArrayList<>();
    List<Object> objects = strings;  // Error: Incompatible types
    objects.add(new Object());

Put in fancy computer science terms: Arrays are covariant, while lists are not.

List methods
------------

You can't use `List` methods on arrays… **WRONG**. There's in fact a bridge from the array world over to the `List` world. The bridge is called [`Arrays.asList`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#asList-T...-). This method returns a `List` implementation backed by the provided array, which means that modifications to the list affect the original array.

Here's an example using `List.replaceAll` on an array:

    String[] strs = { "a", "b", "c", "d" };
    Arrays.asList(strs).replaceAll(s -> s + s);
    // strs == { "aa", "bb", "cc", "dd" }

Note however, that since the backing array can't shrink or grow, operations such as `List.add` will throw `UnsupportedOperationException`.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
