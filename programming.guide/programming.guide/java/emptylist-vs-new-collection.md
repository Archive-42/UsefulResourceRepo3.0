



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

# Java: Collections.emptyList vs new ArrayList

The main difference between `new ArrayList<>()` and [`Collections.emptyList()`](http://download.oracle.com/javase/6/docs/api/java/util/Collections.html#emptyList%28%29) (or the slightly shorter variant [`List.of()`](http://download.java.net/java/jdk9/docs/api/java/util/List.html#of--) introduced in JDK 9) is that the latter returns an _immutable_ list, i.e., a list to which you cannot add elements.

In addition, `Collections.emptyList()`/`List.of()` avoids creating a new object. From the [javadoc](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html#emptyList--):

&gt;Implementations of this method need not create a separate List object for each call. Using this method is likely to have comparable cost to using the like-named field. (Unlike this method, the field does not provide type safety.)

The standard implementation of `emptyList` looks as follows:

    public static final <T> List<T> emptyList() {
        return (List<T>) EMPTY_LIST;
    }

So if this is a hotspot in your code, there's even a small performance argument to be made.

In summary I'd say `List.of` is preferrable (if you're on 9) over `Collections.emptyList`, which is preferable over for instance `new ArrayList<>()`.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
