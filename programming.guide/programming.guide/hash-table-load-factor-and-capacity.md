<span class="underline"></span>

<span class="underline"></span>

## Related

[Hash Tables](hash-tables.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

<span class="underline"></span>

## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Hash Table Load Factor and Capacity

This is an excerpt from the more extensive article on [Hash Tables](hash-tables.html).

## Load Factor

The **load factor** is the average number of key-value pairs per bucket.

load factor

=

total number of key-value pairs

number of buckets

It is when the load factor reaches a given limit that rehashing kicks in. Since rehashing increases the number of buckets, it reduces the load factor.

The load factor limit is usually configurable and offers a **tradeoff between time and space costs**.

Lower limit More empty buckets More memory overhead Higher limit Larger buckets Slower lookups

The default load factor for a Java [`HashMap`](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) is 0.75 and for a C\# [`Hashtable`](https://docs.microsoft.com/en-us/dotnet/api/system.collections.hashtable?view=netframework-4.8) it’s 1.0.

## Capacity

The **capacity** is the maximum number of key-value pairs for the given load factor limit and current bucket count.

capacity

=

number of buckets

×

load factor limit

Since rehashing increases the number of buckets, it increases the capacity.

The default initial capacity for a Java [`HashMap`](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) is 12 and for a C\# [`Hashtable`](https://docs.microsoft.com/en-us/dotnet/api/system.collections.hashtable?view=netframework-4.8) it’s 0, i.e. the bucket array is initialized lazily upon first insertion.

## Example

Here’s the structure of a hash table, configured with load factor limit of 4.

Current load factor: 24 / 8 = 3 Configured limit: 4 Current capacity: 8 × 4 = 32

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
