<span class="underline"></span>

<span class="underline"></span>

## Java Arrays

1.  [Java Arrays (with examples)](arrays.html)
2.  [Maximum length of array](array-maximum-length.html)
3.  [ArrayIndexOutOfBoundsException](arrayindexoutofboundsexception.html)
4.  [Arrays vs ArrayLists (and other Lists)](array-vs-arraylist.html)
5.  [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)
6.  [Appending to an array](array-append.html)
7.  [Copying an array](array-copy.html)
8.  [Inserting an element in an array at a given index](array-insert-at-index.html)
9.  Testing array equality

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

# Java: Testing array equality

    if (Arrays.equals(arr1, arr2)) {
        ...
    }

Note that this performs a **shalow comparison**, i.e. it checks

- `arr1[0].equals(arr2[0])`,
- `arr1[1].equals(arr2[1])`,
- ...

This is **not suitable for multidimensional arrays**.

## Multidimensional arrays

    if (Arrays.deepEquals(arr1, arr2)) {
        ...
    }

This method recurses on the arrays and compares the actual elements.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
