<span class="underline"></span>

<span class="underline"></span>

Java Arrays
-----------

1.  [Java Arrays (with examples)](arrays.html)
2.  [Maximum length of array](array-maximum-length.html)
3.  [ArrayIndexOutOfBoundsException](arrayindexoutofboundsexception.html)
4.  [Arrays vs ArrayLists (and other Lists)](array-vs-arraylist.html)
5.  Matrices and Multidimensional Arrays
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

Java: Matrices and Multidimensional Arrays
==========================================

Java does not have “true” multidimensional arrays. Your alternatives are:

-   Arrays of arrays
-   A flattened array
-   A separate class

Details of these three alternatives follow.

Arrays of arrays
----------------

    // Initialized by 3 x 4 zeroes
    int[][] matrix = new int[3][4];

    matrix[0][0] = 17;
    matrix[2][3] = 100;

You can also initialize as follows:

    int[][] matrix = new int[][] {
        { 1, 2, 3 },
        { 4, 5, 6 },
        { 7, 8, 9 }
    };

Or manually:

    int[][] matrix;
    matrix = new int[3][];
    matrix[0] = new int[] { 1, 2, 3 };
    matrix[1] = new int[] { 4, 5, 6 };
    matrix[2] = new int[] { 7, 8, 9 };

For higher dimensional arrays, just add more brackets. For example: `int[][][] cube = new int[3][4][5];`

### Printing

See [Java: Print 2D Matrix](print-2d-matrix.html)

### Beware of the indirection!

Each row is a separate array (object). This means that

-   there's one extra level of indirection, and
-   the matrix can be spread out in memory.

Although arrays are fixed length, nothing protects you from doing

    int[][] matrix = new int[][] {
        { 1, 2, 3 },
        { 4, 5, 6 },
        { 7, 8, 9 }
    };

    // Overwrite second row:
    matrix[1] = new int[] { 0 };

Which would result in a **jagged** array:

    {
        { 1, 2, 3 },
        { 0 },
        { 7, 8, 9 }
    }

Using `final int[][] matrix` won't help, since this would only prevent you from assigning a new value to `matrix` directly. There's no way to express “read only” for array content.

Flattened Arrays
----------------

Another alternative is one array with rows × cols cells:

    int[] matrix = new int[rows * cols];

    // Access element (r,c):
    matrix[r * cols + c] = 123;

Elements are laid out linearly in memory, and there's no risk of ending up with a jagged array.

A Dedicated Class
-----------------

There's no matrix class in the standard API. However, there are plenty of 3rd party libraries that provide such classes. Many of which also include methods for matrix algebra. Here are a few popular ones:

-   [Efficient Java Matrix Library (EJML)](http://ejml.org)
-   [JAMA](https://math.nist.gov/javanumerics/jama/)
-   [Colt](http://dst.lbl.gov/ACSSoftware/colt/)
-   [jblas](https://github.com/mikiobraun/jblas)
-   [JScience](http://jscience.org/)

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
