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

# AtomicInteger and equals / Comparable

As you may have noticed, two `AtomicInteger`s (or `AtomicLong`, or `AtomicBoolean`) are never equal:

    AtomicInteger i1 = new AtomicInteger(0);
    AtomicInteger i2 = new AtomicInteger(0);
    System.out.println(i1.equals(i2)); // false

This is because `AtomicInteger` doesn't override `equals`, which means it inherits the behavior from `Object.equals` which has the same semantics as `==`.

Same story for `AtomicInteger.hashCode`.

## So why is that?

The [package summary](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/atomic/package-summary.html) states that this is an explicit design decision:

> These classes are not general purpose replacements for `java.lang.Integer` and related classes. They do not define methods such as `equals`, `hashCode` and `compareTo`. Because atomic variables are expected to be mutated, they are poor choices for hash table keys.

Here's what Doug Lea, the principal author of the `java.util.concurrent` package, wrote on the matter ([source](http://cs.oswego.edu/pipermail/concurrency-interest/2004-January/000759.html)):

> While I can't think offhand of any application where I'd use AtomicIntegers as keys in a hash table (HashMap, Hashtable, ConcurrentHashMap), if I did, I would surely want to be able to find them even if they changed value. Using the default identity-based hashCode and equals methods provides this; so normal usages would almost always be correct, while with value-based versions, they almost never would be. And given this, because you aren't supposed to define a compareTo that returns 0 (equals) in different cases than when equals returns true, the only option is not to provide it. <span class="quote-source">Doug Lea</span>

## Comparable

It also doesn't implement `Comparable` as you may expect when comparing it with the `Integer` class.

The reason for this is covered in the same email thread as mentioned above ([source](http://cs.oswego.edu/pipermail/concurrency-interest/2004-January/000745.html)).

> Of course the same arguments can be made for AtomicIntegers being Comparable. Why aren't AtomicIntegers comparable?
>
> Because you cannot rely on the result of the comparison anyway, since the values may be immediately changed by other threads after you compare but before you use the comparison result. To avoid this, you would have to use locking, and those classes exist precisely to avoid locking. In particular, comparable suggests that you can sort objects of this type, and the sort operation assumes that these objects are constant (at least for some time), which is clearly the opposite of why those classes are to be used. Again, you would have to lock to make sure that the values do not change at least \_during\_ sorting. <span class="quote-source">Dawid Kurzyniec</span>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
