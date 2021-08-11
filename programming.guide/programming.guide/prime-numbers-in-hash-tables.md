<span class="underline"></span>

<span class="underline"></span>

Hash Tables
-----------

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
13. [Linked Hash Table](linked-hash-table.html)
14. Why large prime numbers are used in hash tables

<span class="underline"></span>

Top Algorithm Articles
----------------------

1.  [Dynamic programming vs memoization vs tabulation](dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](sliding-window-example.html)
4.  [What makes a good loop invariant?](what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](random-point-within-circle.html)

[**See all algorithm articles**](algorithms.html)

Why large prime numbers are used in hash tables
===============================================

Hash tables store objects in buckets. Which bucket an object ends up in depends on the hash value for the object.

To transform a hash value to a valid bucket index you typically just compute modulo `numBuckets` where `numBuckets` represents the number of buckets in the hash table.

Hash tables perform best when objects are **spread evenly** among the buckets. A hash function should therefore strive for this goal.

Large hash values
-----------------

A hash function that only returns small values, say between 0 and 10, does not achieve a good spread if `numBuckets` becomes greater than 10.

To maintain a good spread when there's a large number of buckets, hash functions typically scale up the values by multiplying with a large prime number.

Why prime numbers?
------------------

If we scaled up the values by a composite number (non-prime), say 1000, there would be many values for `numBuckets` where the scale would be "cancelled out" in the mod operation. 1000 % `numBuckets` = 0 for `numBuckets` = 2, 4, 5, 8, 10, … In other words, similar objects would get similar bucket indexes. This reduces the spread and makes for a poor hash function.

By choosing a large prime number, we avoid this problem, since a prime number is not divisible by `numBuckets` unless `numBuckets` happens to be a multiple of that particular prime number.

Comments
--------

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](terms-and-conditions.html)
