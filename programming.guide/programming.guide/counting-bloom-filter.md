



## Resources

[Bloom Filter](bloom-filter.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Counting Bloom filter](https://en.wikipedia.org/wiki/Counting_Bloom_filter)  
<span style="color: grey; font-style: italic; font-size: smaller">Wikipedia</span>

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)



## Top Java Articles

1.  [Do interfaces inherit from Object?](java/do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](java/executing-code-in-comments.html)
3.  [Functional Interfaces](java/functional-interfaces.html)
4.  [Handling InterruptedException](java/handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](java/why-wait-must-be-in-synchronized.html)

[**See all Java articles**](java/index.html)

# Counting Bloom Filter

A counting Bloom filter is a [Bloom filter](bloom-filter.html) that uses **counters instead of bits**. It shares many of the properties of regular Bloom filters: Insertions and lookups run in constant time, and lookups may give false positives. In addition counting Bloom filters…

- …can store multiple copies of the same element (be used as a **multiset**)
- …can **delete elements** (by "undoing" insertions)
- …consumes **more memory**

Regular Bloom Filter

Counting Bloom Filter

## Insertion & Lookup

Insertion is done by **incrementing counters** (instead of just setting bits).

Lookup can either just check that all counters associated with an element are greater than zero, or more generally, take a **threshold** as an extra argument and check that all counters are greater than or equal to that threshold.

## False Positives and False Negatives

Just as with regular Bloom filters, a counting Bloom filter can report false positives. Adding “foo” and “bar” three times each, could for example make it look like “baz” has been added three times.

Similarly to how standard Bloom filters never report false negatives, a counting Bloom filter would be able to say with certainty that “baz” has _not_ been added more than three times.

## Deleting Elements

A regular Bloom filters does not support deletion of elements. Two elements could have overlapping indexes in the bit vector, which mean that resetting the bits for one element would cause false negatives during subsequent lookups of the other element.

In a counting Bloom filter however, deletion can be implemented by **decrementing counters**.

The reason counting Bloom filters can undo insertions is that **the operations of incrementing and decrementing counters commute**: For example, \[+1, +1, −1\], gives the same end result as \[+1, −1, +1\]. The operations of regular Bloom filters, setting and unsetting bits do not commute: \[set bit, set bit, unset bit\] does _not_ given the same result as \[set bit, unset bit, set bit\].

One caveat here is that you may only delete an element that has previously been inserted. Or, more precisely, insertions and deletions of an element must be balanced in the same way as parentheses are balanced in an expression.

## Maxing out a counter

When a counter reaches its maximum value, trying to increment it further will have no effect. If the filter is implemented in a way such that the insertion still goes through, the operations no longer commute and semantics will start to sway:

- Lookups with thresholds may start to report false negatives. If “foo” is added 10 times but some counter maxed out after 5, the lookup function with a given threshold of 7 may respond with _No, element “foo” has definitely not been added more than 7 times!_
- Deletions may start to misbehave. If you add “foo” 10 times but a counter maxed out after 5, and you try to delete “foo” 10 times, you might inadvertedly delete unrelated elements.

To avoid this, you can let insertions fail whenever an attempt is made to increment an already maxed out counter. Another alternative is to dynamically allocate more memory. Create a new vector with the same number of counters, but with one additional bit per counter (effectively doubling the range of each counter), and copy over the values from the old vector to the new.

## How large counters to allocate?

In practice there's always a memory constraint, and how large counters to allocate becomes a tradeoff:

Small counters

Large counters

More counters which means fewer collisions and fewer false positives.

Longer before counters max out, i.e. more ressilient to problems due to collisions.

A common choice is to use 3 or 4 bits per counter.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
