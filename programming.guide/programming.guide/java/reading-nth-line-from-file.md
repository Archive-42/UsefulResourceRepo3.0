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

Java: Reading the Nth line from a file
======================================

Here's how to retrieve a line at a specific line number from a file.

For **small files**:

    String line = Files.readAllLines(Paths.get("file.txt")).get(n);

For **large files**:

    String line;
    try (Stream<String> lines = Files.lines(Paths.get("file.txt"))) {
        line = lines.skip(n).findFirst().get();
    }

Java 7
------

    String line;
    try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
        for (int i = 0; i < n; i++)
            br.readLine();
        line = br.readLine();
    }

Comments (2)
------------

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

Why do you call `br.readLine()` twice?

<span style="color: grey">by Anonymous | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

The `br.readLine()` in the for loop discards lines. The second `br.readLine()` reads the line we're interested in.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
