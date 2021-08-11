



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

# Java: When should I override equals?

Override `equals` (and `hashCode`) if and only if your class represents some form of **value** or **entity**.

**_Should_ override equals:**

- `Complex`
- `Person`
- `Car`
- `Word`
- `Command`

**Should _not_ override equals:**

- `EntityManager`
- `ExecutionHelper`
- `SuccessCallback`
- `DatabaseUtil`
- `LoginServlet`

## Regarding Mutable classes

It is often good practice to make classes representing values and entities **immutable**. ([What exactly is immutable?](what-exactly-is-immutable.html)) If this is not an option in your situation, think twice before overriding `equals`. Imagine what could happen if the equality of two objects changes between the point where `equals` is called, and the point where the code actually relies value returned by the `equals` call. As a concrete example, using mutable objects (with custom `equals`/`hashCode` implementations) as keys in hash maps is a big no no!

## Remember to also override `hashCode`!

[Why you should always override hashCode when overriding equals](overriding-hashcode-and-equals.html)

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
