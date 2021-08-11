



## Related

[What does final mean, and are final variables always immutable?](final-variable.html)



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

# Java: What exactly is immutable?

In a nutshell, an object is immutable if it's state can not change. This definition however, begs the question: What belongs to the objects state? Suppose we have

    class Person {
        final StringBuffer name = new StringBuffer();
    }

The `name` reference of the `Person` object itself is final so it can not change, but since `StringBuffer` is mutable the actual name of the person can change. So, is `Person` mutable or not?

Most people would agree that objects of this class are _mutable_. So a more precise definition of immutable would be:

An object is immutable if

- it's own state is immutable, and
- the states of all objects directly or indirectly reachable from it's state, are immutable.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
