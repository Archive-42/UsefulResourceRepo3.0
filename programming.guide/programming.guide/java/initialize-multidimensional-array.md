



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

# Java: Initializing a multidimensional array

☞

Java has no built-in support for “true” multidimensional arrays, only **arrays of arrays**. See this article for the difference: [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html)

You can declare and allocate a multidimensional array, as follows (note that it's **automatically initialized with zeroes**):

    // A 2×3×4 array, initialized with zeroes:
    int[][][] multidim = new int[2][3][4];

You can also declare and initialize as follows:

    // A 2×3×4 multidimensional array:
    int[][][] multidim = {
        {
            {  1,  2,  3,  4},
            {  5,  6,  7,  8},
            {  9, 10, 11, 12}
        },
        {
            { 13, 14, 15, 16},
            { 17, 18, 19, 20},
            { 21, 22, 23, 24}
        }
    };

Here's how to first allocate the array, then initialize with loops:

    // A 2×3×4 multidimensional array:
    int[][][] multidim = new int[2][3][4];

    // Fill it with the value 10
    for (int i = 0; i < multidim.length; i++) {
        for (int j = 0; j < multidim[i].length; j++) {
            for (int k = 0; k < multidim[i][j].length; k++) {
                multidim[i][j][k] = 10;
            }
        }
    }

## See also

- [Matrices and Multidimensional Arrays](matrices-and-multidimensional-arrays.html) (Includes more details on multidimensional arrays in Java)
- [Print 2D Matrix](print-2d-matrix.html)

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
