<span class="underline"></span>

<span class="underline"></span>

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

# Java: Generating a random number of a certain length

To generate a random number with, for example 5 digits, you can do:

    int n = 10000 + new Random().nextInt(90000);
    // 10000 ≤ n ≤ 99999

Since the upper bound given to [`nextInt`](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html#nextInt-int-) is exclusive, the maximum is indeed 99999.

## Generalized version

    // Generates a random int with n digits
    public static int generateRandomDigits(int n) {
        int m = (int) Math.pow(10, n - 1);
        return m + new Random().nextInt(9 * m);
    }

**Warning:** The above method breaks for _n_ &gt; 9, since 10<sup>9</sup> is the largest power of 10 that an int can store.

## More than 9 digits

You can adapt the above method to work with `long`. This would get you up to 18 digits.

Alternatively you can work with strings. See this article: [Generating a random String (password, booking reference, etc)](generating-a-random-string.html). The resulting string can be converted to a `BigDecimal` if needed.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
