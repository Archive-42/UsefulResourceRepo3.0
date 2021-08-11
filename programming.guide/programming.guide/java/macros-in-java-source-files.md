



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

# Using C style macros in Java

It's possible to use C style macros in Java source files.

## The _shouldn't_ part

You _shouldn't_ because using the pre-processor is considered bad practice and the need for it has vanished in modern languages.

## The _can_ part

Java itself doesn't support macros. On the other hand, you could pipe the source code through the [C preprocessor](http://en.wikipedia.org/wiki/C_preprocessor) (CPP for short) just like the C/C++ compile chain does.

Here's a demo:

src/Test.java

    #define cube(x) ((x)*(x)*(x))
    class Test {
        public static void main(String[] ags) {
            System.out.println(cube(5));
        }
    }

Run the `cpp` command as follows:

    $ cpp -P src/Test.java preprocessed/Test.java

Result looks as follows:

preprocessed/Test.java

    class Test {
        public static void main(String[] ags) {
            System.out.println(((5)*(5)*(5)));
        }
    }

Compile and run as usual

    $ javac -d bin preprocessed/Test.java
    $ java -cp bin Test
    125

Integrating the `cpp` step in gradle, ant, maven or in the build chain of your favorite IDE should be straight forward.

## A better workaround

You can write a utility class with a static method instead:

    package util;
    public class MathUtil {
        public static int cube(int i) {
            return i*i*i;
        }
    }

To keep invocations as terse as for a macro, you can statically import the method as follows:

    import static util.MathUtil.cube;
    class Test {
        public static void main(String[] args) {
            System.out.println(cube(5));
        }
    }

## And finally, an anecdote

I myself used the CPP preprocessing approach on a Java code base once. I was creating a programming assignment for a course. I wanted to be able to easily extract a code skeleton out of the reference solution. So I just used a few `#ifdef`s to filter out the "secret" parts of the solution. That way I could maintain the reference solution, and easily regenerate the code skeleton.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
