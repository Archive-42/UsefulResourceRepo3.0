



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
11. [2-Choice Hashing](2-choice-hashing.html)
12. [2-Left Hashing](2-left-hashing.html)
13. Linked Hash Table
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# Linked Hash Table

A linked hash table is a **combination of a hash table and a linked list**. Nodes are arranged in buckets but also have a doubly linked list running through them.

One can use the hash table structure for fast hash based lookups, and the linked list for effirient traversal.

## Hash Table Traversal

There's no way to know which buckets are empty, and which ones are not, so all buckets must be traversed. This means traversal is <span class="no-wrap">Θ(_n_ + _m_)</span>.

In practice this is only relevant if the hash table is initialized with a very large capacity. After the first rehashing the number of buckets can be considered linearly proportional to the number of items, and traversal is _Θ_(_n_).

## Adding a linked list

If one wants to avoid the overhead due to empty buckets one can let a linked list run through all nodes. Whenever a node is added to the hash table, it's appended to this list.

**Example:** A linked hash table based on separate chaining.

This effectively trades some memory (additional next / prev pointers) for improved speed.

Since the overlay list structure is doubly linked, append and remove are constant time operations, so it does not affect the complexity of other operations.

The [`LinkedHashMap`](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html) in the Java API is an example of this technique.

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
