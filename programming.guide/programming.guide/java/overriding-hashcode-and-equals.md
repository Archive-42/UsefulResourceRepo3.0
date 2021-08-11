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

Java: Why you should always override hashCode when overriding equals
====================================================================

What could happen if I only override `equals`?
----------------------------------------------

-   Suppose you only override `equals` but not `hashCode`
-   This means that `hashCode` is inherited from `Object`
-   `Object.hashCode` always tries to return different hash codes for different objects (regardless if they are `equal` or not)
-   This means that you may end up with different hash codes for two objects that you consider to be `equal`
-   This in turn causes these two equal objects to end up in different buckets in hash based collections such as `HashSet`
-   This causes such collections to break

Let's illustrate with an example:

    class IntBox {
        int i;
        IntBox(int i) { this.i = i; }

        // equals other IntBoxes that store the same int value.
        @Override
        public boolean equals(Object o) {
            IntBox other = (IntBox) o;
            return this.i == other.i;
        }
    }

    class Main {
        public static void main(String[] args) {
            Set<IntBox> intBoxes = new HashSet<>();
            intBoxes.add(new IntBox(0));
            boolean found = intBoxes.contains(new IntBox(0));
            // found == false
        }
    }

What could happen if I only override `hashCode`?
------------------------------------------------

This will not *break* the code as above, but may degrade performance.

-   Suppose you only override `hashCode` but not `equals`
-   This means that you may return the same hash code for two non-equal objects
    -   `Object.hashCode` might do so too, but it does an as good job as possible to avoid it
-   This in turn means that two non-equal objects end up in the same bucket in a hash based collection such as `HashSet`
-   This degrades performance since objects are not distributed as evenly as possible among the buckets

**Put differently**: If you don't override `equals` any two objects will be considered non-equal. Since `Object.hashCode` ensures that all objects are distributed as evenly as possible in a hash based collection `Object.hashCode` is optimal, and overriding it with anything else will worsen the performance.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
