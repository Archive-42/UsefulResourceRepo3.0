<span class="underline"></span>

<span class="underline"></span>

## Java Arrays

1.  [Java Arrays (with examples)](arrays.html)
2.  [Maximum length of array](array-maximum-length.html)
3.  ArrayIndexOutOfBoundsException
4.  [Arrays vs ArrayLists (and other Lists)](array-vs-arraylist.html)
5.  [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)
6.  [Appending to an array](array-append.html)
7.  [Copying an array](array-copy.html)
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

# Java: ArrayIndexOutOfBoundsException

An `ArrayIndexOutOfBoundsException` is thrown when the program tries to access an element at an invalid index.

The array indexes are **zero-based**, so for an array with _N_ elements (`array.length == N`) the valid indexes are <span class="no-wrap">0…*N* − 1</span>.

**Example:** For an array created like this:

    int[] arr = { 17, 55, 2, 10 };

the memory looks like this:

−3 −2 −1 17 0 55 1 2 2 10 3 4 5 6 Index: Valid indexes

That is, with **4 elements**, the greatest valid index is **3**.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
