<span class="underline"></span>

<span class="underline"></span>

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)

<span class="underline"></span>

## Top Java Articles

1.  Do interfaces inherit from Object?
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

# Java: Do interfaces inherit from Object?

Interfaces _do not_ inherit from `Object`. And there is no common "root" interface implicitly inherited by all interfaces either as in the case with classes.<sup>(\*)</sup>

What may seem surprising is that it's still possible to call `Object` methods (such as `toString`, `hashCode` etc) even on interface types.

    Serializable s = "";
    s.toStringCompiles even though Serializable neither
    declares toString nor inherits from Object.();

Formally, this is because each interface implicitly declares one method for each public method in `Object`. This is explained in detail in the Java Language Specification:

> **9.2 Interface Members**  
> \[…\]
>
> - If an interface has no direct superinterfaces, then the interface implicitly declares a public abstract member method _m_ with signature _s_, return type _r_, and throws clause _t_ corresponding to each public instance method _m_ with signature _s_, return type _r_, and throws clause _t_ declared in `Object`, unless a method with the same signature, same return type, and a compatible throws clause is explicitly declared by the interface.
>
> \[…\] <a href="https://docs.oracle.com/javase/specs/jls/se8/html/jls-9.html#jls-9.2" class="quote-source">JLS 9.2</a>

<span class="small">(\*) Note that the notion of being a _subtype of_ is not equivalent to _inherits from_: Interfaces with no super interface are indeed subtypes of `Object` ([§ 4.10.2. Subtyping among Class and Interface Types](http://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html#jls-4.10.2)) even though they do not inherit from `Object`.</span>

## Comments (4)

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

The question is very interesting, however the above example is not right: you will see that `s.getClass().getName()` will show `java.lang.String`, so you are talking about the method `toString()` from `java.lang.String` class, not from `java.lang.Object`.

<span style="color: grey">by Silviu | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/99e100243aaa8b1469b1ed4e8bbecb06?d=mp)

The `Serializable` example is just to illustrate something that compiles and doesn't relate to the preceding sentence, but I can see how it's a bit confusing. Regardless by replacing `""` with `new Object()` you would actually call `Object.toString`, so no factual error in the text.

<span style="color: grey">by Andreas Lundblad | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/d41d8cd98f00b204e9800998ecf8427e?d=mp)

After a deeper thinking I realized I was wrong in my above comment. I guess too much IDE made me forget about "compile time" meaning. Thank you for reminding me.

<span style="color: grey">by Silviu | </span> <span class="reply-button">Reply</span>

![User avatar](https://www.gravatar.com/avatar/3bc5bd340b979f992efd0eb967da718d?d=mp)

Interesting read.

<span style="color: grey">by Rorttia | </span> <span class="reply-button">Reply</span>

### Add comment

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
