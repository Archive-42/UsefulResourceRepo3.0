



## Resources

[2-left hashing](https://xlinux.nist.gov/dads/HTML/twoLeftHashing.html) NIST DADS  
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
11. [2-Choice Hashing](2-choice-hashing.html)
12. 2-Left Hashing
13. [Linked Hash Table](linked-hash-table.html)
14. [Why large prime numbers are used in hash tables](prime-numbers-in-hash-tables.html)



## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

# 2-Left Hashing

2-left hashing is (just as [2-Choice Hashing](2-choice-hashing.html)) more of a variation that can be applied to other hash table implementations, rather than a full implementation itself.

It's commonly used with separate chaining, but can technically be used with any resolution strategy.

## Representation

In 2-left hashing two hash tables are used (two hash functions and two arrays).

**Example:** State of a hash table using 2-left hashing and separate chaining.

hash 1 hash 2

## Insertion

The key is inserted in the left hash table if the bucket it hashes to in the left table has a **lower or equal load** than the bucket it hashes to in the right hash table.

**Example:** Insertions using 2-Left Hashing.

hash 1 hash 2 To insert: x y z Fewer in left Fewer in right Equal = Go left!

## Lookup

Lookup is performed in both tables. This can be done in parallel.

## Removal

Similar to how lookup works.

## D-Left Hashing

The approach can be generalized to an arbitrary number of hash tables. This is called **d-left hashing**.

The performance gained when going from two tables to three (and beyond) is however far smaller than when going from one to two.

## Comparison to 2-Choice Hashing

[2-Choice Hashing](2-choice-hashing.html) also uses two hash functions and inserts the key in the bucket with least load. Only a single table is used however, and ties are resolved randomly.

☞

**Why would splitting the table up in two, and resolve ties assymetrically to the left be any better?**

For the maximum load to increase, two buckets with the same load must be chosen. If ties are resolved asymmetrically to the left, the left part will always be slightly ahead of the right part, and ties will be less frequent.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
