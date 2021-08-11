



## Java Arrays

1.  [Java Arrays (with examples)](arrays.html)
2.  [Maximum length of array](array-maximum-length.html)
3.  [ArrayIndexOutOfBoundsException](arrayindexoutofboundsexception.html)
4.  [Arrays vs ArrayLists (and other Lists)](array-vs-arraylist.html)
5.  [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)
6.  [Appending to an array](array-append.html)
7.  [Copying an array](array-copy.html)
8.  Inserting an element in an array at a given index
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

# Java: Inserting an element in an array at a given index

In Java arrays can't grow, so you need to create a **new array**, larger array, copy over the content, and insert the new element.

**Example:** Insert `30` in `arr` at index `2`

    int[] arr = { 10, 20, 40, 50 };

    arr = Arrays.copyOf(arr, arr.length + 1);
    System.arraycopy(arr, i, arr, i + 1, arr.length - i - 1);
    arr[i] = 30;

    // arr == [ 10, 20, 30, 40, 50 ]

## Apache Commons Lang

If you have [Commons Lang](https://commons.apache.org/proper/commons-lang/) on your class path, you can use one of the [`ArrayUtils.insert`](https://commons.apache.org/proper/commons-lang/apidocs/org/apache/commons/lang3/ArrayUtils.html#insert-int-int:A-int...-) methods.

**Example:** Insert `30` in `arr` at index `2`

    int[] arr = { 10, 20, 40, 50 };

    arr = ArrayUtils.insert(2, arr, 30);

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
