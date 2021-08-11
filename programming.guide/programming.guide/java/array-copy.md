<span class="underline"></span>

<span class="underline"></span>

## Java Arrays

1.  [Java Arrays (with examples)](arrays.html)
2.  [Maximum length of array](array-maximum-length.html)
3.  [ArrayIndexOutOfBoundsException](arrayindexoutofboundsexception.html)
4.  [Arrays vs ArrayLists (and other Lists)](array-vs-arraylist.html)
5.  [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)
6.  [Appending to an array](array-append.html)
7.  Copying an array
8.  [Inserting an element in an array at a given index](array-insert-at-index.html)
9.  [Testing array equality](testing-array-equality.html)

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

[**See all 190 Java articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

# Java: Copying an array

Copying an array is one of the few situations where [`Object.clone`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#clone--) is a good choice.

    int[] original = { 10, 20, 30 };

    int[] copy = original.clone();

It works for object arrays as well, but note that it makes a **shallow copy**; the objects are not copied, only the references. See [Shallow vs Deep Copy](../shallow-vs-deep-copy.html). If you need to make a deep copy, you have to create a copy constructor or resort to [`Object.clone`](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html#clone--) (but read [this](https://stackoverflow.com/q/4081858/276052) first).

To wrap up, here are some alternative ways to do a shallow copy…

## System.arraycopy

    int[] copy = new int[original.length];
    System.arraycopy(original, 0, copy, 0, original.length);

## Arrays.copyOf

    int[] copy = Arrays.copyOf(original, original.length);

## Commons Lang

    int[] copy = ArrayUtils.clone(original);

## Stream API

    int[] copy = IntStream.of(original).toArray();

    // Or, for reference types
    String[] strs = Stream.of(original).toArray(String[]::new);

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
