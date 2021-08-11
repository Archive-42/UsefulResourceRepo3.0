## Java Arrays

1.  Java Arrays (with examples)
2.  [Maximum length of array](array-maximum-length.html)
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

# Java Arrays (with examples)

    int[] arr = new int[5];

    arr[0] = 5;
    arr[3] = 2;

    // arr == [ 5, 0, 0, 2, 0 ]

- Arrays have **fixed length**. Once created, they can not be resized.
- In an array of length 10, the first index is 0 and the last is 9.
- Arrays are **objects**
  - They are dynamically allocated
  - They live on the heap
  - Array variables are of reference type

Arrays are to be considered a low level language feature. In 99 cases out of 100 you'll want to use a [`List`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html). See [Java: Array vs ArrayList](array-vs-arraylist.html).

## Three ways to create an array

    // Short form
    // (can only be used as initializer in a declaration)
    int[] arr1 = { 1, 2, 77 };

    // Initialize with 10 zeroes
    int[] arr2 = new int[10];

    // General form
    int[] arr3 = new int[] { 1, 2, 77 };

**Note:** It's possible to put the brackets after the identifier:

    int arr[] = { 1, 2, 3 };

This format is rarely used and discouraged by most style guides.

## Accessing Elements

Since indexes start at 0, you write for example `arr[2]` to access the **third** element of `arr`. In an array with _n_ elements, the last valid index is *n* − 1.

If you try to access an element at a **negative index** or an index **greater than or equal to the length** of the array, an [`ArrayIndexOutOfBoundsException`](https://docs.oracle.com/javase/8/docs/api/java/lang/ArrayIndexOutOfBoundsException.html) will be thrown.

## Length

To get the length of an array, `arr`, use `arr.length`.

The length is represented by an `int` which means the maximum length is 2<sup>31</sup> − 1 ([`Integer.MAX_VALUE`](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#MAX_VALUE)).

## Iterating

Arrays can be used in enhanced for loops:

    for (int element : arr) {
        System.out.println(element);
    }

If you need to keep track of the index, use a traditional `for` loop:

    for (int i = 0; i < arr.length; i++) {
        System.out.println("Index " + i + ": " + arr[i]);
    }

For more details on loops, see: [Java Trail: Loops](loops.html)

## Printing

`System.out.println(arr)` prints something like `[I@3af49f1c`. Here's a better way:

    int[] arr = { 1, 2, 77 };
    System.out.println(Arrays.toString(arr));

    // Output: [1, 2, 77]

## Primitives vs objects (references)

Arrays are layed out linearly in memory. In other words, an `int[]` looks like this:

int\[\]: 3 1 15 8 11

In Java, object variables actually store references (see [Java: Primitives vs Objects and References](primitives-vs-objects-references.html)), so for a `Person[]` array, the picture looks like this:

Person\[\]: name: John age: 19 name: Bob age: 55 name: Amy age: 25 name: Eve age: 29

The references are stored linearly, but the actual objects are spread out in memory.

## Multidimensional arrays

Java does not have "true" multidimensional arrays. Instead you typically use arrays of arrays:

    int[][] matrix = new int[3][5];
    matrix[0][0] = 123;
    matrix[2][4] = 321;

For more details see: [Java: Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)

## Comments

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
