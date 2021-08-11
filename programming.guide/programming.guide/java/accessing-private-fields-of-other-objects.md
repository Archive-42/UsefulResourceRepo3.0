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

Java: Why can I access private fields of other objects?
=======================================================

As you may have discovered, this compiles:

    class MyClass {

        private int i = 7;

        public void m(MyClass notThis) {
            System.err.println(notThis.i);
        }
    }

The reason is that access modifiers work on **class level** and not on **object level**. Two different objects of the same class can access each others private members.

That's strange, why doesn't it work on object level?
----------------------------------------------------

This is a good question. Smalltalk, for instance, does in fact enforce access control on object level.

Here are three reasons:

### Efficiency

Enforcing it on class level allows the compiler to catch all violations in compiletime. Had it been on object level on the other hand, the compiler would have had to do one of the following things: - Guard every field access with something like `if (obj != this) throw IllegalAccessException();` which would slow down execution, or - defensively reject anything but `this.i` (like `obj.i`) since it's in general impossible to tell if `obj == this` in all executions. This would have been annoying in cases it was clear to the programmer that `obj` did in fact equal `this`.

### Locality

The field you're accessing (even if it's of a different object in runtime) is declared in the file you're editing. If you mess something up by modifying another objects state, the fault is in the file you have in front of you. There's no spooky action at a distance.

### Convenience

Some methods such as `equals`, `clone` and copy constructors would be tricky to write without giving up encapsulation.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
