



## Java Arrays

1.  [Java Arrays (with examples)](arrays.html)
2.  Maximum length of array
3.  [ArrayIndexOutOfBoundsException](arrayindexoutofboundsexception.html)
4.  [Arrays vs ArrayLists (and other Lists)](array-vs-arraylist.html)
5.  [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)
6.  [Appending to an array](array-append.html)
7.  [Copying an array](array-copy.html)
8.  [Inserting an element in an array at a given index](array-insert-at-index.html)
9.  [Testing array equality](testing-array-equality.html)

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

# Java: Maximum length of array

The maximum length of an array in Java is 2,147,483,647 (i.e. the maximum size of an `int`, 2<sup>31</sup> − 1).

This is the **theoretical limit** implied by the fact that the size of an array creation expression must be of type `int`. In practice there are **two additional limits** in effect:

## Available Memory

The entire array is allocated up front, so the size of the array can not exceed the amount of free memory.

## JVM Implementation

Some JVMs reserve a small part of the array for header information, and bail out with an `OutOfMemoryError` for array sizes that are close to the theoretical limit. In the HotSpot VM For example, the [`max_array_length`](https://github.com/openjdk/jdk14u/blob/84917a040a81af2863fddc6eace3dda3e31bf4b5/src/hotspot/share/oops/arrayOop.hpp#L132) function states the following:

    // It should be ok to return max_jint here, but parts of the code
    // (CollectedHeap, Klass::oop_oop_iterate(), and more) uses an int for
    // passing around the size (in words) of an object. So, we need to avoid
    // overflowing an int when we add the header. See CRs 4718400 and 7110613.
    return align_down(max_jint - header_size(type), MinObjAlignment);

This reduces the effective limit to `Integer.MAX_INT - 5`.

You don't always know what JVM your code will be running on, so to be safe you can follow the approach taken in the core libraries and give a little bit more leeway for the JVM. From the [`ArraysSupport`](https://github.com/openjdk/jdk14u/blob/84917a040a81af2863fddc6eace3dda3e31bf4b5/src/java.base/share/classes/jdk/internal/util/ArraysSupport.java#L577) class:

    /**
     * The maximum length of array to allocate (unless necessary).
     * Some VMs reserve some header words in an array.
     * Attempts to allocate larger arrays may result in
     * {@code OutOfMemoryError: Requested array size exceeds VM limit}
     */
    public static final int MAX_ARRAY_LENGTH = Integer.MAX_VALUE - 8;

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
