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

# Java Stack Traces: Unknown Source

If you get a stack trace with "Unknown Source" like below…

    Exception in thread "main" java.lang.NumberFormatException: For input string: "3.1415"
            at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
            at java.lang.Integer.parseInt(Integer.java:580)
            at ExampleCli.parseNumericArgument(Unknown Source)
            at ExampleCli.parseCliOptions(Unknown Source)
            at ExampleCli.main(Unknown Source)

…it means that the program lacks the relevant **debugging information**. Specifically the class files are missing the `LineNumberTable` attribute ([JVMS 4.7.12](https://docs.oracle.com/javase/specs/jvms/se8/html/jvms-4.html#jvms-4.7.12)).

## Possible reasons

- The code has been compiled with the [`-g:none`](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javac.html#BHCGAJDC) javac option.

- The class files has been processed by an obfuscator or minimizer

## Solution

- **Make sure you're using the JDK classes** and not the JRE classes (if the lines refer to classes in the standard API)

- **Recompile with debug information**. If the lines refer to some third party library for which you don't have access to the source code, you're out of luck.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
