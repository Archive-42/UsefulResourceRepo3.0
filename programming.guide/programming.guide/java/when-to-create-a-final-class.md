



## Further Reading

[Effective Java, Item 19: Design and document for inheritance or else prohibit it](https://books.google.se/books?id=BIpDDwAAQBAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by Joshua Bloch</span>

[Effective Java, Item 18: Favor composition over inheritance](https://books.google.se/books?id=BIpDDwAAQBAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by Joshua Bloch</span>

[Good reasons to prohibit inheritance in Java?](https://stackoverflow.com/q/218744/276052)  
<span style="color: grey; font-style: italic; font-size: smaller">Stack Overflow</span>



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

# Java: When to create a final class

A `final` class is simply a class that can’t be extended.

    This…final class Animal {



        …
    }

    class Dog …prevents this.extends Animal {



        …
    }

It does **not** mean that all fields in the class are automatically `final` or that all references to this class would act as if they were declared as `final`.

## When is this useful?

You should make a class final when the <span class="no-wrap">alternative—allowing</span> <span class="no-wrap">subclassing—opens</span> up for too many complications and becomes error prone.

Allowing subclassing may not seem like a big deal at first, but you should know that it’s **notoriously difficult** to get inheritance correct, and that it’s **better to disallow it altogether** than to get it wrong.

Here’s a non-exhaustive list of things to keep in mind when allowing classes to be extended:

- **Implementing `equals` becomes tricky**

  Suppose an `Animal` has a single property: `name`. Should an `Animal` with name “Fido” equal a `Dog` with name “Fido”?

      @Override
      boolean equals(Object o) {
          return o instanceof Animal
                  && this.name.equals(((Animal) o).name);
      }

  Seems reasonable, no? `equals` however, must by contract, be reflexive: if `x` equals `y`, then `y` must equal `x`. In other words, the `Dog` object must then `equal` the `Animal` object too. But what if `Dog` has an additional property `breed` that an `Animal` lacks? There’s no obvious solution here! Angelika Lagner and Klaus Kreft dedicate a whole article to this subject: [Secrets of equals()](http://www.angelikalanger.com/Articles/JavaSolutions/SecretsOfEquals/Equals.html).

- **Seemingly innocent overrides can have surprising effects**

  If a private method class calls a public method in the base class, then overriding the public method may have unexpected side-effects on the inner workings of the base class.

- **Class invariants may break**

  The base class perhaps maintains certain internal invariants. Perhaps it’s immutable, or intended to be thread-safe. There’s no way to enforce such design decisions upon subclasses. If you receive an object of the base class type, you technically can’t assume it’s immutable or thread-safe unless it’s `final`.

Put differently: Class inheritance is a flexible language feature, and a powerful footgun.

Concluding with a quote from [Effective Java](https://books.google.se/books?id=BIpDDwAAQBAJ):

> **Item 19: Design and document for inheritance or else prohibit it**
>
> \[…\] designing a class for inheritance requires great effort and places substantial limitations on the class.
>
> \[…\] The best solution to this problem is to prohibit subclassing in classes that are not designed and documented to be safely subclassed. <span class="quote-source">Joshua Bloch</span>

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
