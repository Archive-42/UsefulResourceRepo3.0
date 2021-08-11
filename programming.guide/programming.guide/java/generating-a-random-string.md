



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

# Java: Generating a random String (password, booking reference, etc)

If this is intended to be used as a password generator, make sure to use [`SecureRandom`](https://docs.oracle.com/javase/8/docs/api/java/security/SecureRandom.html) instead of [`Random`](https://docs.oracle.com/javase/8/docs/api/java/util/Random.html) in the examples below. You might also want to [use `char[]` instead of `String`](http://stackoverflow.com/questions/8881291) for storing the result.

## Random string

    int length = 8;
    String chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
                 + "abcdefghijklmnopqrstuvwxyz"
                 + "0123456789";
    String str = new Random().ints(length, 0, chars.length())
                             .mapToObj(i -> "" + chars.charAt(i))
                             .collect(Collectors.joining());

## With at least 1 digit and 1 special character

    int length = 8;
    String digits = "0123456789";
    String specials = "~=+%^*/()[]{}/!@#$?|";
    String all = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
               + "abcdefghijklmnopqrstuvwxyz"
               + digits + specials;
    Random rnd = new Random();
    List<String> result = new ArrayList<>();
    Consumer<String> appendChar = s ->
            result.add("" + s.charAt(rnd.nextInt(s.length())));
    appendChar.accept(digits);
    appendChar.accept(specials);
    while (result.size() < length)
        appendChar.accept(all);
    Collections.shuffle(result, rnd);
    String str = String.join("", result);

## Apache Commons Lang

See also the various methods in [`RandomStringUtils`](https://commons.apache.org/proper/commons-lang/javadocs/api-3.8/org/apache/commons/lang3/RandomStringUtils.html) from Apache Commons Lang:

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><tbody><tr class="odd"><td><code>random(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="even"><td><pre><code>random(int count,
       boolean letters,
       boolean numbers)</code></pre></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>random(int count,
       char... chars)</code></pre></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="even"><td><pre><code>random(int count,
       int start,
       int end,
       boolean letters,
       boolean numbers)</code></pre></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>random(int count,
       int start,
       int end,
       boolean letters,
       boolean numbers,
       char... chars)</code></pre></td><td>Creates a random string based on a variety of options, using default source of randomness.</td></tr><tr class="even"><td><pre><code>random(int count,
       int start,
       int end,
       boolean letters,
       boolean numbers,
       char[] chars,
       Random random)</code></pre></td><td>Creates a random string based on a variety of options, using supplied source of randomness.</td></tr><tr class="odd"><td><pre><code>random(int count,
       String chars)</code></pre></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="even"><td><code>randomAlphabetic(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>randomAlphabetic(
        int minLengthInclusive,
        int maxLengthExclusive)</code></pre></td><td>Creates a random string whose length is between the inclusive minimum and the exclusive maximum.</td></tr><tr class="even"><td><code>randomAlphanumeric(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>randomAlphanumeric(
        int minLengthInclusive,
        int maxLengthExclusive)</code></pre></td><td>Creates a random string whose length is between the inclusive minimum and the exclusive maximum.</td></tr><tr class="even"><td><code>randomAscii(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>randomAscii(
        int minLengthInclusive,
        int maxLengthExclusive)</code></pre></td><td>Creates a random string whose length is between the inclusive minimum and the exclusive maximum.</td></tr><tr class="even"><td><code>randomGraph(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>randomGraph(
        int minLengthInclusive,
        int maxLengthExclusive)</code></pre></td><td>Creates a random string whose length is between the inclusive minimum and the exclusive maximum.</td></tr><tr class="even"><td><code>randomNumeric(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>randomNumeric(
        int minLengthInclusive,
        int maxLengthExclusive)</code></pre></td><td>Creates a random string whose length is between the inclusive minimum and the exclusive maximum.</td></tr><tr class="even"><td><code>randomPrint(int count)</code></td><td>Creates a random string whose length is the number of characters specified.</td></tr><tr class="odd"><td><pre><code>randomPrint(
        int minLengthInclusive,
        int maxLengthExclusive)</code></pre></td><td>Creates a random string whose length is between the inclusive minimum and the exclusive maximum.</td></tr></tbody></table>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
