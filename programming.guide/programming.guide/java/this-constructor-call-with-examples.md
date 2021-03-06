



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

# Java: this(…) constructor call (with examples)

When you have multiple constructors, one constructor can call `this(…)` to **invoke another constructor**.

**Example:** The no-arg constructor delegates to the constructor that takes two arguments.

    class Complex() {
        double im;
        double re;

        public Complex() {
            this(0, 0);  // Call other constructor
        }

        public Complex(double initialIm, double initialRe) {
            im = initialIm;
            re = initialRe;
        }
    }

There are a few constraints to keep in mind:

- The `this(…)` call must be the first statement in the constructor
- You can't have circular (recursive) constructor calls

The `this(…)` call is similar to calling `super(…)`. See article [Calling super()](super-call.html).

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
