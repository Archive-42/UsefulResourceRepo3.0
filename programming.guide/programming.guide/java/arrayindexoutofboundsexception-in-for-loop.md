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

# Java: ArrayIndexOutOfBoundsException in for loop

☞

Array indexes are **zero-based**.

The last valid index for an array of **_N_ elements** is <span class="no-wrap">***N* − 1**</span>.

You have most likely written…

    for (int i = 0; i <= arr.length; i++) {
        something(arr[i]);
    }

…where it sohuld be

    for (int i = 0; i < arr.length; i++) {
        something(arr[i]);
    }

## ArrayIndexOutOfBoundsException

An `ArrayIndexOutOfBoundsException` is thrown when the program tries to access an element at an invalid index.

The array indexes are **zero-based**, so for an array with _N_ elements (`array.length == N`) the valid indexes are <span class="no-wrap">0…*N* − 1</span>.

**Example:** For an array created like this:

    int[] arr = { 17, 55, 2, 10 };

the memory looks like this:

−3 −2 −1 17 0 55 1 2 2 10 3 4 5 6 Index: Valid indexes

That is, with **4 elements**, the greatest valid index is **3**.

## Comments

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
