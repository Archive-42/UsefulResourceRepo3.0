



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

# Java: Generating a random char (a-z)

A random character between `'a'` and `'z'`:

    Random rnd = new Random();
    char c = (char) ('a' + rnd.nextInt(26));

A random character from a string of characters:

    String chars = "abcxyz";
    Random rnd = new Random();
    char c = chars.charAt(rnd.nextInt(chars.length()));

## Explanation

Every character corresponds to a number (a code point).

97 for example corresponds to `a`, and we can convert between the two easily:

    char c = (char) 97;  // c == 'a'
    int i = 'a';         // i == 97

So all we have to do is to come up with a random number between 97 (‘a’) and 122 (‘z’) and convert that number to a character.

This is done like so:

    int randomNumber = 97 + rnd.nextInt(26);

We can replace `97` with ‘a’…

    int randomNumber = 'a' + rnd.nextInt(26);

…and convert to char on the same line

    char randomChar = (char) ('a' + rnd.nextInt(26));

## See also

- [Converting a char to an int](converting-char-to-int.html)
- [Random with a random seed](random-seed.html)
- [Generating a random String (password, booking reference, etc)](generating-a-random-string.html)

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
