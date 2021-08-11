



## Resources

[2-choice hashing](https://xlinux.nist.gov/dads/HTML/twoChoiceHashing.html) NIST DADS  
<span style="color: grey; font-style: italic; font-size: smaller">by Paul E. Black</span>

## Hash Tables

1.  [Hash Tables](hash-tables.html)
2.  [Complexity](hash-tables-complexity.html)
3.  [Hash Table Load Factor and Capacity](hash-table-load-factor-and-capacity.html)
4.  [Hash Table vs Hash Set](hash-table-vs-hash-set.html)
5.  [Open vs Closed Addressing](hash-tables-open-vs-closed-addressing.html)
6.  [Open Addressing](hash-tables-open-addressing.html)
7.  [Coalesced Hashing](coalesced-hashing.html)
8.  [Cuckoo Hashing](cuckoo-hashing.html)
9.  [Robin Hood Hashing](robin-hood-hashing.html)
10. [Hopscotch Hashing](hopscotch-hashing.html)
11. 2-Choice Hashing
12. [2-Left Hashing](2-left-hashing.html)
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# 2-Choice Hashing

2-choice hashing is (just as [2-Left Hashing](2-left-hashing.html)) more of a variation that can be applied to other hash table implementations, rather than a full implementation itself.

It's commonly used with separate chaining, but can technically be used with any resolution strategy.

## Insertion

In 2-choice hashing you use **two hash functions**. When inserting a key, you compute which slot to use according to each hash function. You then proceed to insert the key in the slot **with fewest collisions**. Ties are resolved **randomly**.

**Example:** Insertion using 2-Choice Hashing.

To insert: x ← Fewer collisions h 1 h 2

By always having a "backup bucket" the insert operation can almost always avoid piling up on an already overloaded bucket.

## Lookup

When looking up a key, you hash the key with both hash functions and look through both buckets.

## Removal

Similar to how lookup works.

## Complexity

Assuming the hash computation and load comparison runs in constant time, the runtime of the insert operation is unaffected. There's a factor two runtime increase for worst case lookup and remove, but the Big-O complexity is unaffected.

The longest chain will, with high probability, contain no more than Θ(log(log(_n_)) keys. (Compare this with the case of a a single hash function, where the longest chain is expected to have Θ(log(_n_)/log(log(_n_))) keys.) This follows directly from a more general statistical concept called **The Power of Two Choices**, and is often discussed in the context of load balancing.

The intuition for why performance improves with this approach, is that one always "takes the edge off" of the worst case scenario. Outliers are avoided similar to how [truncated means](https://en.wikipedia.org/wiki/Truncated_mean) are used in many sports that rely on scores by judges.

## Hash Functions should be independent

In languages like Java and C\# where there's always one hash function available, it is tempting to derive the second hash function from the first. For example by using something like:

_h_<sub>2</sub>(_x_) = _h_<sub>1</sub>(_x_) xor 0xCAFEBABE         <span style="color: #c00">(bad idea!)</span>

This is unfortunately not as good as two independent hash functions. Intuitively _h_<sub>2</sub> will always provide the same "backup bucket" whenever _h_<sub>1</sub> produces an unfortunate result. One "mistake" will always follow the footsteps of the last time that mistake was made. The randomness is thus removed which impacts the spread of the keys.

## D-Choice Hashing

The approach can be generalized to an arbitrary number of hash functions. Unfortunately additional hash functions only decrease the maximum chain length by a constant factor.

## Related Techniques

[2-Left Hashing](2-left-hashing.html) and [Cuckoo Hashing](cuckoo-hashing.html) are examples of hash table techniques that rely on two hash functions.

Cuckoo Hashing relies heavily the assumption that the two hash functions are independent. Implementations of Cuckoo Hashing usually reserv a few slots (called the stash) for dealing with collisions, taking the idea of avoiding the very worst case one step further.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
