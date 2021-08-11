<span class="underline"></span>

<span class="underline"></span>

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

Java: Print 2D Matrix
=====================

Quick and dirty one-liner
-------------------------

    int[][] matrix = {
        {   5,   8,   13 },
        { -21,  34,   55 },
        {  89, 144, -233 }
    };

    System.out.println(Arrays.deepToString(matrix));

Result

    [[5, 8, 13], [-21, 34, 55], [89, 144, -233]]

With new lines
--------------

    for (int[] row : matrix) {
        System.out.println(Arrays.toString(row));
    }

Result

    [5, 8, 13]
    [-21, 34, 55]
    [89, 144, -233]

Right justified (padded) columns
--------------------------------

    void printMatrix(int[][] matrix) {
        int cols = matrix[0].length;
        int[] colWidths = new int[cols];
        for (int[] row : matrix) {
            for (int c = 0; c < cols; c++) {
                int width = String.valueOf(row[c]).length();
                colWidths[c] = Math.max(colWidths[c], width);
            }
        }
        for (int[] row : matrix) {
            for (int c = 0; c < cols; c++) {
                String fmt = String.format("%s%%%dd%s",
                        c == 0 ? "|" : "  ",
                        colWidths[c],
                        c < cols - 1 ? "" : "|%n");
                System.out.printf(fmt, row[c]);
            }
        }
    }

Result

    |  5    8    13|
    |-21   34    55|
    | 89  144  -233|

Decimal points aligned
----------------------

    void printMatrix(double[][] matrix) {
        int cols = matrix[0].length;
        int[] iWidths = new int[cols];
        int[] fWidths = new int[cols];
        for (double[] row : matrix) {
            for (int c = 0; c < cols; c++) {
                String[] parts = String.valueOf(row[c]).split("\\.");
                iWidths[c] = Math.max(iWidths[c], parts[0].length());
                fWidths[c] = Math.max(fWidths[c], parts[1].length());
            }
        }
        for (double[] row : matrix) {
            for (int c = 0; c < cols; c++) {
                String[] parts = String.valueOf(row[c]).split("\\.");
                int lp = iWidths[c] - parts[0].length();
                int rp = fWidths[c] - parts[1].length();
                String fmt = String.format("%s%%%ss%%s.%%s%%%ss%s",
                        c == 0 ? "|" : "  ",
                        lp == 0 ? "" : lp,
                        rp == 0 ? "" : rp,
                        c < cols - 1 ? "" : "|%n");
                System.out.printf(fmt, "", parts[0], parts[1], "");
            }
        }
    }

Result

    |  5.55    8.333    13.555|
    |-21.0    34.1      55.3  |
    | 89.2   144.5    -233.3  |

Looking for another variant? Please post a comment.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
